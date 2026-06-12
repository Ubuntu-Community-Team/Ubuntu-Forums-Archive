---
title: "floppy"
date: 2006-08-25
forum: Desktop Environments
---

### Post by Aualin on 2006-08-25
How do i install grub on a floppy?

---

### Post by Ramses de Norre on 2006-08-25
Check [this]("http://www.gnu.org/software/grub/manual/html_node/Creating-a-GRUB-boot-floppy.html#Creating-a-GRUB-boot-floppy").

---

### Post by Aualin on 2006-08-25
The directory doesnt exist!

---

### Post by Ramses de Norre on 2006-08-25
I think the stage1 and stage2 files in /usr/lib/grub/i386-pc/ are the same as those in /boot/grub/ so try those. You must have grub installed, there seems to be no other way to install grub to a floppy than first installing it to a hd..

---

### Post by anaconda on 2006-08-25
I have installed grub to a floppy from a disk-image, which I downloaded from grub:s homepages..?? or somewhere.. it was couple of months ago. Can't remember exactly.

---

### Post by jimbob on 2006-08-25
Much easier to use this command:

#grub-floppy /dev/fd0

Check in out in the man pages ...
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by Aualin on 2006-09-04
and how do i unmount the drive?

---

### Post by jimbob on 2006-09-04
sudo umount /dev/fd0

---

### Post by Aualin on 2006-09-04
that doesnt work...
it says that the command unmount couldnt be found...

---

### Post by jimbob on 2006-09-04
Look at what I wrote.

It's umount not unmount.

---

### Post by Aualin on 2006-09-04
u like in ubuntu:p 
but now it says
Cannot create link /etc/mtab~
Perhaps there is a stale lock file?

---

### Post by jimbob on 2006-09-04
Close all other windows and GUI's that may have the floppy assigned.

The umount will not work if some other process is using the floppy.

---

### Post by Aualin on 2006-09-04
ok, ill try

---

### Post by AT-AT on 2006-09-28
I have a question about this too. First let me state that for some reason I could not install GRUB on my computer, so I had to install Lilo instead. I set up a dual boot scheme, but LILO doesnt want to boot my old windows program (98). The files I need to put on a floppy should be on the install disk, so I can search the disk for the appropriate files using Ubuntu, no? If so, are the files 'stage1' and 'stage2' all I need to put on a floppy?

---

### Post by jimbob on 2006-09-28
On a system with grub installed as the boot loader these files are in /boot/grub.

In your case that directory may not exist since you are using LILO.

However you can find them at /lib/grub/i386-pc when Ubuntu is up and running.

Search the forums for 'grub-install'.  You'll find a bunch of how-tos.
&#65279;________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

