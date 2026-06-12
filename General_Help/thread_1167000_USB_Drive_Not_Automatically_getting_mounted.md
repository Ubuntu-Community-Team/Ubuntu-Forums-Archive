---
title: "USB Drive Not Automatically getting mounted"
date: 2009-05-22
forum: General Help
---

### Post by StOlEnDeStInY on 2009-05-22
Hello!

I have been using Ubuntu since the last 2 years and I have been saved from every trouble that I have ever faced by the fantastic forum support that you guys provide. Kudos to that!!

I had previously installed Ubuntu 8.10 but was fascinated by the Ultimate Hardy version so last night itself I installed the Ultimate Edition. I configured my fstab file to show my ntfs partition automatically again using your forums but when I put in my Kingston 4 GB pendrive, it said it can't mount it (See Attachment).  I browsed through the forums. I rebooted in Windows and mounted the pendrive, it mounted perfectly. Copied one or two files and then unmounted it. Came back to Ubuntu and the problem remained.


Forced mount through terminal does work though, but I want to see the plug and show instantaneous icon being shown in the desktop to return. It had no problems in 8.10


I tried to put an entry in the fstab too 
/dev/sdb1
UUID=4A16-A32C /media/USB ntfs-3g defaults,umask=007,gid=46 0 1

But even that didnt help. Now what?

P.S. I had even formatted the drive to both ntfs and fat32 format using gparted, just to make see if that would make a differece. It didn't.

---

### Post by StOlEnDeStInY on 2009-05-22
Bumping the topic! Help will be really appreciated :)

---

### Post by StOlEnDeStInY on 2009-05-22
Sorry to bump the topic again but does it always take so long? I am sorry if am being too impatient and I understand the fact that the questions are answered by people in their free time and that too for absolutely free..

---

### Post by StOlEnDeStInY on 2009-05-23
Do guys who answer go as back as the fifth page to answer a query? If anyone can answer that in affirmative, I wont bump for next 24 hours now :D

---

### Post by StOlEnDeStInY on 2009-05-23
Bump!

---

### Post by StOlEnDeStInY on 2009-05-24
I insist! Please someone help me!! Its been driving me crazy and I have been looking at this page for the past two days in some hope but no replies till now! :(

---

### Post by StOlEnDeStInY on 2009-05-25
I love Ubuntu I really do. I have been trying to get my seniors at the office shiftover to Ubuntu for all the 150 systems from Windows telling them that most of the questions are already answered on the forum and others can be asked and should be answered in a day or two. I know its all volunteering by the community guys but wished someone would give atleast some way forward. Its almost embarrassing that all the replies are mine. Is my question that hard? Or have I given too lil information?

---

### Post by Soul-Sing on 2009-05-25
example:

```
UUID=7685e1f4-edb5-4188-b452-3bd9c8cb115b    /media/500GBDisk    ext3 relatime,user,noauto   0    0
```

basic:

```
sudo mount -t ext3 /dev/sdb /media/usbstick -o relatime,user
```

(in this example usb:ext3)

---

### Post by fballem on 2009-05-25
I have two suggestions:

[LIST=1]
[*]I don't know what gets installed in the Ultimate edition. If you can open Synaptic and do a search for ntfs, this should give you a list of the ntfs programs. Please check that ntfsprogs is installed. If it is not, please install it - it will also pick up the dependencies. Once you have installed this, please restart your system.
[*]I know that this is going to sound counter-intuitive, but have you tried removing the line in /etc/fstab? The reason I ask is that I do not have the line for either of my two usb drives, and both just mount correctly.
[/LIST]

Hope this helps,

---

### Post by StOlEnDeStInY on 2009-05-25
> **leoquant said:**
> example:

```
UUID=7685e1f4-edb5-4188-b452-3bd9c8cb115b    /media/500GBDisk    ext3 relatime,user,noauto   0    0
```basic:

```
sudo mount -t ext3 /dev/sdb /media/usbstick -o relatime,user
```(in this example usb:ext3)

Forced mount through terminal is working without any glitch. Of course unmounting also then needs to be done through the terminal. But I needed an automated mounting as it use to occur previously.

> 
[LIST=1]
[*]I don't know what gets installed in the Ultimate edition. If you can open Synaptic and do a search for ntfs, this should give you a list of the ntfs programs. Please check that ntfsprogs is installed. If it is not, please install it - it will also pick up the dependencies. Once you have installed this, please restart your system.
[*]I know that this is going to sound counter-intuitive, but have you tried removing the line in /etc/fstab? The reason I ask is that I do not have the line for either of my two usb drives, and both just mount correctly.
[/LIST]


1. ntfsprogs is installed (I forgot to mention that I did check that)
2. Initially the line wasn't present. I added the line for some solution but it didn't work either way.

---

### Post by StOlEnDeStInY on 2009-05-28
I found the reply after I posted this topic on the forums of Ultimate Edition. I had to go to NTFS configuration tools and allow read/write from there. DUH!

---

### Post by cb951303 on 2009-05-28
If you need to place a line to fstab to mount your USB stick then there is something wrong with the system.

---

