---
title: "Mounting an image - odd error"
date: 2009-03-05
forum: General Help
---

### Post by Aped on 2009-03-05
Hoy, I want to mount an .iso of Diablo II: Lord of Destruction (classic) to get back into the feel of it before D3 comes out; much to my consternation, however, my iso won't load! What gives, gurus? 

What I said: 

sudo mkdir /media/iso
sudo mount -t iso9660 /Desktop/LoD.ISO /media/iso -o loop
(I also tried putting -o loop in front; no change)


What it said: 
```
mount: wrong fs type, bad option, bad superblock on /dev/loop0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

The relevant bits from dmesg | tail: 
```
[  196.077618] loop: module loaded
[  303.858862] ISOFS: Unable to identify CD-ROM format.
[  473.070147] ISOFS: Unable to identify CD-ROM format.

```

Is this because of a format issue, ie iso9660? Or is it a filesystem problem, ie FAT vs Ext or something? Any thoughts on the issue would be appreciated.

EDIT: I tried using -t msdos as well. The same error occurred, but a new message was logged in dmesg: 
```
[  746.872460] FAT: invalid media value (0x11)
[  746.872466] VFS: Can't find a valid FAT filesystem on dev loop0.

``` 

Don't know if this is relevant or not; figured I'd slap it on here.

---

### Post by kahlil88 on 2009-03-05
Perhaps the problem lies in the file location - it should be **~/Desktop** instead of **/Desktop** unless you have crazy mount points :P

---

### Post by Aped on 2009-03-05
> **kahlil88 said:**
> Perhaps the problem lies in the file location - it should be **~/Desktop** instead of **/Desktop** unless you have crazy mount points :P

Oh durr, thanks. Will see how that works. 

Am I an idiot? Maybe. See sig for details.

---

### Post by jARLAXL on 2009-03-05
[http://ubuntuforums.org/showthread.php?t=704350](http://ubuntuforums.org/showthread.php?t=704350)

It is made for hardy but reported to work for intrepid too!

---

### Post by getbuck911 on 2010-01-19
Alright, Im trying to do a game I downloaded.

/home/user/Desktop/GTA IV PC Version/GTA IV DVD 1.iso~~~~Open

/home/user/Desktop/GTA Final~~~~Open


Heres the error it says.....

An error occured
 wrong fs type, bad option, bad superblock on /dev/loop0,       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so



Can anybody help???:KS

---

### Post by getbuck911 on 2010-01-19
Ok, I restarted my computer, and made sure that no programs other than gmount-iso were running. I got this message:



An error occured

       In some cases useful info is found in syslog - try
       dmesg | tail  or so

SSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSS

Then it went back to the same error as before:




An error occured
 wrong fs type, bad option, bad superblock on /dev/loop0,       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

---

### Post by ralph.p on 2010-09-26
I had to same error.

```
ralphp@ralphp-dell:~$ dmesg | tail
[ 4920.490539] composite sync not supported
[ 4921.554491] composite sync not supported
[ 4922.622277] composite sync not supported
[ 4923.170388] composite sync not supported
[ 5070.084706] ISOFS: Unable to identify CD-ROM format.
[ 5073.729719] lo: Disabled Privacy Extensions
[ 5274.928783] ISOFS: Unable to identify CD-ROM format.
[ 5288.890276] ISOFS: Unable to identify CD-ROM format.
[ 5650.700674] ISOFS: Unable to identify CD-ROM format.
[ 6477.488032] ISOFS: Unable to identify CD-ROM format.

```

```
/ralphp@ralphp-dell:~$ sudo fuseiso blabla.iso /media/fuseiso
init: wrong standard identifier in volume descriptor 0, skipping..
init: wrong standard identifier in volume descriptor 1, skipping..
init: wrong standard identifier in volume descriptor 2, skipping..
init: wrong standard identifier in volume descriptor 3, skipping..
init: wrong standard identifier in volume descriptor 4, skipping..
init: wrong standard identifier in volume descriptor 5, skipping..
init: wrong standard identifier in volume descriptor 6, skipping..
init: wrong standard identifier in volume descriptor 7, skipping..
init: wrong standard identifier in volume descriptor 8, skipping..
init: wrong standard identifier in volume descriptor 9, skipping..
init: wrong standard identifier in volume descriptor 10, skipping..
init: wrong standard identifier in volume descriptor 11, skipping..
init: wrong standard identifier in volume descriptor 12, skipping..
init: wrong standard identifier in volume descriptor 13, skipping..
init: wrong standard identifier in volume descriptor 14, skipping..
init: wrong standard identifier in volume descriptor 15, skipping..
init: wrong standard identifier in volume descriptor 16, skipping..
init: wrong standard identifier in volume descriptor 17, exiting..
```

gmount gives me the demesg error
AceToneIso gives me "error, could not mount"


> Apparently ubuntu has a hard time mounting certain iso files if they have been created in Windows XP or Vista. This is something that needs to be fixed in future distros. People aren't going to be wanting to switch over to Ubuntu if files they backed up on CD or DVD from XP and Vista don't "just work"!

Other iso's worked fine.

---

### Post by asuastrophysics on 2011-02-02
So I take it there is no solution to this error? I'm having the same problem.

---

### Post by Tosho on 2011-04-11
same error when I try to mount with GMount and Furius. but only for 2 .iso. the others worked perfect for now.

---

