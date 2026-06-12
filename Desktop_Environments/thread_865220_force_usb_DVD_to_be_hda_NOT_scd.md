---
title: "force usb DVD to be hda NOT scd"
date: 2008-07-20
forum: Desktop Environments
---

### Post by neill on 2008-07-20
hi

i can't write to my external DVD-RW drive using DVD-R discs

this seems to be a known bug and it has been suggested that forcing the drive to be seen as /dev/hd rather than /dev/sd fixes this

i'd like to try as if i can get this to work i can finally abandon windoze forever !!

my drive is currently mapped as /dev/sdc2 (my 2 internal optical drives are scd0 and scd1)

how can i force the drive to /dev/hda0 or whatever's appropriate and will so doing 'break' the burning soft ?

ta

/neill

---

### Post by warp99 on 2008-07-20
> **neill said:**
> hi

i can't write to my external DVD-RW drive using DVD-R discs

this seems to be a known bug and it has been suggested that forcing the drive to be seen as /dev/hd rather than /dev/sd fixes this

i'd like to try as if i can get this to work i can finally abandon windoze forever !!
folders
my drive is currently mapped as /dev/sdc2 (my 2 internal optical drives are scd0 and scd1)

how can i force the drive to /dev/hda0 or whatever's appropriate and will so doing 'break' the burning soft ?

ta

/neill

The convention for writing to the drive has nothing to do with the /dev/scd or /dev/hda since everything is a *nix system is seen as a file or directory. Did you check the permissions on /dev/scd2 and at the mount point?

---

### Post by decoherence on 2008-07-20
which bug is it?

you should be able to do this by editing /etc/udev/rules.d/70-persistent-cd.rules

it *shouldn't* break things (assuming you don't butcher the file) .... but then again, changing it *shouldn't* fix things, either. but that's what a bug is, i guess.

---

### Post by neill on 2008-07-20
the bug in question is described here

[https://bugs.launchpad.net/ubuntu/+bug/202736](https://bugs.launchpad.net/ubuntu/+bug/202736)

and here

[https://bugs.launchpad.net/ubuntu/+source/cdrkit/+bug/15424](https://bugs.launchpad.net/ubuntu/+source/cdrkit/+bug/15424)

and in this thread

[http://ph.ubuntuforums.com/showthread.php?t=652740](http://ph.ubuntuforums.com/showthread.php?t=652740)

the hardware is good as i can write from XP (which i dual boot on the same machine) and i don't have any DVD+R to try

thanks

/neill

---

### Post by warp99 on 2008-07-20
Well according to the last post in this thread nothing was done but an upgrade to the kernel and the drive was seen as /dev/hdc:

[https://answers.launchpad.net/ubuntu/+question/7142](https://answers.launchpad.net/ubuntu/+question/7142)

Please check the permissions and the owner-group on /dev/scd2 like this:

```
ls -ls /dev/scd*
```

and also at the mount point:

```
ls -ls /media
```

You may have to change these in order to have the drive work properly.

---

### Post by neill on 2008-07-20
hi

```
neill@ubuntu-desktop:~$ ls -ls /dev/scd*
0 brw-rw----+ 1 root cdrom 11, 0 2008-07-20 18:09 /dev/scd0
0 brw-rw----+ 1 root cdrom 11, 1 2008-07-20 18:09 /dev/scd1
0 brw-rw----+ 1 root cdrom 11, 2 2008-07-20 17:09 /dev/scd2
neill@ubuntu-desktop:~$ ls -ls /media
total 12
0 drwxr-xr-x 10 neill neill    0 2008-07-20 17:12 bowzer
0 lrwxrwxrwx  1 root  root     6 2008-06-27 01:07 cdrom -> cdrom0
4 drwxr-xr-x  2 root  root  4096 2008-06-27 01:07 cdrom0
8 drwxrwxrwx  1 root  root  8192 2008-07-20 13:27 disk
```

i would have thought that was enough

no ?

thanks again

/neill

---

### Post by warp99 on 2008-07-20
Well your permissions and owner groups look correct, so we can rule this out. I would try this:

1) Edit the file '/etc/udev/rules.d/70-persistent-cd.rules' and remove all of the entires except the beginning comments section. The file will be regenerated during reboot.

2) Shutdown the computer and disable the other two optical drives physically or in the BIOS.

3) Plug in your USB DVD, power up and boot normally.

This may resolve any issues with either udev or your burning software. After this you can enable the other two drives. Some of the other suggestions were to burn at a slower speed and/or use DAO mode.

---

### Post by DrHu on 2008-07-21
[quote=neill]i can't write to my external DVD-RW drive using DVD-R discs[/quote]
Does it wirite with other media types, dvd +r, can you confirm the mdia types your specific dvd writer supports (sl or dl), and so on..

Also the /dev/hd* device type related to the hardware interfaces, that is a pata (older ide controller) detects all drives as /dev/hd*, where as sata ur usd detact as sd* 
--/dev/hda being the first ide device on that cable (master)

---

### Post by neill on 2008-07-21
thanks guys

i'm away from the PC for a couple of days but i'll have a play when i get back

thanks for the advice and support

/neill

---

