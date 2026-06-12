---
title: "Mount Permissions (SOLVED)"
date: 2005-10-13
forum: Desktop Environments
---

### Post by zoulman on 2005-10-13
Hi everybody, and happy Release Day!

I just got my new shiny Breezy Installed and I'm lov'n it. There is only one little thing e.g. my mounted windows patitions **do** show, but are only accessable in root mode. I can't browse them by clicking the icon launchers on the desktop. If I click the icons or access the partitions through /media/hda1 ect. I get the error:

The folder contents could not be displayed.

You do not have the permissions necessary 
to view the contents of "hda1".


What should I do? 
Oh woe is me!

---

### Post by adwait on 2005-10-13
Change their ownership to you. To do this, open the /etc/fstab file using
```
 sudo gedit /etc/fstab 
```
Now for the partitions that you want to access normally, in the options sections, add the line
```
uid=<UID> 
```
 To find out your UID, use the command
```
echo $UID
```

---

### Post by aysiu on 2005-10-13
Have you followed these instructions:

[http://www.ubuntuguide.org/#windows](http://www.ubuntuguide.org/#windows)

---

### Post by zoulman on 2005-10-13
Thanks. Up and running.

Live long and prosper.

---

### Post by adwait on 2005-10-13
nanoo nanoo

---

### Post by daschl on 2005-10-13
well, i got this message too (and fixed it)

BUT

i think this folder should be available to everyone (maybe with password-protection like synaptics and so on?)

---

### Post by adwait on 2005-10-13
Synapatic is available via the root password, or through sudo......Similarly, anyone having sudo previleges can access these files. If you many people to have access to it...add them all to one group. Lookup the GID (in the system>administration>add users). Now add the line
```
gid=GID
```
Replace GID with the appropriate number. That should do it. Then you can change the permissions with
```
sudo chmod 774 </mnt/location>
```

---

