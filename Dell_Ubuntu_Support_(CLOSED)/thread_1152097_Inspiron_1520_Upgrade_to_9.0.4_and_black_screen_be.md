---
title: "Inspiron 1520: Upgrade to 9.0.4 and black screen before login"
date: 2009-05-07
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Zyma on 2009-05-07
Hi guys!

I am a newbie to linux ubuntu, so please try to be simple in explanations!

My laptop (32 bits) has been running ubuntu 8.10 perfectly well. I have just upgraded to Jaunty and the installation went well without a single error(system >administrator ...so on). After the installation I was asked to restart the computer which i did. But , when it was time to show the login screen, the screen went totally black. I couldn't login (no window for that!) I had to switch off the computer (and start again in order to go back to vista so that I could use my computer).

Before the upgrading I had lots of files in Intrepid and I wonder if I shall be able to recover them.

I shall really appreciate your help!

---

### Post by coffeeaddict22 on 2009-05-07
Hi,
You should be able to get into recovery mode.  If you're dual booting, there's a screen where you select which OS you're going into.  Underneath the Linux option you usually use, there's one for "recovery mode".  Boot into that, and if your data is REALLY important, that should give you enough access to back it up somewhere.  Once you've done that, there's an option to repair X (X is the rather cryptic name of the window manager).  Try that.

---

### Post by Zyma on 2009-05-08
Thanks coffeeaddict22!

I boot into recovery mode (Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)). I get the following window:

Recovery Menu
   resume   Resume normal boot
   clean    Try to make free space
   dpkg     Repair broken packages
   fsck     File system check
   grub     Update grub bootloader
   netroot  Drop to root shell prompt with networking

I choose "dpkg" and get:
   rm: cannot remove '/var/lib/apt/lists/partial/*': No such file or directory
   rm: cannot remove '/var/cache/apt/archives/partials/*': No such file or directory.

I go back to "resume" and the problem remains: the login screen does not show up and the computer hangs on forever (with black screen) so that I am obliged to switch off.

---

### Post by Zyma on 2009-05-08
It seems that the problem may be due to incompatibility of "Intel integrated graphic chips" with ubuntu Jaunty.

I wonder if there is a way to fix it or I may be obliged to uninstall ubuntu Jaunty in order to reinstall my favorite ubuntu Intrepid.

Thanks for your help!

---

### Post by coffeeaddict22 on 2009-05-08
OK.  
Two options.  I'm assuming you did the upgrade from within the system- by pressing on the Upgrade button in the package manager?
The easiest solution is to just scroll down past recovery mode, and boot into your previous setup.  It should be all still there.

There's a wiki page on getting the Intel driver sorted, if you're sure that's what the problem is - [here.]("https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4")

---

### Post by Zyma on 2009-05-08
Yes.
I did the upgrade using Upgrade button in the package manager. I would be very glad if I can find a way to return back to ubuntu 8.10 (I am writing my thesis and all my fortran programs are stored there!)

When I do the booting in ubuntu, here is the screen I see,  after I've pressed "Esc":

GRUB4DOS 0.4.4 2008-10-27, Memory: 636K/2037 M, CodeEnd: 0x42910

Ubuntu 9.04, kernel 2.6.28-11-generic
Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
Ubuntu 9.04, kernel 2.6.27-11-generic
Ubuntu 9.04, kernel 2.6.27-11-generic (recovery mode)
Ubuntu 9.04, memtest 86+
Other operating systems:
Windows Vista/Longhorn (loader)
Microsoft Windows XP Embedded

Use the (up arrow) and (down arrow) keys to highlight an entry. Press ENTER or 'b' to boot.
Press 'e' to edit the commands before booting, or 'c' for a command-line.


I choose to highlight one of the two recovery mode and press ENTER. Affter some scrolling of info I end up at this window:
 Recovery Menu
 ....( as it is shown in the previous post).

So how can I do in order to boot into my previous setup? (After the screen has gone black, the computer is just dead: no button or combination of buttons work; except the switch on/off button). 

Thanks!

---

