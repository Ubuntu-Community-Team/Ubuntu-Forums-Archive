---
title: "Error Running Software"
date: 2009-04-19
forum: General Help
---

### Post by falconfan on 2009-04-19
Attached a WD external HD (Passport) to my newly acquired Dell Mini.  I have added a couple of things to the HD, no problem, but when trying to run any of the setup.exe files, whether it be factory installed stuff (on the Passport) or the files I added I get an error message:

Error running software
Error starting autorun program: Permission denied.

What am I missing?  I am the administrator on the machine.  Many thanks in advance!
Blue skies-
Jeff

---

### Post by Titan8990 on 2009-04-19
Are you using Ubuntu?

Is WINE installed?

What format is the external drive?

---

### Post by falconfan on 2009-04-19
Yes, using Ubuntu.  Not sure what WINE is (sorry); also not clear about the HD format.  How would I check that?  Many thanks!

---

### Post by Titan8990 on 2009-04-19
WINE is what allows you to run some Windows .exe files in Linux. 

Was the drive already formatted when you bought it? Can you use it in Windows?

To find out plug the drive in, go to Applications -> Accessories -> Terminal

Type:

blkid

and press enter. Copy and past the contents here.

Also, while you have access to the files on the drive, type the following:

mount


Post the results of the mount command as well.

---

### Post by falconfan on 2009-04-19
Just found out that whatever the problem is, it has nothing to do with the HD.  Just hooked up a new external CD/DVD drive, and I get the same error trying to run it's install software too.  BTW - the HD, the CD/DVD drive, everything is brand new.  Will go check on the other.  Thank you.

---

### Post by falconfan on 2009-04-19
jeff@jeff:~$ blkid
/dev/mmcblk0p1: SEC_TYPE="msdos" UUID="3936-6437" TYPE="vfat" 
jeff@jeff:~$

---

### Post by falconfan on 2009-04-19
jeff@jeff:~$ mount
/dev/sda2 on / type ext3 (rw)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-22-lpia/volatile type tmpfs (rw)
gvfs-fuse-daemon on /home/jeff/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=jeff)
/dev/mmcblk0p1 on /media/disk type vfat (ro,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)
/dev/sdc1 on /media/My Passport type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)
/dev/scd0 on /media/Nero-NE71011 type iso9660 (ro,nosuid,nodev,uhelper=hal,uid=1000,utf8)
jeff@jeff:~$

---

### Post by Titan8990 on 2009-04-19
Well, most likely the problem is that whatever autmount utility that is in use is mounting with the options "user" which implies "noexec" unless overrode. It is a security measure that may need to be overridden.

---

### Post by jimmyhacker on 2009-04-19
i really say LOL! how do you think Ubuntu can run .exe without help of an application?its linux kernel not NT!also it needs exploler.exe,winlogon.exe and Visual Library.And they can`t be runned by Linux.so you give a try to Wine or VirtualBox

---

### Post by falconfan on 2009-04-19
So how do I give WINE a shot?

---

### Post by Titan8990 on 2009-04-19
Easiest way around this will just be to copy the .exe to the your local drive. FAT is not a Linux/UNIX filesystem.


To install WINE go to: System -> Administration -> Synaptic Package Manager

Search for fine and installations should be fairly self explanatory via the GUI. Any problems, feel free to ask.


Synaptic Package Manager is where you should be installing **all** applications in Ubuntu. 


However, it is likely that your Dell came with WINE preinstalled to ease the transition from Windows.

---

