---
title: "Cannot Login to Desktop"
date: 2009-06-14
forum: Desktop Environments
---

### Post by lotusalive on 2009-06-14
Hi all...  Don't know if it's even worth a try to fix this, but it'd be nice to find out why it happened if at all possible.  I have experienced some kind of error with my video card running in low-mode.  After a 3 min load from Synaptics, and a required restart, I receive this message:  

Update Configuration to Solve:  
(EE) GARTinit: Unable to open /dev/agpgart (No such file or directory) 
(EE) (drm) drm Open failed
(EE) Intel(0) [dri] DRIScreen init failed.  Disabling DRI
(EE)  Intel(0): Failed to allocate framebuffer.  Is your Video RAM set too low?
(EE) Intel(0): Couldn't allocate video memory   

And only button choice is: [ok]

Other explanations in grub: 

a)  apache2: Could not reliably determine server's fully qualified domain name, just using 127.0.1.1 for Server Name

b)  jackd fail

c)  Alsa is not active, cannot start TiMidity++ Alsa midi emu

Since I've never seen this kind of error, I don't know what I'm dealing with, and don't know the grub commands well enough to untangle.

Am running on LiveCD to send this message.  I'd like to retrieve my system and desktop files instead of a re-install.

Also, it seems to have something to do with x11, although I did not specifically mean to install any programs for x11 prior to the required re-start: 

2.6.28-11-server #42-Ubuntu SMP X Protocol Version 11, Linux 2.6.24-23-server i686 Ubuntu

I thought I was running only i386 programs for this 2 year old Dell emachine, with Intel 945 graphics card.

All suggestions welcome.  Thanks in advance.

---

### Post by leef on 2009-06-14
I take it that GDM (the login screen) didn't start. Are you able to log in by changing to a another VT (press Crl+Alt+F2) and entering your login details. You can perhaps get some more info with this command which might give us a clue (if you can get to the Terminal that is);

```
cat /var/log/Xorg.0.log | grep -e "(WW)" -e "(EE)"
```

Also the "dmesg" command might be useful since this problem seems to be effecting other systems, such as alsa.

It should at the very least be possible to recover your data;

from the live cd;
```

sudo fdisk -l # find the linux partition
sudo mkdir /media/hdd
sudo mount /dev/sda2 /media/hdd # mount the root fs (sda2 is just an example it could be different)

```

you should then see an icon for the drive on the desktop, plug in a usb disk and copy the user users home directory (/home/USER) over to the usb drive, if there is too much data for this you might have to use gparted to resize partitions, etc. Good luck.

---

### Post by lotusalive on 2009-06-14
Thanks leef !  That's right, no login screen, no terminal, surprised and sorry to say the least !  Thanks for the live-cd commands.  I'll try to get it and post back. Thanks much !:KS

I have a brand new 512mb USB, so there should be plenty of space on it for my desktop, just not had time today, and wanted to try the terminal command at the login / grub line, just for shts and giggles...  will get to it soon.  Live cd is keeping me happy for the day, and keeping my mind off of this !  lol !

---

### Post by lotusalive on 2009-06-18
It should at the very least be possible to recover your data;

from the live cd;
```

sudo fdisk -l # find the linux partition
sudo mkdir /media/hdd
sudo mount /dev/sda2 /media/hdd # mount the root fs (sda2 is just an example it could be different)

```

you should then see an icon for the drive on the desktop, plug in a usb disk and copy the user users home directory (/home/USER) over to the usb drive, if there is too much data for this you might have to use gparted to resize partitions, etc. Good luck.[/QUOTE]

When I try these commands with the live cd, it is requesting: 

ubuntu@ubuntu:~$ sudo mkdir /media/hdd
ubuntu@ubuntu:~$ sudo mount /dev/sda2 /media/hdd # mount the root fs
mount: you must specify the filesystem type
ubuntu@ubuntu:~$ sudo mount /dev/sda2 /media/hdd # mount the root fs desktop-sol
mount: you must specify the filesystem type
ubuntu@ubuntu:~$ 

I'm not sure it's /sda2 either, tried it, and with fs as name of what I want to retrieve, but as you can see...   

Will someone suggest to me what 'filesystem type' should be expressed, please ?  Thanks for this.  I named a ton of photos I'd hate to lose.

