---
title: "Memory Stick Mounted as Read-Only"
date: 2006-06-17
forum: Desktop Environments
---

### Post by larry on 2006-06-17
Hello,
I have a problem: my memory stick gets mounted as a read-only medium.
I suppose it should be easy to fix it (though I have seen many people reporting similar troubles with XFCE).
This is what happens:
1) I plug in my memory stick and a sda1 icon appears on the desktop.
2) right click on the icon and I mount it
3) The medium mounted this way is read-only. If I try:
sudo chmod -R 777 /media/usbdisk/

Then I get tons of complains from Xubuntu as the medium filesystem is read-only.
I am using a sony 1Gb memory stick and no write protection is enabled.
How comes? I cut and paste my /etc/fstab and /etc/mtab. I am sure this is very trivial to solve for somebody experienced (unlike me...).
If I need to change the USB key filesystem, then tell me how to do it, please (no idea where to start from).
A guy I know with a similar problem solved it with chmod 777 plus something he does not remember, but he will be away for quite some time.
Here are my mtab and fstab files, respectively:

/dev/hda1 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw 0 0
/sys /sys sysfs rw 0 0
varrun /var/run tmpfs rw 0 0
varlock /var/lock tmpfs rw 0 0
procbususb /proc/bus/usb usbfs rw 0 0
udev /dev tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
devshm /dev/shm tmpfs rw 0 0
lrm /lib/modules/2.6.15-25-386/volatile tmpfs rw 0 0

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

Final question: has anybody experienced the same problems with Kubuntu/Ubuntu?
I mean, is this really an XFCE problem?
Many thanks

Larry

---

### Post by fdimmling on 2006-06-17
You are shure that the switch write-protect of the stick is not set on. With my sticks I sometimes inadvertantly activate the switch while removing the stick.

Friedrich

---

### Post by jtwJGuevara on 2006-06-17
I'm merely guessing on this post, but hopefully it will lead you in the right direction...

Are you sure your usb disk is being mounted as procbususb /proc/bus/usb?  I would find out by typing "mount" at the command line without any parameters.  Find where your usb drive actually mounted to, and add that explicitely to your /etc/fstab with rw permissions in /etc/fstab.  Unmount it then try "mount -a" to mount it again.  (If your previous entry is the result of trying this already, I apologize).

Also, there could be a chance your usb stick is NTFS - and I'm not sure that NTFS writing is enabled by default.

---

### Post by larry on 2006-06-17
Well, my memory stick does not even have a switch or anything you can move in order to activate write protection...that is why I am puzzled!

larry

---

### Post by larry on 2006-06-17
[QUOTE=jtwJGuevara]I'm merely guessing on this post, but hopefully it will lead you in the right direction...

Are you sure your usb disk is being mounted as procbususb /proc/bus/usb?  I would find out by typing "mount" at the command line without any parameters.  Find where your usb drive actually mounted to, and add that explicitely to your /etc/fstab with rw permissions in /etc/fstab.  Unmount it then try "mount -a" to mount it again.  (If your previous entry is the result of trying this already, I apologize).

Also, there could be a chance your usb stick is NTFS - and I'm not sure that NTFS writing is enabled by default.[/QUOTE]


Alright, perhaps we are getting there.
This is what I read when typing mount after mounting the usb stick:

/dev/sda1 on /media/usbdisk type vfat (rw,nosuid,nodev,quiet,shortname=mixed,uid=1000,gid=1000,umask=077,iocharset=utf8)

How should I paste this to /etc/fstab?
Sorry for that (I am not very expert), I tried stuff like:

/dev/sda1      /media/usbdisk   vfat, user , no auto   0          0 

but then sudo mount -a tells me that line is bad.
Hopefully it will be easy to fix!
Many thanks

Larry

---

### Post by jtwJGuevara on 2006-06-17
Larry,

Try placing a comma between "no" and "auto".  /etc/fstab is a space delimited file and you need to make that list of options comma delimited.

Also, it looks like it is attempting mount your usb disk as rw by default anyway.  I'm not quite sure why chmod 777 isn't working on it.  You should be able to write to vfat filesystems, if I'm not mistaken.

---

### Post by larry on 2006-06-17
[QUOTE=jtwJGuevara]Larry,

Try placing a comma between "no" and "auto".  /etc/fstab is a space delimited file and you need to make that list of options comma delimited.

Also, it looks like it is attempting mount your usb disk as rw by default anyway.  I'm not quite sure why chmod 777 isn't working on it.  You should be able to write to vfat filesystems, if I'm not mistaken.[/QUOTE]

Hi, 
After several attempts, I found some (very partial) solution.
I am using the fstab file as I had before the installation (no reference to a mount point for the usb key in it) whereas the mtab file does contain info about the /media/usbdisk mountpoint.
It sounds odd, but I did not have better luck with other attempts.
I can now write/read files but with some difficulty (I have to re-mount the stick from time to time when I get again the stupid write-only filesystem complain. If I try removing the New Folder folder I have on the memory stick, then the system complains again that it is a read-only filesystem).
Very weird...do these sort of things also happen with (K)Ubuntu?
If anyone has some suggestions, please come forward.
Cheers

Larry

---

