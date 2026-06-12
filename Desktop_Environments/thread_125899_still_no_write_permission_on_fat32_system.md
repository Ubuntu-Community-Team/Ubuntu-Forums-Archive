---
title: "still no write permission on fat32 system"
date: 2006-02-05
forum: Desktop Environments
---

### Post by rkakkar on 2006-02-05
the following is the entry in fstab:

/dev/hda5       /windows        vfat    iocharset=utf8,users,umask=000        0       0

also, ls -l gives me:

drwxrwxrwx   25 root root 65536 1970-01-01 05:30 windows


however, when i try:

rahul@ubuntu:/windows$ mkdir test
mkdir: cannot create directory `test': Read-only file system

where am i going wrong? :confused:

---

### Post by gerbman on 2006-02-05
[QUOTE=rkakkar]the following is the entry in fstab:

/dev/hda5       /windows        vfat    iocharset=utf8,users,umask=000        0       0

also, ls -l gives me:

drwxrwxrwx   25 root root 65536 1970-01-01 05:30 windows


however, when i try:

rahul@ubuntu:/windows$ mkdir test
mkdir: cannot create directory `test': Read-only file system

where am i going wrong? :confused:[/QUOTE]

Hello.  I think you just need to give yourself permission for the directory where you are mounting your FAT32 system. ```
sudo chmod you:you /windows
```Where "you" is your username.

EDIT:  In addition, it might be mounting read-only, try adding the option 'defaults' to your options list

Cheers!

---

### Post by rkakkar on 2006-02-05
Hi,

Thanks for the prompt reply, but it didn't work. 

Firstly I changed my fstab entry to:
/dev/hda5       /windows        vfat    defaults        0       0

but that didn't work. 

Also, I think you meant "sudo chown you:you /windows"

where I replaced you with my username.

I did that and it displayed:
chown: changing ownership of `/windows': Read-only file system

but on doing ls -l, it still showed:
drwxrwxrwx   25 root root 65536 1970-01-01 05:30 windows

btw, doesn't drwxrwxrwx indicate read/write/execute permissions to all?

---

### Post by gerbman on 2006-02-05
Sorry that didn't work. The line in my fstab that I use to do the same thing you're trying to do is ```
/dev/hdb1       /mnt/hd2        vfat    defaults,uid=gerb       0       0
```Where my username is 'gerb'.

Try unmounting /windows before doing the chown command (not chmod ;-))

---

### Post by manicka on 2006-02-05
my fstab for a shared fat32 r/w music drive, looks like this

/dev/hda9      /music          vfat     defaults,rw,umask=000 0 0


HTH

---

### Post by rkakkar on 2006-02-05
:cry: 

nope. i changed the entry to, but still says read-only filesystem.
/dev/hda5       /windows        vfat    defaults,uid=rahul        0       0

Also, when i tried to unmount /windows, it gave me the following error:
rahul@ubuntu:/windows$ sudo umount /windows
umount: /windows: device is busy

even though I wasn't accessing /windows at the time.

---

### Post by rkakkar on 2006-02-05
[QUOTE=manicka]my fstab for a shared fat32 r/w music drive, looks like this

/dev/hda9      /music          vfat     defaults,rw,umask=000 0 0


HTH[/QUOTE]
i changed the entry to:
/dev/hda5       /windows        vfat    defaults,rw,umask=000 0 0

then:rahul@ubuntu:/windows$ sudo mount -a

and finally to test it, 

rahul@ubuntu:/windows$ mkdir a
mkdir: cannot create directory `a': Read-only file system

:(

---

### Post by gerbman on 2006-02-05
[QUOTE=rkakkar]i changed the entry to:
/dev/hda5       /windows        vfat    defaults,rw,umask=000 0 0

then:rahul@ubuntu:/windows$ sudo mount -a

and finally to test it, 

rahul@ubuntu:/windows$ mkdir a
mkdir: cannot create directory `a': Read-only file system

:([/QUOTE]

Try doing ```
sudo mkdir a
```If that works then my guess is you need to get that chown command to execute. Does ```
fuser /windows
``` return any processes? If it does, kill them, unmount the drive, run the chown command and remount. Hope that works.

---

### Post by rkakkar on 2006-02-05
I hope this isn't a bug in my installed system. :(

It didn't work.

1)
rahul@ubuntu:/windows$ sudo mkdir a
mkdir: cannot create directory `a': Read-only file system

2)
rahul@ubuntu:/windows$ fuser /windows
/windows:             7260  7628c

