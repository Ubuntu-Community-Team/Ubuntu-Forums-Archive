---
title: "[SOLVED] Could not start the X-Server"
date: 2007-10-25
forum: Desktop Environments
---

### Post by MacDuff on 2007-10-25
Have been running Ubuntu 7.10 without problems for several days but today I had to reboot and at re-start the following error message appeared:

Could not start the X 
Server due to some internal error.
Please contact your sysem adminstrator
or check your syslog to diagnose.
In the meantime this display will be 
disabled. Please restart GDM when the 
problem is corrected"

The system then freezes so I could not check the "syslog" even if I knew where it is and how to do that.
I have no idea what "GDM" is although at this moment I would guess something like G** Damned Machine"
but it probably means something else.

Can someone point me toward a solution, please?

---

### Post by taurus on 2007-10-25
GDM stands for Gnome Display Manager--GUI login screen.

Boot into recovery mode from GRUB menu and look at your /var/log/syslog.

```
more /var/log/syslog
```
Hit the Space bar for the next 24 lines.

---

### Post by MacDuff on 2007-10-25
OK I did that but it is one huge file, literally thousands of entries.  What am I looking for?
I assume error messages and there are some but nothing I would consider fatal.  The last line is:
ubu-comm rpc.statd[4272]:Caught signal 15, un-registering and exiting.

The line immediately above that reads:
ubu-comm nmbd[5713]: Got SIGTERM: going down...

Does that tell you anything?

Would the simplest thing be to re-install the GDM (if that is possible without doing a complete install)?
If so, how would I go about doing that?

---

### Post by taurus on 2007-10-25
What happens if you run

```
startx
```

---

### Post by MacDuff on 2007-10-25
hostname: Unknown host
/usr/bin/startx: line 132:cannot create temp file for here document: Read-only file system
xauth:error in locking authority file /root/.Xauthority
/usr/bin/startx: line 144:cannot create temp file for here document: Read-only file system
xauth:error in locking authority file /root/.Xauthority
/usr/bin/startx: line 144:cannot create temp file for here document: Read-only file system

x: warning; process set to priority -1 instead of requested priority 0

Fatal server error:
Could not create lock file in /tmp/.tX0-lock
sgiving up

xinit: Connection refused (errno 111): unable to connect to X server
xinit: No such process (errno 3): Server error.
xauth: error in locking authority file /root/.Xauthority
root@ubu-comm: ~#
 
Since I have to copy this to another computer I hope I have not made any typing errors

---

### Post by MacDuff on 2007-10-25
taurus:

I have been looking at the output you asked for and the "read only file system" got me thinking. I don't want to distract you but here is some more information that may shed some light:
Before I re-booted, I edited the /etc/fstab file to change the mount point of a second drive on this box.  The drive is an ntfs drive and even though fdisk displays a "*" under boot, I don't think it would be an actual boot drive on a Linux system but I really lack any depth of knowledge about Linux, as you can tell.

I just tried to  use  NANO to reverse the change that I made to fstab before I re-booted but I could not save the change reversal.  Nano reported that the file system was read-only.  Would that normally be the case with the boot failing at this point or have I, in my ignorance cause a major problem?

