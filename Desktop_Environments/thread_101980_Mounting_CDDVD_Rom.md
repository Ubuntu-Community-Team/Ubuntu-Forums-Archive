---
title: "Mounting CD/DVD Rom"
date: 2005-12-11
forum: Desktop Environments
---

### Post by CharlieC on 2005-12-11
When I put in a blank CD or DVD to copy to and attempt to mount the drive I get this:

cc@ubuntu:~$ sudo mount /dev/cdrom1 /mnt
mount: you must specify the filesystem type

Here is fstab:

/dev/hdd             /media/cdrom1        subfs      user,noauto           0 0

I get the same error with /dev/hdd

In the mount directory it is cdrom1 and when I try to mount it with /media/cdrom1 I get the same error.

I am clueless what this is all about can someone help me out.

TIA
Charlie

---

### Post by infoseeker on 2005-12-11
#sudo mount -t iso9660 /dev/.........       for cdroms

#sudo mount -t ntfs /dev/.............         for ntfs drives

---

### Post by dcstar on 2005-12-11
[QUOTE=CharlieC]When I put in a blank CD or DVD to copy to and attempt to mount the drive I get this:

cc@ubuntu:~$ sudo mount /dev/cdrom1 /mnt
mount: you must specify the filesystem type

Here is fstab:

/dev/hdd             /media/cdrom1        subfs      user,noauto           0 0

I get the same error with /dev/hdd

In the mount directory it is cdrom1 and when I try to mount it with /media/cdrom1 I get the same error.

I am clueless what this is all about can someone help me out.

TIA
Charlie[/QUOTE]

Here is my fstab entry, you may want to try it:

/dev/hdd        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0

---

### Post by infoseeker on 2005-12-11
This is my fstab entry for cdroms :

/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

and it automounts  :)

---

### Post by kabus on 2005-12-11
I don't think you can mount a blank cd because it doesn't have a filesystem yet.
Just put it in your drive and write to /dev/yourdrive with whatever burning tool you are using.

---

### Post by dcstar on 2005-12-11
[QUOTE=kabus]I don't think you can mount a blank cd because it doesn't have a filesystem yet.
Just put it in your drive and write to /dev/yourdrive with whatever burning tool you are using.[/QUOTE]
Correct, but the automounter should start up whatever default burner program is set when a blank disk is inserted.

The fstab looked wrong anyway, so possibly that was confusing the automount.

---

### Post by CharlieC on 2005-12-11
I tried both suggestions in either case here is what I get, this is a blank DVD.

cc@ubuntu:/$ sudo mount -t iso9660 /dev/cdrom1 /mnt
mount: block device /dev/cdrom1 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/cdrom1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

cc@ubuntu:/$ dmesg | tail
[4297770.482000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4297770.482000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297770.590000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4297770.590000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297770.742000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4297770.742000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297853.292000] cdrom: This disc doesn't have any tracks I recognize!
[4297871.975000] attempt to access beyond end of device
[4297871.975000] hdd: rw=0, want=68, limit=4
[4297871.975000] isofs_fill_super: bread failed, dev=hdd, iso_blknum=16, block=16
cc@ubuntu:/$

---

### Post by CharlieC on 2005-12-11
I think it does automount, I was trying it again. I changed my fstab to

#/dev/hdd             /media/cdrom1        subfs      user,noauto           0 0
/dev/hdd             /media/cdrom1        udf,iso9660 user,noauto 0 0

Does this seem OK?

Sorry I am so dense, noob syndrome.

Charlie

---

### Post by infoseeker on 2005-12-11
For a blank CD / DVD I use 'k3b' to copy data, etc.  I'm not sure what would happen if you attempted to (manually) mount a blank CD / DVD.

---

### Post by CharlieC on 2005-12-11
Thanks, 
K3b works fine.
Does anyone know about DVD:RIP
The error there is:
cdrecorder device (n.n.n or filename) X,0,X has not format n,n,n and is no file:NOT OK.
Any idea what that is about?
Ripping DVD's, which I own is the last thing that I cant do on Ubuntu that I can do on windows.

Charlie

---