3)
rahul@ubuntu:~$ kill 7260
rahul@ubuntu:~$ fuser /windows
/windows:
rahul@ubuntu:~$ sudo chown rahul:rahul /windows
chown: changing ownership of `/windows': Read-only file system
rahul@ubuntu:~$ sudo mount -a
rahul@ubuntu:~$ cd /windows
rahul@ubuntu:/windows$ mkdir a
mkdir: cannot create directory `a': Read-only file system
rahul@ubuntu:/windows$ sudo mkdir a
mkdir: cannot create directory `a': Read-only file system

---

### Post by gerbman on 2006-02-05
[QUOTE=rkakkar]I hope this isn't a bug in my installed system. :(

It didn't work.

1)
rahul@ubuntu:/windows$ sudo mkdir a
mkdir: cannot create directory `a': Read-only file system

2)
rahul@ubuntu:/windows$ fuser /windows
/windows:             7260  7628c

3)
rahul@ubuntu:~$ kill 7260
rahul@ubuntu:~$ fuser /windows
/windows:
rahul@ubuntu:~$ sudo chown rahul:rahul /windows
chown: changing ownership of `/windows': Read-only file system
rahul@ubuntu:~$ sudo mount -a
rahul@ubuntu:~$ cd /windows
rahul@ubuntu:/windows$ mkdir a
mkdir: cannot create directory `a': Read-only file system
rahul@ubuntu:/windows$ sudo mkdir a
mkdir: cannot create directory `a': Read-only file system[/QUOTE]

After you kill the process, can you unmount /windows? If you can, then I can't think of any reason why the chown command would fail after it is unmounted.  :-k

---

### Post by rkakkar on 2006-02-05
rahul@ubuntu:~$ fuser /windows
/windows:
rahul@ubuntu:~$ sudo umount /windows
umount: /windows: device is busy
umount: /windows: device is busy

---

### Post by gerbman on 2006-02-05
[QUOTE=rkakkar]rahul@ubuntu:~$ fuser /windows
/windows:
rahul@ubuntu:~$ sudo umount /windows
umount: /windows: device is busy
umount: /windows: device is busy[/QUOTE]

Quite odd. Perhaps a (gasp) windows approach:  take that line out of fstab and reboot. Then chown the folder and add the line back to fstab. Kinda stumped here, but it'll work eventually.

---

### Post by manicka on 2006-02-05
[QUOTE=rkakkar]i changed the entry to:
/dev/hda5       /windows        vfat    defaults,rw,umask=000 0 0

then:rahul@ubuntu:/windows$ sudo mount -a

:([/QUOTE]

keep that fstab entry and  try 

sudo mkdir /windows

the mount it using 

sudo mount /dev/hda5

---

### Post by rkakkar on 2006-02-05
[QUOTE=manicka]keep that fstab entry and  try 

sudo mkdir /windows

the mount it using 

sudo mount /dev/hda5[/QUOTE]
I already have the drive mounted at boot. the problem is that I can't write to it.

---

### Post by gerbman on 2006-02-05
manicka, what are the permissions (including user/group) for /music set as...just curious.

---

### Post by rkakkar on 2006-02-05
[QUOTE=gerbman]Quite odd. Perhaps a (gasp) windows approach:  take that line out of fstab and reboot. Then chown the folder and add the line back to fstab. Kinda stumped here, but it'll work eventually.[/QUOTE]
funny thing happened.

I removed the entry from fstab and restarted the machine. Then,
rahul@ubuntu:~$ sudo chown rahul:rahul /windows

worked. on ls -l, it showed that I was the owner for /windows.
However, once I re-entered the entry in fstab and did a:

sudo mount -a

the owner for /windows was changed back to root and it became read-only

---

### Post by gerbman on 2006-02-05
[QUOTE=rkakkar]funny thing happened.

I removed the entry from fstab and restarted the machine. Then,
rahul@ubuntu:~$ sudo chown rahul:rahul /windows

worked. on ls -l, it showed that I was the owner for /windows.
However, once I re-entered the entry in fstab and did a:

sudo mount -a

the owner for /windows was changed back to root and it became read-only[/QUOTE]

Setting ```
uid=you
``` in your mount options should fix the ownership stuff, but I'm unclear why it would still be mounting read-only. The "defaults" option includes "rw".

---

### Post by rkakkar on 2006-02-05
[QUOTE=gerbman]Setting ```
uid=you
``` in your mount options should fix the ownership stuff, but I'm unclear why it would still be mounting read-only. The "defaults" option includes "rw".[/QUOTE]
$ sudo chown rahul:rahul /windows
$ ls -l
drwxrwxrwx   25 rahul root 65536 1970-01-01 05:30 windows

$ cd /windows
$ mkdir a
mkdir: cannot create directory `a': Read-only file system

