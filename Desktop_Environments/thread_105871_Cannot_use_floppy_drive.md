---
title: "Cannot use floppy drive"
date: 2005-12-19
forum: Desktop Environments
---

### Post by guido32 on 2005-12-19
Hello everyone.  Let me start by saying I am a newbie.  I have been using kubuntu since September and love it.  However recently I have encountered a problem that I cannot figure out.  

When I try to open up files from on a disk from my floppy drive I get the following error:

"mount: I could not determine the filesystem type, and none was specified
Please check that the disk is entered correctly."

The disk is entered correctly, and the drive spins.  However, I cannot access the files on the disk itself.  Any ideas?

Any information is appreciated.  Thanks

---

### Post by sabitha on 2005-12-19
try fix with

code :
$ sudo kedit /etc/fstab

change the lines 

/dev/fd0        /media/floppy0  auto   rw,user,noauto  0       0

with this one

/dev/fd0        /media/floppy0  auto,vfat   rw,user,noauto  0       0

this is what i have :

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto,vfat   rw,user,noauto  0       0

save the changes and reboot
:p

---

### Post by guido32 on 2005-12-24
I tried the code provided and got the following error:

bash: $: command not found

Any other suggestions? 

Thanks

---

### Post by paddyg on 2005-12-24
if you still want to try what sabitha said, just don't use $ in the code, just
```
sudo kedit /etc/fstab
```

---

### Post by cwaldbieser on 2005-12-24
[QUOTE=paddyg]if you still want to try what sabitha said, just don't use $ in the code, just
```
sudo kedit /etc/fstab
```[/QUOTE]
It is a little confusing to beginners, but the "$" at the beginning of a command is the prompt, like
```

C:\>

```
in Windows.  A "#" is a little trickier, since it can mean the prompt for the root user, or it can be a comment if it is in a script.

---

### Post by guido32 on 2005-12-24
When I try that code, this is the error message:

sudo: kedit: command not found

Am I doing something wrong?

---

### Post by der_joachim on 2005-12-25
[QUOTE=guido32]When I try that code, this is the error message:

sudo: kedit: command not found

Am I doing something wrong?[/QUOTE]

Substitute the 'kedit' part with the name of your favourtie text editor and you're set. I'd recommend gvim, but it's not very newbee-friendly to say the least. ;)

Have fun.

---

### Post by palsyboy on 2005-12-25
Perhaps try "kate" instead of "kedit".  Kate is extremely newbie-friendly.

If Kate gives you the same "command not found" error, try
```
sudo apt-get install kate
```
And then try
```
sudo kate /etc/fstab
```
to add the lines sabitha recommended.

---

### Post by guido32 on 2005-12-25
Thanks, "kate" allowed me to fix the problem.  Thanks everyone.  This also fixed the problem I was having with my sisters' card reader for her digital camera flash card(a storage media device as well).  

These forums are great and I look forward to using them again to either help myself or others.

---

### Post by palsyboy on 2005-12-25
"Killerweaksweet." -Eric Cartman

---

