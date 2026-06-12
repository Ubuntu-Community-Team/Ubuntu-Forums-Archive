---
title: "GUI tool for Gnome to edit fstab. Trying to mount at boot 5 network drives."
date: 2005-02-13
forum: Desktop Environments
---

### Post by MetalMusicAddict on 2005-02-13
Like it says im trying to mount at boot 5 network drives and I dont wanna F' up the fstab. So Im wondering if theres a tool to help setup the mountpoints, permissions and such. Im workin off of warty.

This is my 1st post (been lurkin', readin' :)) and Im in love with Ubuntu. After many a distro search I feel I found mine. :) I have 75% of the functionality on my M$ box. :) Almost there.

---

### Post by Xian on 2005-02-13
I don't know if there is such a tool but I'd think that would be the more hazardous route. I just wouldn't trust some auto-config package to set up my fstab. Geez, that really is a scary thought. If you would post your partition table, your current fstab file contents, and describe which mountpoints you are interested in including w/desired permissions I'm sure we can help you out and get your set-up working properly.

---

### Post by MetalMusicAddict on 2005-02-13
Thanx so much for the offer sir. Im on my M$ side now. I have some DivX stuff to do and I gotta get the kids to bed but I will post tomorrow with my info. Thanx again. ;)

---

### Post by MetalMusicAddict on 2005-02-14
Ok. Heres my fstab as of now:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdd        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
```

The network drives I wanna have show up in /mnt.

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdd        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
//192.168.1.103/MP3s     /mnt/MP3s  smbfs   credentials=/root/.smbcredentials,dmask=777,fmask=777   0       0
```

Now I think thats right. Now I could just copy the one line and change the to and from directories. Right?
I did also create the ".smbcredentials" in the root directory. I have a username but I dont have passwords on the win box. So its blank. Will that F' up linux?

Looks like this:
```
username=atm
password=
```

When I type  this:
```
sudo mount //192.168.0.103/MP3s /mnt/MP3s/ -o username=atm,password=,dmask=777,fmask=777
```
I cant mount the drive. I get this:
```
 wrong fs type, bad option, bad superblock on //192.168.1.103/MP3s, or too many mounted file systems
```

---

### Post by Xian on 2005-02-14
As I've not done this from experience I don't want to just say, "yeah, that looks great" and tell you to run with what you have. It makes sense, but I would also consult the Ubuntu Starter Guide, which has some nice examples and suggestions on this subject. You could also try and mount the drives manually and then work from those commands. That subject is also in the guide and should be of some assistance.

-- >[Mounting Networks on Boot](http://ubuntuguide.org/#automountnetworkfolder)

---

### Post by piedamaro on 2005-02-14
Xian, as a sidenote if you use hotplug and hal, everytime at boot or if an usb drive is connected, your fstab is rewritten by fstab-sync, an "automated" config tool.

---

### Post by Xian on 2005-02-14
[QUOTE=piedamaro]Xian, as a sidenote if you use hotplug and hal, everytime at boot or if an usb drive is connected, your fstab is rewritten by fstab-sync, an "automated" config tool.[/QUOTE]
Based on detected hardware but not HD partitions I'm assuming.

---

### Post by piedamaro on 2005-02-14
[QUOTE=Xian]Based on detected hardware but not HD partitions I'm assuming.[/QUOTE]
 It should be based on sysfs but now I'm seeing that on fedora /etc/fstab get rewritten directly, but on ubuntu there should be another fstab somewhere but I can't remember.

---

### Post by MetalMusicAddict on 2005-02-16
So my 1st post is pretty much where Im at. The only thing I can think of is that it doesnt like me having a blank password

---

### Post by doogy2004 on 2006-10-03
if you are only using a username without a password and you are not too concerned about security (which seems to be the case since you are not useing a password) try this setup in the fstab

```

//fileserver/storage /media/storage smbfs username=USER,uid=LOCALUSER,gid=GROUP 0 0

```

uid sets the ownership of the disk(mounted volume)
gid sets the group of users or user that can access and not modify

---