fstab:
/dev/hda5       /windows        vfat    defaults,rw,umask=000,uid=rahul 0 0

---

### Post by gerbman on 2006-02-05
Well I'm stumped. I pasted the same options into my fstab and everything works fine. Hope manicka has better words of wisdom for you.  :???:

---

### Post by rkakkar on 2006-02-05
[QUOTE=gerbman]Well I'm stumped. I pasted the same options into my fstab and everything works fine. Hope manicka has better words of wisdom for you.  :???:[/QUOTE]
damn! :(

thanks though! I really hope I can get this to work, cause if I can't write to my fat32 partition, no point in me keeping linux and i'll have to go back to windows (which I JUST DON'T want to!)

---

### Post by gerbman on 2006-02-05
[QUOTE=rkakkar]if I can't write to my fat32 partition, no point in me keeping linux and i'll have to go back to windows (which I JUST DON'T want to!)[/QUOTE]

My last stab (motivated by your last statement). Let's start over. Unmount /windows and do ```
sudo rmdir /windows
```Fresh start. Now ```
mkdir /windows
```and add ```
/dev/hda5       /windows        vfat    defaults,uid=rahul       0       0
```to fstab, followed by ```
sudo mount /windows
```I used this exact sequence of operations on my FAT32 partition and it works.

---

### Post by lol on 2006-02-05
First, what is the output of 'mount'. This should list all the mounted filesystems, with their options.

In your fstab, you should have at least the following options:
- defaults : same as rw, suid, dev, exec, auto, nouser, and async
- user
- umask=000

or:
- rw
- exec
- user
- umask=000

For example, in my fstab, I have (some options are actually useless!):
/dev/hda1 /mnt/windows vfat defaults,user,exec,auto,umask=000,noatime,utf8 0 0

The IMPORTANT thing is: after modifying /etc/fstab, you really need to umount/remount the filesystem. If 'sudo umount /windows' complains that the filesystem is busy, try 'fuser -muv /windows' or 'fuser -km /windows' before trying to umount the filesystem again. In the worst case scenario, if you still cannot umount it, simply reboot the computer, and check again the state of the filesystems with 'mount'.

---

### Post by rkakkar on 2006-02-05
[QUOTE=gerbman]My last stab (motivated by your last statement). Let's start over. Unmount /windows and do ```
sudo rmdir /windows
```Fresh start. Now ```
mkdir /windows
```and add ```
/dev/hda5       /windows        vfat    defaults,uid=rahul       0       0
```to fstab, followed by ```
sudo mount /windows
```I used this exact sequence of operations on my FAT32 partition and it works.[/QUOTE]
:(

---

### Post by rkakkar on 2006-02-05
[QUOTE=lol]First, what is the output of 'mount'. This should list all the mounted filesystems, with their options.

In your fstab, you should have at least the following options:
- defaults : same as rw, suid, dev, exec, auto, nouser, and async
- user
- umask=000

or:
- rw
- exec
- user
- umask=000

For example, in my fstab, I have (some options are actually useless!):
/dev/hda1 /mnt/windows vfat defaults,user,exec,auto,umask=000,noatime,utf8 0 0

The IMPORTANT thing is: after modifying /etc/fstab, you really need to umount/remount the filesystem. If 'sudo umount /windows' complains that the filesystem is busy, try 'fuser -muv /windows' or 'fuser -km /windows' before trying to umount the filesystem again. In the worst case scenario, if you still cannot umount it, simply reboot the computer, and check again the state of the filesystems with 'mount'.[/QUOTE]
okay.. this worked, but not properly.

here is the thing.

i tried to unmount the filesystem, but it said that the device was busy.
i noticed some command called 'gam_server' was accessing the /windows filesystem. if i killed the process, another process immediately would occupy it. So I settled for rebooting the system...

After reboot, I was able to create a directory on /windows through the terminal!! BUT, if I tried the same through the nautilus file browser, I would get the read-only file system error and THEN if I tried again to create a directory through the terminal, it would give me the read-only filesystem error, unless I restarted the system.

:(

---

### Post by lol on 2006-02-05
can you please post the output of the 'mount' command?

---

### Post by rkakkar on 2006-02-05
well since it was a clean install, I reinstalled ubuntu, and followed the steps mentioned here and it worked this time!! :) 

Thanks a lot for the support guys! :cool:

---

