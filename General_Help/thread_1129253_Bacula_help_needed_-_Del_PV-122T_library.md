---
title: "Bacula help needed - Del PV-122T library"
date: 2009-04-18
forum: General Help
---

### Post by mrojas73 on 2009-04-18
Hi,

I have been trying to get my library to work with Bacula but,  I don't know what I am doing wrong.

I installed Bacula from source on Ubuntu 8.04 and even though I can get all the deamons to start...I can't get the darn library to do anything.  First it took me a good deal of time to figure out the device naming.  Most information point to /dev/nst0 and /dev/st0.  In my case they appear to be /dev/sg3 for the autoloader and /dev/sg4 for the drive:

Here is the output of lsscsi:```

[1:0:0:0]    disk    ATA      Maxtor 6Y080M0   YAR5  /dev/sda
[4:0:0:0]    cd/dvd  SAMSUNG  CD-ROM SC-148A   B403  /dev/scd0
[4:0:1:0]    disk    ATA      WDC WD400BB-75FJ 14.0  /dev/sdb
[6:0:5:0]    mediumx DELL     PV-122T          D37r  -
[6:0:6:0]    tape    HP       Ultrium 1-SCSI   E32K  /dev/st0

```
My passwords match on all files however I do run into a lot of permission issues when I try to run some library commands.  For example labeling a tape:```


root@cet-backup:/etc/bacula# ./bconsole
Connecting to Director 127.0.0.1:9101
1000 OK: cet-backup-dir Version: 3.0.0 (06 April 2009)
Enter a period to cancel a command.
*label
Automatically selected Catalog: MyCatalog
Using Catalog "MyCatalog"
The defined Storage resources are:
     1: File
     2: Autochanger
Select Storage resource (1-2): 2
Enter new Volume name: Tests2
Defined Pools:
     1: Default
     2: Scratch
Select the Pool (1-2): 1
Connecting to Storage daemon Autochanger at 127.0.0.1:9103 ...
Sending label command for Volume "Tests2" Slot 0 ...
Invalid slot=0 defined in catalog for Volume "" on "tape" (/dev/sg4). Manual load may be required.
3301 Issuing autochanger "loaded? drive 0" command.
3991 Bad autochanger "loaded? drive 0" command: ERR=Permission denied.
Results=

```

Here is my library configuration on bacula-sd:
```


Autochanger {
  Name = "autochanger"
  Device = tape
  Changer Device = /dev/sg3
  Changer Command = "/etc/bacula/mtx-changer %c %o %S %a %d"
}
Device {
  Name = tape
  Drive Index = 0
  Media Type = LT0-1
  Archive Device = /dev/sg4
  RemovableMedia = yes
  Autochanger = yes
  Autoselect = yes
  Maximum Changer Wait = 300
  LabelMedia = yes #lets Bacula label unlabeled media
  AutomaticMount = yes
  AlwaysOpen = no
}

```

Maybe some one could help me get pass this wall, I would really appreciate it.

Thanks.

Marco

---