Also, I think I brought this on by loading 4 kernels offered in Synaptics, without reading each one, dah.  Sometimes I get so Synaptics-slap-happy that I slap myself.  ;>)(

---

### Post by leef on 2009-06-18
Hi, just to check did you do he "fdisk -l" command o help determine which partition is your root partition. If you did and you root partition is on /dev/sda2 (which is the default for ubuntu when not dual boot), then you could try;

```
mount -t ext3 /dev/sda2 /media/hdd
```
assuming that the root fs is ext3, substitute ext3 for you fs type

I didn't include this because usually the file system type is determined automatically.

---

### Post by lotusalive on 2009-06-18
Thx leef for keeping up with me.  No, I was working, and did not try it yet.  I will only have the grub line, I believe.  I could try it in the live-disk terminal, but it might not work there... ?  Anyway, I'll try it now and post back.  Thx.

Here are the live-cd terminal results for the fdisk command:

ubuntu@ubuntu:~$ sudo fdisk -l # find the linux partition

Disk /dev/sda: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x01fa01fa


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19650   157838593+  83  Linux
/dev/sda2           19651       20023     2996122+   5  Extended
/dev/sda5           19651       20023     2996091   82  Linux swap / Solaris

Disk /dev/sdf: 1049 MB, 1049558528 bytes
32 heads, 63 sectors/track, 1016 cylinders
Units = cylinders of 2016 * 512 = 1032192 bytes
Disk identifier: 0x714357f6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               1        1016     1024096+   6  FAT16

Disk /dev/sdg: 503 MB, 503709696 bytes
16 heads, 32 sectors/track, 1921 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Disk identifier: 0xcb0a3bc5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1   *           1        1922      491888    6  FAT16
ubuntu@ubuntu:~$



Going to try a regular restart without the live-cd and the command: 
cat /var/log/Xorg.0.log | grep -e "(WW)" -e "(EE)" at the line I have, don't know if it's a grub line, or a login line.

Okay:  I have a login line that leads to a terminal line !  So, results of: cat /var/log/Xorg.0.log | grep -e "(WW)" -e "(EE)" is:

(WW) warning  (EE) error  (NI) not implemented  (??) unknown

(WW) The directory "user/share/fonts/X11/cyrillic" does not exist.
(WW) intel(0): libpciaccess reported 0 rom size, guessing 64kB
(EE) GARTInit: Unable to open /dev/agp gart (No such file or directory)
(WW) intel(0): /dev/agpgart is either not available, or no memory is available
(WW) intel(0): DRI2 requires UXA
(EE) [drm] drmOpen failed.
(EE) intel(0): [dri] DRIScreen Init failed. Disabling DRI.
(EE) intel(0): Failed to allocate framebuffer. Is your Video RAM set too low?
(@@) intel(0): Couldn't allocate video memory
sol@sol-desktop:~$ * Reloading web server config apache2
* Reloading Common Unix Printing System: cupsd
* Reloading System log daemon...  (I waited until it finished.)

Also, in BIOS info, fyi: L2 Cache RAM 2MB, Total Memory 1024MB (Memory Channel A Slot 0 is Not Installed, but Memory Channel B Slot 0 is 1024MB)  And Video Config: IGD DVMT Memory <128MB>, Primary Video Adaptor <Auto>
 
Please advise when you have a moment.  I don't think I am well-versed enough to untangle this... if it makes sense to you, and you can think of anything I could try, I'd really appreciate it.  Thanks.  

(Also, haven't retrieved desktop yet due to my confusion over exactly what to specify for it to do so...)

---

### Post by lotusalive on 2009-06-23
Can anyone tell me what this really means ?  And if I can retrieve my files before I re-install ?

Root / is on ext3, according to gparted, and I can see the data is there...

ubuntu@ubuntu:~$ mount -t ext3 /dev/sda2 /media/hdd
mount: only root can do that
ubuntu@ubuntu:~$ sudo mount -t ext3 /dev/sda2 /media/hdd
mount: mount point /media/hdd does not exist
ubuntu@ubuntu:~$

Never freaking mind !  LOL  !  I GOT THE DESKTOP ICON OF MY HARD DRIVE !  DAH !   THANKS LEEF !

D.O.A.:  Photos are fine to copy, but my Documents all say: Permission Denied, so I can't move them to the USB?

Assistance appreciated.

---

### Post by lotusalive on 2009-06-23
D.O.A.: My own Documents and many of the Photos will not copy to USB, all saying 'Permission Denied.'  Since the operation did not require my password to create the Icon, the computer thinks I'm not me !  :confused:

Still fiddling with this:

ubuntu@ubuntu:~$ sudo mount -t ext3 /dev/sda1 /media/hdd
mount: mount point /media/hdd does not exist
ubuntu@ubuntu:~$ 

Why doesn't a mount point exist ?  

All assistance appreciated.

---

