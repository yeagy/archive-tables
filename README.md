# archive-tables
Tool to move deleted data into a schemaless recoverable archive table. Postgres, HSTORE.

The basic idea is to back every table that needs a soft delete with a seperate table for the deleted data. To get around the problem of DDL changes between old deleted data with the current model is to store the deleted data in a HSTORE column. Stored procedure to create the archive table, move data to archive table and delete original.

Anatomy of archive table:

  * Same primary key name/type of active table
  * Delete time millis
  * Data HSTORE

Thoughts:

  * Stored proc to auto-restore data?
  * Dealing with foreign keys and cascading behavior for the delete.
  * Versioning needed? Most likely if we want auto-restore of some sort.
  * Deal with data types of original table.
  * Don't eff up transactions!

  
