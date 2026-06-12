---
title: "Mounting a HD"
date: 2008-09-20
forum: Desktop Environments
---

### Post by Curtis_bob on 2008-09-20
ok i just installed my Ubuntu on this tower... my only problem is... i can't seem to mount one of my Hard drives.. it was formatted on a Windows Vista system. (i had it hooked up to it threw a USB connection to format it and take files off of that computer. then put it on here right before installing ubuntu on the other hard drive...) the error that Ubuntu gives me says i can force a mount... but i don't know how to do that.... can one help me??? lol i know very very little when it comes to this

---

### Post by marcthenarc on 2008-09-20
"Forcing a mount" means that your kernel will be forced to recognize your filesystem as the one you decide it is (typically by using the command 'mount -t <type> /dev/<fs> /mnt/<target>". Not a very good idea - for a newbie, in any case -: as Linux supports a large array of disk formats, if it didin't recognize it first hand, chances are your kernel doesn't support it yet.

On Ubuntu, there is support for NTFS (assuming the Vista drive was formatted this way).  Use the excellent ntfs-3g package for mounting your drive (and reading and writing too).  Once installed, you'll have a few tools on your menu to operate on it (or a simple mount will do, I believe.)

Good luck.

---

### Post by Curtis_bob on 2008-09-20
thank you... i will look for that... i know the hard rive is formatted in NTFS.. i made sure of it it was originally on my 2003 Windows server... and i never install stuff on a fat32 any more. lol.. unless i have to... i'm trying to completely get away from Windows so... i will post back with my findings

---

### Post by Curtis_bob on 2008-09-21
Got it.. thank you very much.... you guys rock

---

### Post by marcthenarc on 2008-09-21
Well I'm glad it worked. :)

---

