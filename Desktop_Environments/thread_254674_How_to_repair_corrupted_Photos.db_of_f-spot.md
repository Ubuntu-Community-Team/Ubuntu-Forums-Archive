---
title: "How to repair corrupted Photos.db of f-spot?"
date: 2006-09-10
forum: Desktop Environments
---

### Post by swamytk on 2006-09-10
I have Ubuntu Dapper 6.06. I moved all my huge photos collection from gthumb to f-spot spending a few hour. After some time, when I was running f-spot, it was hanging at some point. Since whole system was hanging, I restarted the PC. Oh, God! f-spot consistently crashed with corrupted ~/.gnome2/f-spot/photos.db file (If i rename this, f-spot starts properly with empty collection). Again I can't tag each and every collection, since it is scatterd in ~/Photos/yyyy/mm/dd directories. **[SIZE="6"]I am crying for some help to repair the photos.db[/SIZE]**

Here is the error message with this corrupted photos.db

```
An unhandled exception was thrown: SQL logic error or missing database

in <0x000d0> Mono.Data.SqliteClient.SqliteCommand:ExecuteStatement (IntPtr pStmt, System.Int32 cols, System.IntPtr pazValue, System.IntPtr pazColName)
in <0x000a4> Mono.Data.SqliteClient.SqliteDataReader:ReadpVm (IntPtr pVm, Int32 version, Mono.Data.SqliteClient.SqliteCommand cmd)
in <0x000e0> Mono.Data.SqliteClient.SqliteDataReader:.ctor (Mono.Data.SqliteClient.SqliteCommand cmd, IntPtr pVm, Int32 version)
in (wrapper remoting-invoke-with-check) Mono.Data.SqliteClient.SqliteDataReader:.ctor (Mono.Data.SqliteClient.SqliteCommand,intptr,int)
in <0x0019a> Mono.Data.SqliteClient.SqliteCommand:ExecuteReader (CommandBehavior behavior, Boolean want_results, System.Int32 rows_affected)
in <0x0001d> Mono.Data.SqliteClient.SqliteCommand:ExecuteReader (CommandBehavior behavior)
in <0x0000c> Mono.Data.SqliteClient.SqliteCommand:ExecuteReader ()
in <0x00089> TagStore:LoadAllTags ()
in <0x0005c> TagStore:.ctor (Mono.Data.SqliteClient.SqliteConnection connection, Boolean is_new)
in <0x00180> Db:Init (System.String path, Boolean create_if_missing)
in <0x0008d> FSpot.Core:.ctor ()
in <0x0037a> FSpot.Driver:Main (System.String[] args)
.NET Version: 1.1.4322.2032

Assembly Version Information:

System.Data (1.0.5000.0)
Mono.Data.SqliteClient (1.0.5000.0)
gdk-sharp (2.8.0.0)
Mono.Posix (1.0.5000.0)
gnome-vfs-sharp (2.8.0.0)
dbus-sharp (0.60.0.0)
System (1.0.5000.0)
atk-sharp (2.8.0.0)
gtk-sharp (2.8.0.0)
glib-sharp (2.8.0.0)
gnome-sharp (2.8.0.0)
f-spot (0.0.0.0)
mscorlib (1.0.5000.0)

Platform Information: Linux 2.6.15-26-686 i686 unknown GNU/Linux

Disribution Information:

[/etc/debian_version]
testing/unstable

[/etc/lsb-release]
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=6.06
DISTRIB_CODENAME=dapper
DISTRIB_DESCRIPTION="Ubuntu 6.06.1 LTS"

```

---

### Post by swamytk on 2006-09-11
Any one has idea about it? Actually photos.db is an sqlite3 database. Any clue in this angle is also useful. Is there any way to edit the file?

---

### Post by gabaug on 2006-09-13
You can try to dump the database to a flat text file, move it out of the way, then restore it.

sqlite ~/.gnome2/f-spot/photos.db .dump > f-spot.dump
mv ~/.gnome2/f-spot/photos.db photos.db.backup
sqlite ~/.gnome2/f-spot/photos.db < f-spot.dump

If you happen to be using sqlite3, you'll need to use sqlite3 instead of sqlite in the above.  Actually, if the db is currently in sqlite2, it's good to move it to sqlite3, so use sqlite3 in the third command either way.  Good luck.

---

### Post by swamytk on 2006-09-13
waavv... thanks for your suggestion. let me check it out.

---

### Post by Kitty on 2006-11-06
See [https://launchpad.net/distros/ubuntu/+source/f-spot/+bug/69910](https://launchpad.net/distros/ubuntu/+source/f-spot/+bug/69910)

---

