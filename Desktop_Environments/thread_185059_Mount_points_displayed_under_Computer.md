---
title: "Mount points displayed under Computer"
date: 2006-05-31
forum: Desktop Environments
---

### Post by Rondonjin on 2006-05-31
I just installed the RC of Dapper over my FC5 install, reformatting the / and /var partitions there. Everything went well and after updating the system and installing extra software packages and codecs, etc, my system is rock solid. Only one thing is weird. When I open the 'Computer' icon on my desktop there
are 3 extra mount points displayed: /home, /var and one called Root Volume. I
never had this with Breezy nor with FC5. Is this a bug in the partitioner?

Wayne

---

### Post by simonn on 2006-05-31
cat /etc/fstab and paste it here.

---

### Post by Rondonjin on 2006-05-31
[QUOTE=simonn]cat /etc/fstab and paste it here.[/QUOTE]

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda7       /home           ext3    defaults        0       2
/dev/hdb1       /media/video    ext3    defaults        0       2
/dev/hdb5       /media/video1   ext3    defaults        0       2
/dev/hda6       /var            ext3    defaults        0       2
/dev/hda5       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by stimpsonjcat on 2006-05-31
this is a bug AND a feature (depending on your point of view) :-? 
Bug: [https://launchpad.net/distros/ubuntu/+source/gnome-vfs2/+bug/47349](https://launchpad.net/distros/ubuntu/+source/gnome-vfs2/+bug/47349)
Feature: [http://bugzilla.gnome.org/show_bug.cgi?id=341446](http://bugzilla.gnome.org/show_bug.cgi?id=341446)

---

### Post by ubnoobie on 2006-05-31
while i can see the benefit of displaying USER MOUNTABLE volumes, particularily removable media -- the display of non-user mountable physical volumes should be considered a bug and a potential security issue.

---

### Post by Rondonjin on 2006-05-31
[QUOTE=stimpsonjcat]this is a bug AND a feature (depending on your point of view) :-? 
Bug: [https://launchpad.net/distros/ubuntu/+source/gnome-vfs2/+bug/47349](https://launchpad.net/distros/ubuntu/+source/gnome-vfs2/+bug/47349)
Feature: [http://bugzilla.gnome.org/show_bug.cgi?id=341446](http://bugzilla.gnome.org/show_bug.cgi?id=341446)[/QUOTE]

Thanks for the info. I suppose I just have to wait for the bug-fix or the feature update :D 

Wayne

---

