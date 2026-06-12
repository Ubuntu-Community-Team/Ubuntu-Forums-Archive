---
title: "Requesting assistance mounting CD burner"
date: 2005-08-07
forum: Desktop Environments
---

### Post by cajunaggie on 2005-08-07
I'm attempting to mount a CD-burner but I'm not having any luck. So far Ubuntu and GNOME Baker both recognize the burner but I can't get any CD's to mount.
My FSTAB configuration for my CD drive and CD burner looks like this:
```

<file system> <mount point> <type>         <options>          <dump> <pass>
/dev/hdc         /media/cdrom0 udf,iso9660 ro,user,noauto         0            0
/dev/hdd         /media/cdrom1 udf,iso9660 ro,user,noauto         0            0

```
What am I doing wrong and how do I go about fixing it?

---

### Post by woedend on 2005-08-07
[QUOTE=cajunaggie]I'm attempting to mount a CD-burner but I'm not having any luck. So far Ubuntu and GNOME Baker both recognize the burner but I can't get any CD's to mount.
My FSTAB configuration for my CD drive and CD burner looks like this:
```

<file system> <mount point> <type>         <options>          <dump> <pass>
/dev/hdc         /media/cdrom0 udf,iso9660 ro,user,noauto         0            0
/dev/hdd         /media/cdrom1 udf,iso9660 ro,user,noauto         0            0

```
What am I doing wrong and how do I go about fixing it?[/QUOTE]
 what are the messages with either?   Mine used to just not burn and would disappear(close) To get Graveman to work(and gnomebaker) in Ubuntu(and only ubuntu), I had to uncheck the automounting features.  To do so, click system -> preferences -> removable drives and media.  Uncheck all but the first box on that page is my preference...then close gnomebaker if running, unmount the drive and eject if its mounted, and start over...worked like a charm.

---

### Post by cajunaggie on 2005-08-07
[QUOTE=woedend]what are the messages with either?   Mine used to just not burn and would disappear(close) To get Graveman to work(and gnomebaker) in Ubuntu(and only ubuntu), I had to uncheck the automounting features.  To do so, click system -> preferences -> removable drives and media.  Uncheck all but the first box on that page is my preference...then close gnomebaker if running, unmount the drive and eject if its mounted, and start over...worked like a charm.[/QUOTE]

I'm getting a message that says: "Cannot mount drive. There is no media in the drive."

---