### Post by coffeeaddict22 on 2009-05-08
OK, so you need the data.  Either boot into recovery mode or if you've got a live CD, use that to boot up; mount the hard drive and copy the data off it.
The link above has instructions on how to correct the Intel graphics display driver.  Have a look; basically cut and paste 3 lines into a terminal, which you should be able to get to in recovery mode (choose the last option- drop to root shell mode with networking, and you're in a terminal).

---

### Post by Zyma on 2009-05-09
Hi!

I have no liveCD so I shall boot into recovery mode (choosing the last option- drop to root shell mode with networking and I get "root@ubuntu:~#" as termainal). 

I am new to linux, so I do not know which commands I shall type in order to mount the hard driver. I shall be glad if you tell me how I proceed (to mount and unmount the hard driver). I have a usb flash with 4GB at hand. 

On how to correct the Intel graphics display driver: I went to the link above and get info on how to install the package. But there are lot of info, to be sure I should ask if the three lines you mentioned are:

deb [http://ppa.launchpad.net/siretart/ppa/ubuntu](http://ppa.launchpad.net/siretart/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/siretart/ppa/ubuntu](http://ppa.launchpad.net/siretart/ppa/ubuntu) jaunty main
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 0xce90d8983e731f79

There is also info on "Install the driver", namely:
$ sudo apt-get update
$ sudo apt-get install xserver-xorg-video-intel-2.4

Are these two last lines to be typed?

---

### Post by coffeeaddict22 on 2009-05-09
You should find you've mounted the drives if you're in a root shell.    Your USB key may not be at /media/disk : if you type in ```
mount
``` you'll get a list of all the disks/ filesystems you have access to, and if the USB is in you should be able to figure out which one it is (it'll be in /media for a start). 
Assuming that you've got access to the hard drive and can figure your USB key's location, you should be able to copy all the files you want out.  In a terminal, key commands are ```
ls
``` to show you what's in the directory you're in; ```
cp
``` is copy.  Try typing in ```
man cp
``` for the full info; man is the manual that's built into Linux.  If your Home directory is less than 4G, you could do cp /home/xxxx/* /media/disk/ -dpR and that should copy all the files out.

The reorganising of your driver; yep, they're all terminal commands.  Think of the terminal not so much as deep magic, it just that when someone's trying to explain what to do, it's an awful lot easier in a terminal.  Graphical is nice and pretty, but if anyone's ever tried to describe a painting to you you'll appreciate the problem with trying to explain how to do something in a GUI without pictures.

All five lines need to be typed into a terminal.  Or, if you're lazy ( I prefer "time- efficient"), highlight with the mouse, move to where you need to paste them and click the middle mouse button (push the wheel down).
The first two (starting with deb) add a couple of repositories to your system, so it knows it can go looking there for files you want to download.  
In your case, you need to edit the file that contains the software sources; do this by typing ```
sudo nano /etc/apt/sources.list
``` and typing in the above lines in the bottom of the file that opens.
The next one (sudo apt-key) gets the security key; without it your system will refuse to download the files.  apt-key will download the key from the address given.

The next line is an instruction to the package manager to update what files are available- you've just added a new source of files that it needs to sift through.  Finally, the final line actually gets the driver you need, and automatically installs it.  Once you've done that, if the driver was the issue you're away laughing.

Post back if you need more help.

---

### Post by Zyma on 2009-05-09
When I choose "netroot Drop to root shell prompt with networking", I end up in a window similar to the old days DOS Command Window (I mean before Windows came to the market): no mouse, one has to type a command for every line. 

Here is how the prompt looks like:
root@ubuntu:~#

So I typed "mount" then pressed ENTER and got this:

/host/ubuntu/disk/root.disk on /type ext3 (rw, error=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid, mode=0755)
proc on /proc type ...(I mean here so on)
Sysfs on ...
Varrun on ...
Varlock on ...
udev on ...
.
.
.
root@ubuntu:~#
I tpyped ls then ENTER and got:
DESKTOP
root@ubuntu:~#

If I understand you correctly, when I am in "root shell prompt" I should be able to use the mouse. This is not the case! What I get is a window which looks like a dos environment window (black background and the scripts are in white colour).

I need more help!

---

### Post by coffeeaddict22 on 2009-05-09
No, you may not be able to use the mouse.  You'll have to type if you can't.  Did you have your USB plugged in when you typed in ```
mount
```
because if you didn't, it wouldn't show up.  
It may not be automounting, either; fdisk -l will show you whether the system has seen it at all.  if it shows up with fdisk, but not in mount, you need to tell the system a little about it using the mount command.   That's a bit wordy: this will mount it in /media/disk:
```
mount -t vfat -o rw,nosuid,nodev,quiet,shortname=mixed,uid=1001,gid=100,umask=077,iocharset=utf8 /dev/sda1 /media/disk
```

when you get to the shell, type in ```
pwd
```
That stands for "print working directory", and tells you where you are in the filesystem; It should spit out something like ```
root
```
Try ```
cd /home
```; then ls (= "list" or something like that); should show you your home folder, which you can move into with cd ./xxx (cd is change directory; . is the directory you're in, and so ./ is the files and folders in that directory).

So, to summarise, boot into a recovery console, put in your USB, and then enter into the terminal the following commands:
```
mount
ls

```and try and spot the USB key.  It's usually called /media/disk/; it may not mount automatically, in which case 
fdisk -l[/CODE]which will tell you what it's called; then the mount line as above should make it visible to the system.  Then
```

cd /home/
pwd
cd ./xxxx/

```
where xxxx is your home directory, and you can then use cp to copy as much of it as you like to the location of your USB:
```
cp ./xxxx /media/disk
```
Once you've done that, fix the Intel driver.

---

### Post by Zyma on 2009-05-09
The USB key does not show up with "mount" but I can see it with "fdisk -l": two blocks of info; one for the hard disk (/dev/sda1, ...,/dev/sda5) and /dev/sdb1 for the usb key.

When I type in :

mount -t vfat -o rw,nosuid,nodev,quiet,shortname=mixed,uid=1001,gid=100,umask=077,iocharset=utf8 /dev/sda1 /media/disk

I get:
mount: mount point /media/disk does not exist
root@ubuntu:~#

Then, I type in ls and get:
Desktop
root@ubuntu:~#

I wonder if "the mount point" should be created and then do the mounting. If so, how to proceed?

An other question:
If I can guess the meaning of the "mount" line above (the long line), is to tell "/dev/sda1" to become "/media/disk". But "/dev/sda1" is part of the hard disk while "/dev/sdb1" is part of the usb key. I mean if one can change "/dev/sda1" into "/dev/sdb1" in the "mount" line. (Even doing so I get the same "/media/disk does not exist" ). I do not know if my understanding is correct.

---

### Post by coffeeaddict22 on 2009-05-09
You're getting there!

First, yes, you need a place to mount it.  Sorry, I should have added a command to make a directory to mount it on: 
```
mkdir /media/disk
```
then, you're right- to quote: 
When I type in :

mount -t vfat -o rw,nosuid,nodev,quiet,shortname=mixed,uid=1001,gid =100,umask=077,iocharset=utf8 **_/dev/sda1_** /media/disk

That's supposed to be where your USB key is- and as you've noted, it's on the system at /dev/sdb1, not dev/sda1.  So replace a with b, and you should be good to go!
IF you aren't sure about any command, you can always type in "man xxx" and you'll get some info.  Linux has a fairly extensive manual built in.

---

### Post by Zyma on 2009-05-10
Hi!

I have created the mount point. But when i type in:

mount -t vfat -o rw,nosuid,nodev,quiet,shortname=mixed,uid=1001,gid =100,umask=077,iocharset=utf8 /dev/sdb1 /media/disk

I get this:

[512.952559] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
root@ubuntu:~#

And then I type in ls, then ENTER and get:

Desktop
root@ubuntu:~#

Another thing: how to exit the linux manual? I typed "exit" and it didn't work!

---

### Post by Zyma on 2009-05-10
I just ignore 

[512.952559] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!

and continue to follow your instructions. I can see the name of my home dir! I am going to do the copy thing and then fix the Intel driver.

I will continue to ask for help though!

---

### Post by coffeeaddict22 on 2009-05-10
Yes, ignore it.  the long answer: 

It's an underlying problem Linux has: FAT (=File Allocation Table) is a MS trademarked system; if you've been watching the news, they shanghai'ed Tomtom about 2 months ago for using it.  Their approach is that file names should not be case sensitive; the alternative is what your Linux system runs on, where /MYsystem is a different file to /mysystem, because uppercase is seen as different to lowercase.  What it's telling you is when you transfer all those files, make sure the file names are different from each other in more than just the case, because once they are on the USB, they're on a FAT-based system.

Win won't read any Linux filesystem; Linux will read Win filesystems.  Because they get plugged into both, USB keys are usually formatted with a FAT system, and that's OK for now (MS are unlikely to sue you in the near future...).
As to how MS could extort money for the idea that a sentence could contain up to 256 letters... well, I think we thank the US Patent Office for that stroke of genius (and then try to ignore them).

---

### Post by Zyma on 2009-05-10
While fixing the Intel driver:

I have edited and saved the first two lines, namely

deb [http://ppa.launchpad.net/siretart/ppa/ubuntu](http://ppa.launchpad.net/siretart/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/siretart/ppa/ubuntu](http://ppa.launchpad.net/siretart/ppa/ubuntu) jaunty main

Then typed into the root the following line

sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 
0xce90d8983e731f79

and got this:

Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --recv-keys --keyserver keyserver.ubuntu.com 0xce90d8983e731f79
gpg: requesting key 3E731F79 from hkp server kyeserver.ubuntu.com
gpgkeys: HTTP fetch error 7: Failed to connect to 91.189.94.173: Unknown error 101
gpg: no valid OpenPGP data found
gpg: Total number processed: 0
root@ubuntu:~#

I need more help!

---

### Post by coffeeaddict22 on 2009-05-10
OK.  Two options.  Essentially it's saying it can't find the address.  Either the network is the problem, or the instruction.
First, try it without the sudo in front of it.  The terminal you're in is a root terminal; once again, apology for missing it, but it's unusual in Ubuntu.  
If that doesn't work, could you type in ```
ping -c5 91.189.94.173
``` and post the output back?  It should be not pinging.  You are in recovery mode with networking?  And what sort of network are you on? wired or wireless?

---

### Post by Zyma on 2009-05-10
Hi,
I am using a wired network (ADSL) and the network is on.

Without sudo, I get this:

Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --recv-keys --keyserver keyserver.ubuntu.com 0xce90d8983e731f79
**gpg: Invalid option "--rec-keys"**

ping -c5 91.189.94.173 gives this

Connect: Network is unreachable

---

### Post by coffeeaddict22 on 2009-05-10
Your network is playing games then.  Sorry, I meant not "Is the network on?" but "You are in recovery mode _with networking_, aren't you?
What does ```
ifconfig
``` return?

---

### Post by Zyma on 2009-05-10
Yes. (I am in "netroot Drop to root shell prompt with networking")

ifconfig spits out a lot info about my network connection. I do not know if that info can help in order to reach the 91.189.94.173 server.

---

### Post by coffeeaddict22 on 2009-05-10
The problem is that your network isn't working well enough to download; if it was, ping would return something like this: ```
ping -c 10 91.189.94.173
PING 91.189.94.173 (91.189.94.173) 56(84) bytes of data.
64 bytes from 91.189.94.173: icmp_seq=1 ttl=44 time=606 ms
64 bytes from 91.189.94.173: icmp_seq=2 ttl=44 time=526 ms
64 bytes from 91.189.94.173: icmp_seq=3 ttl=44 time=447 ms
64 bytes from 91.189.94.173: icmp_seq=4 ttl=44 time=368 ms
64 bytes from 91.189.94.173: icmp_seq=5 ttl=44 time=596 ms
64 bytes from 91.189.94.173: icmp_seq=6 ttl=44 time=516 ms
64 bytes from 91.189.94.173: icmp_seq=7 ttl=44 time=437 ms
64 bytes from 91.189.94.173: icmp_seq=8 ttl=44 time=358 ms
64 bytes from 91.189.94.173: icmp_seq=9 ttl=44 time=585 ms
64 bytes from 91.189.94.173: icmp_seq=10 ttl=44 time=506 ms

--- 91.189.94.173 ping statistics ---
10 packets transmitted, 10 received, 0% packet loss, time 9008ms
rtt min/avg/max/mdev = 358.575/495.000/606.525/85.247 ms

```
so the next question is where is it dropping out?  If it looks like you've got an interface, try
```
ifconfig down
``` then ```
ifconfig up
``` and see if that connects you.

---

### Post by Zyma on 2009-05-10
It seems that ubuntu 9.04 is not stable (problems with internet connections or slow connection). I have chosen to get rid of jaunty (using easyBCD free software) and reinstall ubuntu 8.10. Everything went fine. But.

I want to recover my data from the usb key (/media/disk), and when I plug in I can't see the files. If I go to Terminal and write cd /media/disk then ls, it comes nothing!

I appreciate your help.

---

### Post by coffeeaddict22 on 2009-05-11
Plug in your USB, try ```
fdisk -l
``` again, then mount it as before.  You should be able to access it then.  The problem will be that you accessed it as root user to put the files on, so you will probably have to do the same to move them.  In this setting, put "sudo" before each command you type in.

---

### Post by Zyma on 2009-05-11
The usb shows up when using "fdisk -l". To be sure. Do you mean I should do this?

sudo mkdir /media/disk

sudo mount -t vfat -o rw,nosuid,nodev,quiet,shortname=mixed,uid=1001,gid=100,umask=077,iocharset=utf8 /dev/sdb1 /media/disk

---

### Post by Zyma on 2009-05-11
"sudo mkdir /media/disk" tells me that /media/disk already exists.

"sudo mount -t vfat -o rw,nosuid,nodev,quiet,shortname=mixed,uid=1001,gid  =100,umask=077,iocharset=utf8 /dev/sdb1 /media/disk"

gives info on "mount" !

---

### Post by coffeeaddict22 on 2009-05-11
what happens when you just type in "mount" on its own?  Can you see the USB key?

---

### Post by Zyma on 2009-05-11
Here is what I get in sequence:

hakiza@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x38000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          15      120456   de  Dell Utility
/dev/sda2              16        1321    10485760    7  HPFS/NTFS
/dev/sda3   *        1321       30075   230969336    7  HPFS/NTFS
/dev/sda4           30075       30402     2621440    f  W95 Ext'd (LBA)
/dev/sda5           30075       30402     2620416   dd  Unknown

Disk /dev/sdb: 4016 MB, 4016046080 bytes
90 heads, 25 sectors/track, 3486 cylinders
Units = cylinders of 2250 * 512 = 1152000 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               4        3487     3917824    b  W95 FAT32
hakiza@ubuntu:~$

hakiza@ubuntu:~$ mkdir /media/disk
mkdir: cannot create directory `/media/disk': File exists
hakiza@ubuntu:~$ 


hakiza@ubuntu:~$ sudo mount -t vfat -o rw,nosuid,nodev,quiet,shortname=mixed,uid=1001,gid =100,umask=077,iocharset=utf8 /dev/sdb1 /media/disk
Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
One can change the type of mount containing the directory dir:
       mount --make-shared dir
       mount --make-slave dir
       mount --make-private dir
       mount --make-unbindable dir
One can change the type of all the mounts in a mount subtree
containing the directory dir:
       mount --make-rshared dir
       mount --make-rslave dir
       mount --make-rprivate dir
       mount --make-runbindable dir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .
hakiza@ubuntu:~$ 


hakiza@ubuntu:~$ sudo mount
/host/ubuntu/disks/root.disk on / type ext3 (rw,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
/dev/sda3 on /host type fuseblk (rw,nosuid,nodev,user_id=0,group_id=0,allow_other,blksize=4096)
lrm on /lib/modules/2.6.27-11-generic/volatile type tmpfs (rw,mode=755)
/host/ubuntu/disks/boot on /boot type none (rw,bind)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/hakiza/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=hakiza)
/dev/sdb1 on /media/disk type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)
hakiza@ubuntu:~$

---

### Post by coffeeaddict22 on 2009-05-11
This is your USB:
Disk /dev/sdb: 4016 MB, 4016046080 bytes
90 heads, 25 sectors/track, 3486 cylinders
Units = cylinders of 2250 * 512 = 1152000 bytes
Disk identifier: 0x00000000
ie, it's already mounted on your system.  Which is one less thing to worry about...
So now you can  get the data off it.  As I mentioned, because you transferred the data on as superuser, you may need to do "sudo cp" instead of "cp" to copy stuff back off it.

---

### Post by Zyma on 2009-05-11
If I do like this:
 sudo cp /media/disk/* /MyUSB
I get
cp: cannot stat `/media/disk/*': No such file or directory

And
 sudo cp /dev/sdb/media/disk/* /MyUSB
gives me
cp: cannot stat `/dev/sdb/media/disk/*': No such file or directory

I want to copy the content of the usb to the directory (already created) MyUSB.

---

### Post by coffeeaddict22 on 2009-05-11
OK.  Don't use /dev/sdb.  Linux treats everything on the system as a file; one implication of that is that every device plugged in has to have a place where it writes data; a "virtual file" if you like.  For mounted devices, /dev stores that information.  It's not meant to be a good place for you to get access to it though; that's what the /media directory is for.

Going on the response you're getting, what does ```
cd /media/disk/

followed by: 
ls
``` do?

---

### Post by Zyma on 2009-05-12
I get this:

hakiza@ubuntu:~$ cd /media/disk
hakiza@ubuntu:/media/disk$ ls
hakiza@ubuntu:/media/disk$ 

When I copied the files, I used this code:

root@ubuntu:~# cp /home/hakiza/* /media/disk -dpR

I hope the files were copied.

---

### Post by coffeeaddict22 on 2009-05-12
going on that, there wasn´t anything on that USB key... ls should show the files.  your copy command was correct for copying onto it, but wouldn´t copy off it- after cp, the first command is where the files come from, the second where they go to.

---

### Post by Zyma on 2009-05-12
But the usb has 4GB space and it shows 3.7GB free space. Can those files be hidden?

---

### Post by coffeeaddict22 on 2009-05-12
Good thought.  Brain failing.  Try ```
ls -l
```

---

### Post by Zyma on 2009-05-12
Thank you very much! I learned a lot from you. May God bless you!

---

