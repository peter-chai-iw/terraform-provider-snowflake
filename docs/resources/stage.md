---
# generated by https://github.com/hashicorp/terraform-plugin-docs
page_title: "snowflake_stage Resource - terraform-provider-snowflake"
subcategory: ""
description: |-
  
---

# snowflake_stage (Resource)



## Example Usage

```terraform
resource "snowflake_stage" "example_stage" {
  name        = "EXAMPLE_STAGE"
  url         = "s3://com.example.bucket/prefix"
  database    = "EXAMPLE_DB"
  schema      = "EXAMPLE_SCHEMA"
  credentials = "AWS_KEY_ID='${var.example_aws_key_id}' AWS_SECRET_KEY='${var.example_aws_secret_key}'"
}

resource "snowflake_stage_grant" "grant_example_stage" {
  database_name = snowflake_stage.example_stage.database
  schema_name   = snowflake_stage.example_stage.schema
  roles         = ["LOADER"]
  privilege     = "OWNERSHIP"
  stage_name    = snowflake_stage.example_stage.name
}
```

<!-- schema generated by tfplugindocs -->
## Schema

### Required

- **database** (String) The database in which to create the stage.
- **name** (String) Specifies the identifier for the stage; must be unique for the database and schema in which the stage is created.
- **schema** (String) The schema in which to create the stage.

### Optional

- **aws_external_id** (String)
- **comment** (String) Specifies a comment for the stage.
- **copy_options** (String) Specifies the copy options for the stage.
- **credentials** (String, Sensitive) Specifies the credentials for the stage.
- **directory** (String) Specifies the directory settings for the stage.
- **encryption** (String) Specifies the encryption settings for the stage.
- **file_format** (String) Specifies the file format for the stage.
- **id** (String) The ID of this resource.
- **snowflake_iam_user** (String)
- **storage_integration** (String) Specifies the name of the storage integration used to delegate authentication responsibility for external cloud storage to a Snowflake identity and access management (IAM) entity.
- **tag** (Block List) Definitions of a tag to associate with the resource. (see [below for nested schema](#nestedblock--tag))
- **url** (String) Specifies the URL for the stage.

<a id="nestedblock--tag"></a>
### Nested Schema for `tag`

Required:

- **name** (String) Tag name, e.g. department.
- **value** (String) Tag value, e.g. marketing_info.

Optional:

- **database** (String) Name of the database that the tag was created in.
- **schema** (String) Name of the schema that the tag was created in.

## Import

Import is supported using the following syntax:

```shell
# format is database name | schema name | stage name
terraform import snowflake_stage.example 'dbName|schemaName|stageName'
```