Ignorance is a major handicap when working with operating systems :(

---

### Post by taurus on 2007-10-25
Let's have a look at the permissions of your /etc/fstab then.

```
ls -la /etc/fstab
```

---

### Post by MacDuff on 2007-10-25
Here it is:
-rw-r--r-- 1 root root 588 Oct 25 14:42 /etc/fstab

---

### Post by taurus on 2007-10-25
While you are still in the recovery mode, do

```
nano -Bw /etc/fstab
```
Once you have finished making your changes, save it with <Ctrl>o and exit with <Ctrl>x.  Look at it again to see if everything is in order.

```
cat /etc/fstab
```
Otherwise, post it here including the output of this command.

```
df -h
```

---

### Post by MacDuff on 2007-10-25
When I try to save /etc/fstab using ^0 I get an error message 
[error writing /etc/fstab: Read-only file system]

The contents of fstab leaving out the header lines:
proc /proc  proc defaults 0 0
# Entry for /dev/hdb2 :
UUID=814e801c-320a-4130-8d29-5787d967b7a9 / ext3 defaults, errors=remount -ro 0 1
# Entry for /dev/hdb5 :
UUID=ad7a3348-7766-44c7-9347-ed6a7891eb76 nono swap sw 0 0
/dev/hda /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/sda1 /CommNTFS ntfs-3g auto,uid=1000,gid=100,umask=007,locale=en_CA.UTF -8$

The last line above is the one I was trying to comment out, after the system failure.

The second file you asked for:
root@ubu-comm:~# df -h
Filesystem       Size    Used  Avail  Use%  Mounted on
/dev/hdb2       119G  22G    92G     19%       /
varrun             951M  24K    951M    1%       /var/run
varlock             951M   0      951M    0%       /var/lock
udev                951M  316K  950M    1%       /dev   
devshm           951M     0      951M    0%       /dev/shm
root@ubu-comm:~#

---

### Post by taurus on 2007-10-25
To save it, it should be <Ctrl> and then lower case letter o, not zero--0.  

Can you boot your machine with the LiveCD?

---

### Post by MacDuff on 2007-10-25
Taurus:

Actually I think I did use ^o.  My typing is getting pretty bad.  I am soon going to have to turn in. I have a stinking cold that has prevented me from getting more than a couple of hours sleep for the past 4 nights.   My brain and fingers just will not work any more.

Yes I can boot using the Live CD.

---

### Post by MacDuff on 2007-10-26
OK taurus, I am back in the office and ready for another day of education.

I booted from the live CD  but I am not sure how that will get me to a fix, other than it proves that the hardware still works.  Is it possible to make changes to the installed system from the live CD?

I then tried again to boot the system using the recovery mode and the last page of the boot process, contains the following:
"* Starting the Firestarter firewall... "  and at the right in RED is [fail]
"chown: changng ownership of '/tmp/.X11-unix': Read-only file system
rm: cannot remove '/var/log/dmesg.4.gz': Read only file system
mv: cannot move '/var/log/dmesg.3.gz' to '/var/log//dmesg.4.gz' : Read-only file system
mv: cannot move '/var/log/dmesg.2.gz' to '/var/log//dmesg.3.gz' : Read-only file system
mv: cannot move '/var/log/dmesg.1.gz' to '/var/log//dmesg.2.gz' : Read-only file system
gzip: /var/log..mesg.0.gz: Read-only file system
mv: cannot stat '/var/log//dmesg.0.gz': No such file or directory
touch: cannot touch '/var/log/dmesg.new': Read-only file system
chown: cannot access '/var/log/dmesg.new': Read-only file system
chmod: cannot access '/var/log/dmesg.new': Read-only file system
ln: cannot remove '/var/log//dmesg.0': Read-only file system
Error hardlinking var/log/dmesg to /var/log///dmesg.0
/etc/rdS.d/S80bootmisc.sh: 81: cannot create /var/log/dmesg: Read-only file system
chgrp: changing group of  '/var/log/dmesg': Read-only file system
rm: cannot remove '/var/lib/urandom/random-seed': Read-only file system
root@ubu-comm:~#"

Does that provide any more clues as to what might be wrong?

---

### Post by taurus on 2007-10-26
If you want to edit /etc/fstab on your harddrive, /dev/hdb2, from the LiveCD, do

```
sudo mkdir /media/ubuntu
gksudo gedit /media/ubuntu/etc/fstab
```

---

### Post by MacDuff on 2007-10-26
Hi Taurus:

Sorry to be such an imbecile but I honestly don't understand what it is I am to do.  Are you telling me to start the system using the Live CD and then to enter the code you posted?  

Will that unlock the system somehow or how does it relate to my inablilty to boot?
Do I have to copy the result of that code to the system on the disk or how does it unlock the system?

Did the posting of the boot screen tell you what the problem is?  Is the problem that I somehow re-set everything to read only?

Could you perhaps you could flesh out your instructions a little more bearing in mind that I am a newbie?

Thanks

---

### Post by taurus on 2007-10-26
I thought you said you modified /etc/fstab and since then, everything goes south.  Now, you need to change /etc/fstab back to the way it was before and you couldn't do it since it's a read-only file.

---

### Post by MacDuff on 2007-10-26
Yes I did modify fstab and when I re-booted the display manager failed.  I wondered if the change I had made to fstab might have caused it or if it was just a coincidence.

I then posted the contents of several commands you suggested and the contents of the last page of my last attempted boot in recovery mode, which listed a number of errors or what I take to be errors.  Could they be caused by the change to the fstab file?

If so, yes I will have to modify the fstab file.
Using your last suggestion I booted from the Live CD  but when I enter your code:
sudo mkdir /media/ubuntu
gksudo gedit /media/ubuntu/etc/fstab

I just get a blank file.  There is nothing to edit and if there was, I do not know how I can copy it to a file which is read only.

The live CD shows me the drives that are on my system but will not display the contents because I do not have permission.  Therefore I cannot edit or copy information from the hard drive.

I need a way to edit the fstab file and/or change my file system from read only to read write execute.

Your last suggestion did not do it.

---

### Post by taurus on 2007-10-26
Sorry.  We skipped an important command to actually mount it first before you could edit it.

```

sudo mkdir /media/ubuntu
**sudo mount -t ext3 /dev/hdb2 /media/ubuntu**
gksudo gedit /media/ubuntu/etc/fstab
```

---

### Post by MacDuff on 2007-10-26
OK I did that and it displayed the original fstab file which I edited to remove the last line I had edited.

NOW What?     Sorry to be so flippant but you guys who know it all, do not realize that we who know nothing, have to be told everything.

In the absence of any further instructions, I made the assumption that I must re-boot the system (after removing the Live CD).

IT WORKED!

Thanks taurus.  Sorry to be such a pain.  There are times when I almost regret making the decision to dump MicroSoft and go fully to Linux.   I was really comfortable with Windows and this particular problem never happened with Windows in 20+ years of use, although lots of other problems did occur.  However as a last resort I could always do a clean install over top of the original OS.  That is not as easy to do with Linux but it is also very seldom required thanks to you people on the forums.

Each time somebody like you shoulders a problem like this it renews my determination to make the complete switch to Ubuntu.  If I can overcome a few more problems in the next month, hopefully I will be able to chuck MS by the year end.

Much obliged to you.

---

### Post by patchoro on 2007-12-20
May I add my thanks to this exellent post.

Just encountered this baddy. Fstab was more dangerous then I ever anticipated...

Solved. Many thanks to the community in general!

---

### Post by pe7er on 2008-06-27
Thanks for this marvellous thread + solution!

I experienced the same problem on Ubuntu 8.04 Hardy Heron: 
after a reboot it could not start X-window + the Gnome GUI.
(yes, before I rebooted I indeed changed /etc/fstab to automatically mount a Network Attached Storage device ](*,))

Thanks to this thread I was able to solve it!

I rebooted Linux from the Live CD, 
then I used 
[INDENT]sudo gedit (and the directory + fstab filename on my harddisk)[/INDENT]
I removed the two lines that I had added, saved the file & rebooted my PC.
and now Ubuntu is running smoothly again.....

Many thanks!

---

### Post by mvanbeek on 2008-07-02
Another thanks from me.  Had the same problem and was able to take care of it.

---

### Post by dragonflyseven on 2008-07-09
Hey, it worked for me too, with a couple modifications. I have a jfs filesystem for reasons I don't remember now, but here is what I did:
```
jfs_fsck -f /dev/sda1
mount -t jfs /dev/sda1 /media/ubuntu
```
The rest of the steps were the same, but definitly try forcing a clean with fsck if you are getting errors about wrong types and such.

---

