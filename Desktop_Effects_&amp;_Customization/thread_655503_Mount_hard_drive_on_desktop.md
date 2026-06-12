---
title: "Mount hard drive on desktop"
date: 2008-01-01
forum: Desktop Effects &amp; Customization
---

### Post by ronbrooks on 2008-01-01
I don't know what has happened but I use to be able to double click on each of my three, second hard drive partitions and they would mount and they would show up on my desktop.  Now the first two partitions will do that but the third one will not but it will mount and just not show up on the desktop.

Not sure how to fix this.  I have checked the properties on each drive and they are all the same except the name of the partition. Can anyone help with this. 

Thank you

---

### Post by ryanVickers on 2008-01-01
first, understand the difference between the mount point (the folder that contains the contents of the drive) and the icon they make on your desktop. ;)

Now that that's clear, I would check in mtab and fstab files (in /etc) and see how they are setup to mount... if they are not all the same, that could be the problem there.

also, make sure its mounted by going to its folder - if you haven't changed it, it's probably like /media/disk... :p

---

### Post by ronbrooks on 2008-01-01
OK I have checked the two files that you said and here are the out put.
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=8db64489-2a24-44cb-9714-88eaccdc2bb7 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=c91225d7-d997-4771-be9c-a19619e48b2f none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

# /dev/hdb1
#UUID=19EA-5882 /media/drive1 vfat auto,utf8,user,uid=1000,gid=100,umask=007 0 0 


/dev/hda1 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
procbususb /proc/bus/usb usbfs rw 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.20-16-generic/volatile tmpfs rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw 0 0
/dev/hdb1 /media/disk vfat rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077 0 0
/dev/hdb5 /media/SECOND vfat rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077 0 0
/dev/hdb6 /media/THIRD vfat rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077 0 0

The one I am having trouble with is /dev/hdb6 /media/THIRD.  The other two are ok.  When I mount it the icon in the media window will change to show that it is mounted but when I go to the desktop I can only see the first two drives.

---

### Post by ryanVickers on 2008-01-01
random point: if you have SECOND and THIRD, shouldn't "disk" be "FIRST" ;)

ok, now to the problem :p
well, according to that, if the 2 work, so should the 3rd, but perhaps thats not what determines that...

1) Are you mounting the drives all the same way?
2) what type are the drives?  Brand name, capacity, USB vs. internal? SATA or SATA II vs. IDE?

---

### Post by ronbrooks on 2008-01-01
Ok to start with they were all working ok a few weeks ago and I was having trouble with my sounds and I got them working ok.  Then I must have done something to the system because it stoped working.  Why just that one I don't know. The three drives are on the one hard drive that is an IDE. After I monut them and go to Places the drop down menu will show all three.  The desk top will only show the first two.  From there if I click on the thrid drive it will open and I can work on it with no trouble.

I was thinking that there may be a setting in gnome that may need to be change.

---

### Post by ronbrooks on 2008-01-02
bump

---

### Post by ryanVickers on 2008-01-02
Well, 3 partitions on the same IDE drive is about as ordinary as you can get ;), so I don't see and incompatibility problems there, especially if you say they all work fine, just the icon doesn't show up... I'll look into the possibility of a gconf key gone bad... :p

[COLOR=Red]**EDIT:**[/COLOR] I forgot to ask one blatantly obvious question that should have been first - do all 3 icons appear properly when you...[INDENT]1. unmount and then re-mount the drive(s)[/INDENT][INDENT][INDENT]AND / OR
[/INDENT][/INDENT][INDENT]2. reboot/logoff then on again
[/INDENT][COLOR=Red]**EDIT 2: **[COLOR=Black]Try running this script - it will reload the desktop (but a much more in-depth version then just "control + r") and then it will reload the fact it should show device icons (mounted drives, CD's, mp3 players, etc.)

[COLOR=Red]**EDIT 3:**[COLOR=Black] I just finished a little script that's uses are much broader than this problem, but it may be useful - give it a try! (last in signature)[/COLOR][/COLOR]
[/COLOR] [/COLOR]

---

### Post by ronbrooks on 2008-01-03
First off RyanVickers thank you for your help.

I ran the Script and re booted my system and it didn't help.

In the Media folder I don't have any mounting points for any of the drives but there is a drive1 there.  When I click on Places and Computer all the drives are listed there.  When I dubble click on each drive it will mount and then I check the Media folder and see that they are there, but still the Media/THIRD is not on the desktop but the other two are. 

Now I go to Places again and the drives are listed under Computer with my CD drives. Now when I unmount them from the system a new Icon shows that it is unmounted and they will go from the Desktop and they will not be in the Media file anymore.

when they are mounted  I can use them with no trouble. 

I have comment out my /ect/fstab so they should not load and there is no mounting point in the Media folder. here is my /ect/fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=8db64489-2a24-44cb-9714-88eaccdc2bb7 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=c91225d7-d997-4771-be9c-a19619e48b2f none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

# Mount hard drive

# /dev/hdb1
#UUID=3865-15E0 /media/drive vfat auto,utf8,user,uid=1000,gid=100,umask=007 0 0 
# /dev/hdb5
#UUID=44AA-3544 /media/SECOND vfat auto,utf8,user,uid=1000,gid=100,umask=007 0 0 
# /dev/hdb6
#UUID=19EA-5882 /media/THIRD vfat auto,utf8,user,uid=1000,gid=100,umask=007 0 0 

So it is just an Icon thing and I don't know why the one drive will not show in the desktop like the others.

If anyone else has an Idea please let me know.

---

### Post by ryanVickers on 2008-01-03
Ok, the only thing I can say now is I have always used this great little panel applet called "Disk Mounter"; it shows all drives (floppy, CD, and all disks) whether they are mounted or not. It creates an icon for eack thing, and when you click it, you can choose to mount/unmount the drive, and view it's contents :D Give it a try! I wouldn't need the desktop ones after you get it ;)

---

### Post by ronbrooks on 2008-01-03
OK I got the applet and it is showing all my drives.  I guess that will work for now but I would like to get it back the way it was.  If anything else that you can think of put it here and I will check it for the next week or so to see if there is any addistions to the tread. 

Again thank you very much and have a Happy New Year.

---

