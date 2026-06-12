---
title: "Bacula: Director authorization problem"
date: 2009-04-28
forum: General Help
---

### Post by jprof7 on 2009-04-28
Hi there,
I'm using Bacula 2.4.2 on Ubuntu 8.10 (installed from the Live disk if that makes a difference). It is using bacula-director-sqlite3 and bacula-sd-sqlite3. My issue is that when I try to run bconsole I get an error stating "Director authorization problem" and the program exits. I've checked the passwords and names from my config files and they appear to be the same, but I could be missing something obvious when you haven't been staring at text files for hours. Any help would be appreciated and let me know if there is any other info I can supply that would make this easier. I haven't even begun to worry about jobs, so when viewing my config don't worry about that...yet ;P

Here are my config files:

BACULA-SD.CONF
Storage {                             # definition of myself
  Name = cortana-sd
  SDPort = 9103                  # Director's port      
  WorkingDirectory = "/var/lib/bacula"
  Pid Directory = "/var/run/bacula"
  Maximum Concurrent Jobs = 20
}

Director {
  Name = cortana-dir
  Password = "Cv70F6pf1t6pBopT4vQOnigDrR0v3LT3Cgkiyj"
}

Director {
  Name = cortana-mon
  Password = "Cv70F6pf1t6pBopT4vQOnigDrR0v3LT3Cgkiyj"
  Monitor = yes
}

Device {
  Name = FileStorage
  Media Type = File
  Archive Device = /nonexistant/path/to/file/archive/dir
  LabelMedia = yes;                   # lets Bacula label unlabeled media
  Random Access = Yes;
  AutomaticMount = yes;               # when device opened, read it
  RemovableMedia = no;
  AlwaysOpen = no;
}

--------------------------------------------

BACULA-DIR.CONF

Director {                            # define myself
  Name = cortana-dir
  DIRport = 9101                # where we listen for UA connections
  QueryFile = "/etc/bacula/scripts/query.sql"
  WorkingDirectory = "/var/lib/bacula"
  PidDirectory = "/var/run/bacula"
  Maximum Concurrent Jobs = 1
  Password = "Cv70F6pf1t6pBopT4vQOnigDrR0v3L"         # Console password
  Messages = Daemon
}

JobDefs {
  Name = "DefaultJob"
  Type = Backup
  Level = Incremental
  Client = cortana-fd 
  FileSet = "Full Set"
  Schedule = "WeeklyCycle"
  Storage = cortana-sd
  Messages = Standard
  Pool = Default
  Priority = 10
}

Job {
  Name = "Client1"
  JobDefs = "DefaultJob"
  Write Bootstrap = "/var/lib/bacula/Client1.bsr"
}

Job {
  Name = "BackupCatalog"
  JobDefs = "DefaultJob"
  Level = Full
  FileSet="Catalog"
  Schedule = "WeeklyCycleAfterBackup"
  RunBeforeJob = "/usr/bin/awk -f /etc/bacula/scripts/make_catalog_backup_awk -v cat1=<CatalogName> /etc/bacula/bacula-dir.conf"
  # This deletes the copy of the catalog
  RunAfterJob  = "/etc/bacula/scripts/delete_catalog_backup"
  Write Bootstrap = "/var/lib/bacula/BackupCatalog.bsr"
  Priority = 11                   # run after main backup
}

Job {
  Name = "RestoreFiles"
  Type = Restore
  Client=cortana-fd                 
  FileSet="Full Set"                  
  Storage = cortana-sd                      
  Pool = Default
  Messages = Standard
  Where = /nonexistant/path/to/file/archive/dir/bacula-restores
}

FileSet {
  Name = "Full Set"
  Include {
    Options {
      signature = MD5
    }
    File = /build/buildd/bacula-2.4.2/debian/tmp-build-sqlite
  }


  Exclude {
    File = /proc
    File = /tmp
    File = /.journal
    File = /.fsck
  }
}

Schedule {
  Name = "WeeklyCycle"
  Run = Full 1st sun at 23:05
  Run = Differential 2nd-5th sun at 23:05
  Run = Incremental mon-sat at 23:05
}

Schedule {
  Name = "WeeklyCycleAfterBackup"
  Run = Full sun-sat at 23:10
}

FileSet {
  Name = "Catalog"
  Include {
    Options {
      signature = MD5
    }
    File = /var/lib/bacula/bacula.sql
  }
}

Client {
  Name = cortana-fd
  Address = 127.0.0.1
  FDPort = 9102
  Catalog = MyCatalog
  Password = "Cv70F6pf1t6pBopT4vQOnigDrR0v3LT3Cg"          # password for FileDaemon
  File Retention = 30 days            # 30 days
  Job Retention = 6 months            # six months
  AutoPrune = yes                     # Prune expired Jobs/Files
}

Storage {
  Name = cortana-sd
# Do not use "localhost" here    
  Address = cortana               # N.B. Use a fully qualified name here
  SDPort = 9103
  Password = "Cv70F6pf1t6pBopT4vQOnigDrR0v3LT3Cgkiyj"
  Device = FileStorage
  Media Type = File
}

Catalog {
  Name = MyCatalog
  dbname = "bacula"; dbuser = "bacula"; dbpassword = ""
}


Messages {
  Name = Standard
  mailcommand = "/usr/lib/bacula/bsmtp -h localhost -f \"\(Bacula\) \<%r\>\" -s \"Bacula: %t %e of %c %l\" %r"
  operatorcommand = "/usr/lib/bacula/bsmtp -h localhost -f \"\(Bacula\) \<%r\>\" -s \"Bacula: Intervention needed for %j\" %r"
  mail = root@localhost = all, !skipped            
  operator = root@localhost = mount
  console = all, !skipped, !saved
  append = "/var/lib/bacula/log" = all, !skipped
}

Messages {
  Name = Daemon
  mailcommand = "/usr/lib/bacula/bsmtp -h localhost -f \"\(Bacula\) \<%r\>\" -s \"Bacula daemon message\" %r"
  mail = root@localhost = all, !skipped            
  console = all, !skipped, !saved
  append = "/var/lib/bacula/log" = all, !skipped
}

Pool {
  Name = Default
  Pool Type = Backup
  Recycle = yes                       # Bacula can automatically recycle Volumes
  AutoPrune = yes                     # Prune expired volumes
  Volume Retention = 365 days         # one year
}

Pool {
  Name = Scratch
  Pool Type = Backup
}

Console {
  Name = cortana-mon
  Password = "Cv70F6pf1t6pBopT4vQOnigDrR0v3L"
  CommandACL = status, .status
}

--------------------------------------------

BACULA-FD.CONF

Director {
  Name = cortana-dir
  Password = "Cv70F6pf1t6pBopT4vQOnigDrR0v3LT3Cg"
}


Director {
  Name = cortana-mon
  Password = "Cv70F6pf1t6pBopT4vQOnigDrR0v3LT3Cg"
  Monitor = yes
}


FileDaemon {                          # this is me
  Name = cortana-fd
  FDport = 9102                  # where we listen for the director
  WorkingDirectory = /var/lib/bacula
  Pid Directory = /var/run/bacula
  Maximum Concurrent Jobs = 20
}

Messages {
  Name = Standard
  director = cortana-dir = all, !skipped, !restored
}

----------------------------------------

BCONSOLE.CONF

Director {
  Name = cortana-dir
  DIRport = 9101
  address = 127.0.0.1
  Password = "Cv70F6pf1t6pBopT4vQOnigDrR0v3L"
}

---

