---
title: "f-spot not starting"
date: 2009-02-02
forum: General Help
---

### Post by slibuntu on 2009-02-02
Hey guys,
I'm having a problem with f-spot, when ever I start it nothing happens, I get the following error on the command line
```

Unhandled Exception: Mono.Data.SqliteClient.SqliteExecutionException: SQL logic error or missing database
  at Mono.Data.SqliteClient.SqliteCommand.ExecuteStatement (IntPtr pStmt, System.Int32& cols, System.IntPtr& pazValue, System.IntPtr& pazColName) [0x00000] 
  at Mono.Data.SqliteClient.SqliteCommand.ExecuteStatement (IntPtr pStmt) [0x00000] 
  at Mono.Data.SqliteClient.SqliteCommand.ExecuteReader (CommandBehavior behavior, Boolean want_results, System.Int32& rows_affected) [0x00000] 
  at Mono.Data.SqliteClient.SqliteCommand.ExecuteNonQuery () [0x00000] 
  at Banshee.Database.QueuedSqliteCommand.Execute () [0x00000] 

```

I've tried deleting the .gnome2/f-spot/photos.db file, with no joy.

Also, starting the program as super user works, but it says there is a problem with the database, copies it to a backup in /home/user and starts with a new one. Very annoying

Any ideas?

---

