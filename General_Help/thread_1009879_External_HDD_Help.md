---
title: "External HDD Help"
date: 2008-12-13
forum: General Help
---

### Post by Dj DeathCool on 2008-12-13
Hello, I'm a new Ubuntu user (sorry in advance for the ignorance). I just recently became comfortable enough with Ubuntu to completely ditch Windows and jump into the Linux community. 

The problem that I'm experiencing right now is that when I plug in my external hard drive I get what appears to be the standard improperly unmounted error message. The error tells me to either use Windows to properly disconnect or do a force mount through the terminal. When I tried doing a force mount the terminal simply acts as if I typed the typical "mount" command. One time I misspelled the name of my HDD and the force command went through but gave me a "media not present" error. 

So I just want to know why I can't do a force mount, and if there's anything else I can do to get this baby working again short of pirating, installing and using Windows to "properly unmount" my drive. Thanks in advance for any help!

---

### Post by nielz on 2008-12-13
Try mounting the hard drive read only (mount -o ro) that way you can at least access the data on it.

---

### Post by scouser73 on 2008-12-13
When your HDD was last plugged into a Windows PC, did you use the **Safely Remove Hardware** function?, this is located in the bottom right-hand of the screen on Windows.  If you haven't, plug it back into a Windows PC and then use the **Safely Remove Hardware** function. Your HDD should then operate as normal.

---

### Post by vanadium on 2008-12-13
As previous replies indicated, the best option is to connect to a Windows system, then disconnect properly.

As you indicate you do not anymore use Windows, I recommend you to reformat the external drive to ext3. ext3 is a native linux file system, that you can maintain using linux. You should be using ntfs only if you have ready access to a Windows machine.

I have my external drives formatted in ext3 (which if the need arises can still be read after installing an ext2 driver in Windows). I keep small USB sticks in fat32 for compatibility.

---

