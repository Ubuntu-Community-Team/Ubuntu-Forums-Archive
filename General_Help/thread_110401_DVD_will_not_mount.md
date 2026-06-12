---
title: "DVD will not mount"
date: 2005-12-30
forum: General Help
---

### Post by bluevoodoo1 on 2005-12-30
I'm having trouble mounting DVDs. Audio discs work fine, but with DVDs they will spin for a bit then stop. They would mount before I installed libdvdcss (but not play due to libdvdcss things). I installed libdvdcss-1.2.9, and now nothing happens. libdvdcss2 is not in the repos, correct? here are the outputs of a few commands...
```

brian@ubuntu:~$ mount /dev/hda
mount: block device /dev/hda is write-protected, mounting read-only

brian@ubuntu:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdc1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdc5       /home           ext3    defaults        0       2
/dev/hdc6       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0

brian@ubuntu:~$ mount
/dev/hdc1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /dev/shm type tmpfs (rw)
usbfs on /proc/bus/usb type usbfs (rw)
/dev/hdc5 on /home type ext3 (rw)
tmpfs on /dev type tmpfs (rw,size=10M,mode=0755)
/dev/hda on /media/cdrom0 type iso9660 (ro,noexec,nosuid,nodev,user=brian)


```
Is this a libdvdcss problem? or something else? Any help??

I also noticed that clicking on cdrw/dvdr drive in 'computer' yields this message

Warning: device /dev/hda is already handled by /etc/fstab, supplied label is ignored
mount: block device /dev/hda is write-protected, mounting read-only
mount: /dev/hda already mounted or /media/cdrom0 busy
mount: according to mtab, /dev/hda is already mounted on /media/cdrom0
Error: could not execute pmount

and

within /media there is a cdrom and a cdrom0 folder... I only have one drive. Upon clicking on each of them (with a DVD in the drive), I am able to access the information-- both info is the same in cdrom and cdrom0.

EDIT: If I click on one of those file folders and choose open with xine, an error comes up stating... "There is no demuxer plugin available to handle /media/cdrom/newline/website/id/empathyhit.aiff" This usually means the filr format was not recognized."

---

### Post by soulestream on 2005-12-30
[http://ubuntuforums.org/showthread.php?t=85167](http://ubuntuforums.org/showthread.php?t=85167)

soule

---

### Post by fordfan753 on 2005-12-30
libdvdcss2 is in the Marillat repository for Debian, I've used it from there on Ubuntu heaps of times without any problems.
go to the site, debian.video.free.fr and it'll tell you what to put in your sources.list, I usually just use the etch entry.

---

### Post by bluevoodoo1 on 2005-12-30
I tried uninstalling/reinstalling all my video players xine/mplayer/vlc and their supporting files as well as removing and installing libdvdread3 and libdvdcss2 and the problem still persists. DVDs won't show as mounted on the desktop, and when i try to access them through xine, it will freeze.

---

### Post by soulestream on 2005-12-30
might want to change udf,iso9660 to auto

soule

---

### Post by bluevoodoo1 on 2005-12-30
changed it to 'auto' no change...

---

### Post by bluevoodoo1 on 2005-12-30
got it to work! the solution was found in the following...

[http://ubuntuforums.org/showthread.php?t=13129&highlight=auto+mount](http://ubuntuforums.org/showthread.php?t=13129&highlight=auto+mount)

[http://ubuntuforums.org/showthread.php?t=74570&highlight=auto+mount](http://ubuntuforums.org/showthread.php?t=74570&highlight=auto+mount)

those two did the trick. Get 'hal' from Synaptic, then reboot. upon rebooting

sudo adduser hal <username>

that's it. oh, and make sure you have a video player to automatically start (if you want it to) from System > Preferences >Removable drives +media. totem is selected in mine, but i deleted it so of course a movie would not automatically begin.

---

