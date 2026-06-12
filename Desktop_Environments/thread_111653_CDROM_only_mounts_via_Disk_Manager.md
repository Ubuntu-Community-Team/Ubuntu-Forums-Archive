---
title: "CDROM only mounts via Disk Manager"
date: 2006-01-02
forum: Desktop Environments
---

### Post by jongkind on 2006-01-02
When I insert a disk in my CD-ROM it is not automatically recognized. I can only mount it manually via Disk Manager (System-Administration-Disk). This is quiet incovenient.

 I'm not sure whether there is an error in the fstab file. The CD-ROM line reads as follows:

/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0

Do you have any idea what goes wrong?

regards, Herman

---

### Post by schilcha on 2006-01-02
Did you have a look at System -> Preferences -> Removable Drives and Media Preferences? There you can tweak how ubuntu reacts on inserted removable media and such. 
In my fstab, the filesystem-column contains "auto" instead of "udf,iso9660" -- don't know if that'd make any difference for you. 

Good Luck

---

### Post by jongkind on 2006-01-02
[QUOTE=schilcha]Did you have a look at System -> Preferences -> Removable Drives and Media Preferences? There you can tweak how ubuntu reacts on inserted removable media and such. 
In my fstab, the filesystem-column contains "auto" instead of "udf,iso9660" -- don't know if that'd make any difference for you. 

Good Luck[/QUOTE]

Thanks for your help. I already had a look at drives and media preverences, everything looks OK there. I changed the "udf,iso9660" to auto. That did not help. This issue must be related to permissions: e.g. when I try to eject the CDROM it tells me that only the root account can do this. However, when I check my permissions I must be able to acces e.g. a CDROM drive. Further I noticed that USB keys also have to be mounted manually via Disk Manager. Strange. Hope that somebody can help me.

Thanks, Herman

---

### Post by schilcha on 2006-01-03
[QUOTE=jongkind]However, when I check my permissions I must be able to acces e.g. a CDROM drive.[/QUOTE]
Just to make sure (since this was my second guess)... Do you mean, you've checked that you're member of the appropriate groups (i.e. the correct settings in System -> Administration -> Users and Groups -> Properties (of your account) -> User privileges).

I'm sorry, I can't be of any help in this case. Have a look at your log-files (e.g. /var/log/syslog) to see if some problems are reported there.

---

### Post by jongkind on 2006-01-03
Thanks. Yes, I checked that I'm member of the correct groups, in fact, I'm member of all groups that can be selected in the "setting for user screen". I had a look at the syslog file which has several entries (generated during start-up of Ubuntu) telling met that cdrom: open failed. As example I copied-pasted a Jan 3 entry with the following text:

Jan  3 18:33:38 localhost kernel: [4294692.100000] cdrom: open failed.

It might be related to the recent installation of Gnomebaker. However, removal of that software did not solve this issue. 

Herman

---

### Post by dcstar on 2006-01-17
Try adding this to your /etc/sysctl.conf file (and reboot):

dev.cdrom.check_media = 0

---

