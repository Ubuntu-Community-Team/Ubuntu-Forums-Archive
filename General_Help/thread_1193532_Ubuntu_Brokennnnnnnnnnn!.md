---
title: "Ubuntu Brokennnnnnnnnnn!"
date: 2009-06-21
forum: General Help
---

### Post by Spaceman7o on 2009-06-21
Yes thats right broken... after getting the wrong advice from someone about my boot menu. Ive accidently set my ubuntu to boot using windows vista/longhorn WTF!!! now i know this person never meant this but i aint bothered right now all i want is too fix it and all i have access too is windows vista please someone help!

---

### Post by howefield on 2009-06-21
> **Spaceman7o said:**
> Yes thats right broken... after getting the wrong advice from someone about my boot menu. Ive accidently set my ubuntu to boot using windows vista/longhorn WTF!!! now i know this person never meant this but i aint bothered right now all i want is too fix it and all i have access too is windows vista please someone help!

So is Ubuntu booting ?

Do you mean windows is broken ?

Just what do you mean ?

---

### Post by TeoBigusGeekus on 2009-06-21
From what I can understand it's a grub restoration problem:
[http://maketecheasier.com/how-to-restore-grub-in-ubuntu/2008/04/11]("http://maketecheasier.com/how-to-restore-grub-in-ubuntu/2008/04/11")

---

### Post by Spaceman7o on 2009-06-21
Ok right i cant access my ubuntu because its trying to boot using the windows vista/longhorn booter. all i can do right now is access my windows vista. This happened when i set the default booter to Windows Vista/Longhorn after getting the wrong advice.

---

### Post by kndlewis on 2009-06-21
You need a supergrub boot disk
[http://members.iinet.net.au/~herman546/SuperGrubDiskPage.html]("http://members.iinet.net.au/%7Eherman546/SuperGrubDiskPage.html")
This saved me once already.

---

### Post by Spaceman7o on 2009-06-21
can i use this from vista? and what do i do exactly? and i use Wubi installer does this make a difference?

---

### Post by paperplate9 on 2009-06-21
> **Spaceman7o said:**
> Ok right i cant access my ubuntu because its trying to boot using the windows vista/longhorn booter. all i can do right now is access my windows vista. This happened when i set the default booter to Windows Vista/Longhorn after getting the wrong advice.

I assume you're referring to [this](http://ubuntuforums.org/showthread.php?t=1193494) thread where I and someone else just told you to change your "default". You must've set "timeout" to 0.

---

### Post by merlinus on 2009-06-21
If you can boot from the live cd, open a terminal and post results of:

```

sudo fdisk -l

```This will show your partitions.  Then you can reinstall grub and boot ubuntu.

But first try pressing the Esc key right after booting to see if the grub menu shows up.

---

### Post by Spaceman7o on 2009-06-21
> **paperplate9 said:**
> I assume you're referring to [this]("http://ubuntuforums.org/showthread.php?t=1193494") thread where I and someone else just told you to change your "default". You must've set "timeout" to 0.
yes but i did not set timeout to 0 i set default boot loader to windows vista/longhorn

---

### Post by Spaceman7o on 2009-06-21
> **merlinus said:**
> If you can boot from the live cd, open a terminal and post results of:

```

sudo fdisk -l

```This will show your partitions.  Then you can reinstall grub and boot ubuntu.

But first try pressing the Esc key right after booting to see if the grub menu shows up.

i cant even access ubuntu how an i type the command into the terminal?

---

### Post by JordyD on 2009-06-21
> **Spaceman7o said:**
> i cant even access ubuntu how an i type the command into the terminal?

Live CD.

EDIT: You can download a live CD from ubuntu.com, just pop it in and restart, then choose "Try Ubuntu without any change to my computer", then you can use that command he mentioned.

---

### Post by paperplate9 on 2009-06-21
Under windows, install fs-driver : [www.fs-driver.org](www.fs-driver.org)

This will allow you to read/write to your ext2 (linux) partitions.

Locate your boot partition and post the contents of your boot/grub/menu.lst.

---

### Post by Spaceman7o on 2009-06-21
ok it dont matter then im gona uninstall wubi and partition my drive for real can someone help me by posting a link on instructions how to partition my drive and load ubuntu? thanks

---

### Post by merlinus on 2009-06-21
[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)

---

### Post by RobOrr on 2009-06-21
Hi Spaceman, go to the ubuntu website and grab a copy of the Ubuntu Live Desktop CD.

It's the primary method of installing Ubuntu and is massively useful for fixing ubuntu if you manage to wreck it (i've needed it once or twice). 

This disc will allow you to run Ubuntu purely off of it with nothing installed on the harddrive, as well as install everything properly AND partition your drive for you, as you mentioned you were planning on doing. The instructions on the CD are very straightforward, your windows partition can be left alone and the ubuntu website and forums will have all the info you need if you run into any problems.

My final piece of advice, and one that I've found invaluable, is to search around forums and use google if you run into a problem, as it seems that almost all the problems you get, someone will have had before and an answer will have been provided. This saves you waiting around for people to post on your thread ;)

---

