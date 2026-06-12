---
title: "help mounting cue. with cdemu"
date: 2005-10-06
forum: Desktop Environments
---

### Post by floyd27 on 2005-10-06
I have it installed..
I can mount the image
I cant get it to work?

roderick@ubuntu:~$ cdemu 0 angel_hov1.cue
roderick@ubuntu:~$ cdemu -s
Drive Loaded Comment
  0:     1   angel_hov1.cue
  1:     0   NO_CD_LOADED
  2:     0   NO_CD_LOADED
  3:     0   NO_CD_LOADED
  4:     0   NO_CD_LOADED
  5:     0   NO_CD_LOADED
  6:     0   NO_CD_LOADED
  7:     0   NO_CD_LOADED

roderick@ubuntu:~$ mount /dev/cdemu/0 /mnt/cdrom
mount: only root can do that
roderick@ubuntu:~$ mount /dev/cdemu/0 /mnt/cdrom
mount: only root can do that
roderick@ubuntu:~$ su
Password:
root@ubuntu:/home/roderick # cdemu 1 angel_hov1.bin
Invalid header of the cue-file </home/roderick/angel_hov1.bin>
root@ubuntu:/home/roderick #

I only tried this 1 file.(the only 1 i have ) If you think it may be the flie itself i can DL another.. But does what i have so far look right?
thanx

---

### Post by floyd27 on 2005-10-06
I thinkit may have something to do with this line..

"mount /dev/cdemu/0 /mnt/cdrom"

Thsi is the line to mount the cue image after i added it to the cdemu list...but it does not work..

(i now have 2 images in cdemu on drive 0 and 1 ) but they wont mount

root@ubuntu:/home/roderick/Desktop # mount /dev/cdemu/1 /mnt/cdrom
mount: block device /dev/cdemu/1 is write-protected, mounting read-only
mount: you must specify the filesystem type
root@ubuntu:/home/roderick/Desktop # mount /dev/cdemu/1 -t iso9660 /mnt/cdrom
mount: block device /dev/cdemu/1 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/cdemu/1,
       missing codepage or other error
       (could this be the IDE device where you in fact use
       ide-scsi so that sr0 or sda or so is needed?)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

---

### Post by floyd27 on 2005-10-06
root@ubuntu:/home/roderick # mount /dev/cdemu/0 /mnt/cdrom
mount: block device /dev/cdemu/0 is write-protected, mounting read-only
mount: you must specify the filesystem type
root@ubuntu:/home/roderick #  

What does "file system type" mean?  iso,cue,ext3???? and where would i go about putting that info at?

---

### Post by floyd27 on 2005-10-06
I think im real close to getting this to work..
I just need a little help twith the last step..
I dont think the command to mount the file is correct for ubuntu..
What command are you guys using to mount the cue. in cdemu?
thanx....

---

### Post by NutMonkey on 2005-10-06
I've never used cdemu before, but you probably need to run in on the .cue file and not the .bin file
cdemu 1 angel_hov1.cue
instead of
cdemu 1 angel_hov1.bin

---

### Post by floyd27 on 2005-10-06
Sorry i have tried both ways..just posted the bin way though...
thnax for your reply though

---

### Post by NutMonkey on 2005-10-06
Is the cdemu kernel module loaded?  Does it show up in lsmod?

---

### Post by floyd27 on 2005-10-07
normally when i do this command it tells me whick of the 0-7 virtual drives is loaded..
Now it says this..

roderick@ubuntu:~$ cdemu -s
cdemu: cdemu kernel module not loaded
roderick@ubuntu:~$

but usually it does tell me and i would assume that means the module woudl be loaded. however right now it doesnt seem to be..

---

### Post by NutMonkey on 2005-10-07
Run "lsmod" and see if it's listed.  If not, run "sudo modprobe cdemu" to load it.  This will load the module, but if you reboot it won't be loaded anymore.  To have it automatically loaded at boot time, add cdemu to the /etc/modules file.  Try the following sequence of commands and copy the output:

lsmod
sudo modprobe cdemu
sudo cdemu 0 angel_hov1.cue
cdemu -s
sudo umount /mnt/cdrom
sudo mount -t iso9660 /dev/cdemu/0 /mnt/cdrom
dmesg | tail

---

### Post by floyd27 on 2005-10-07
thanx..
here is what i get.. Still not working...

the module is loaded..
roderick@ubuntu:~$ lsmod
Module                  Size  Used by
cdemu                  11276  0
proc_intf               3972  0
freq_table              4100  0


roderick@ubuntu:~$ sudo cdemu 0 angel_hov1.cue
roderick@ubuntu:~$ cdemu -s
Drive Loaded Comment
  0:     1   angel_hov1.cue
  1:     0   NO_CD_LOADED
  2:     0   NO_CD_LOADED
  3:     0   NO_CD_LOADED
  4:     0   NO_CD_LOADED
  5:     0   NO_CD_LOADED
  6:     0   NO_CD_LOADED
  7:     0   NO_CD_LOADED

roderick@ubuntu:~$ sudo umount /mnt/cdrom
umount: /mnt/cdrom: not mounted
roderick@ubuntu:~$ sudo mount -t iso9660 /dev/cdemu/0 /mnt/cdrom
mount: block device /dev/cdemu/0 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/cdemu/0,
       missing codepage or other error
       (could this be the IDE device where you in fact use
       ide-scsi so that sr0 or sda or so is needed?)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

roderick@ubuntu:~$ dmesg | tail
[fglrx] max   Inv = 0
[fglrx] total Inv = 0
[fglrx] total TIM = 0
[fglrx] total FB  = 0
[fglrx] total AGP = 32768
cdemu:917: ver 0.6.0 loaded.  Registered 8 cdemus.
cdemu:605: loaded angel_hov1.cue cd (2 track[s]) on drive cdemu0 by uid 0
cdemu:193: Normal read not possible for track mode '20'
end_request: I/O error, dev cdemu0, sector 64
isofs_fill_super: bread failed, dev=cdemu0, iso_blknum=16, block=32
roderick@ubuntu:~$           


any ideas....

---

### Post by NutMonkey on 2005-10-07
It looks like you're trying to mount an SVCD, which can't be done according to the FAQ at cdemu.org:

Q: I am trying to mount an [S]VCD but the mount command keeps failing!
A: Of course it does not work ! An [S]VCD contains no real filesystem. You need to read it in raw mode.
e.g. use MPlayer or xine to watch the movie. Just point the player to the virtual device (i.e. /dev/cdemu/0)
But Windows does you say !? Windows lies to you ;-) Windows has the problem that it can't read cds in raw mode, so the ATAPI driver creates a virtual file system, so Windows programs can read it. This layer is not needed in Linux since we can just handle the raw format with our media players. ;-)


If it's not an SVCD it appears to be some weird file with a nonstandard track mode, maybe the file is corrupt.

---

### Post by floyd27 on 2005-10-07
I will try to play it in mplayer (previou attemps have failed) but not while mounted in cdemu..

I have burned the file and played it in windows to make sure it worked..
I will let you know how it goes..
I dont know why they would be labled cue. and bin. if they are different files though  \p.s i did have to extract them at first??
anyway theks for the help ill let you know..

---

