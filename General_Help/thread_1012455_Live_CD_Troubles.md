---
title: "Live CD Troubles"
date: 2008-12-15
forum: General Help
---

### Post by Seasonal Wealth on 2008-12-15
I can't seem to get the live CD to work, some help?

---

### Post by oilchangeguy on 2008-12-15
> **Seasonal Wealth said:**
> I can't seem to get the live CD to work, some help?

how about some computer specs, and the version of ubuntu you're using.

---

### Post by Seasonal Wealth on 2008-12-15
> **oilchangeguy said:**
> how about some computer specs, and the version of ubuntu you're using.

I have a Emachines T1840 running XP Home. Version 8.10 is what I'm trying to load.

---

### Post by drs305 on 2008-12-15
Does it start the install? Did you check the download integrity with md5sum and the iso burn? If you look at the CD with a file browser, can you see individual folders/files on the CD?  If you can start the CD, there is an option to check the integrity of the disk. Did you do this?

In addition to the specs requested by oilchangeguy, you will have to give us more detail on exactly what problems you are having.

Here are a couple of references:
[BurningIsoHowto]("https://help.ubuntu.com/community/BurningIsoHowto")

[http://www.psychocats.net/ubuntu/iso]("http://www.psychocats.net/ubuntu/iso")

---

### Post by eBoxNet on 2008-12-15
> **Seasonal Wealth said:**
> I can't seem to get the live CD to work, some help?


And what kind of prob do you have?
Can't boot at all or something else?

---

### Post by EdThaSlayer on 2008-12-15
Have you tried using multiple .iso files and burned them on different cds?
Sometimes there are problems with specific iso files. For ex: if you download from some American server that might not work but downloading from one in the Netherlands for examples works perfectly. Give more information as oilchangeguy said.

---

### Post by Seasonal Wealth on 2008-12-15
> **drs305 said:**
> Does it start the install? Did you check the download integrity with md5sum and the iso burn? If you look at the CD with a file browser, can you see individual folders/files on the CD?  If you can start the CD, there is an option to check the integrity of the disk. Did you do this?

In addition to the specs requested by oilchangeguy, you will have to give us more detail on exactly what problems you are having.

Here are a couple of references:
[BurningIsoHowto]("https://help.ubuntu.com/community/BurningIsoHowto")

[http://www.psychocats.net/ubuntu/iso]("http://www.psychocats.net/ubuntu/iso")

It loads a screen when I double click the cd drive in My Computer. But after I click the prompts, nothing happens.

> **EdThaSlayer said:**
> Have you tried using multiple .iso files and burned them on different cds?
Sometimes there are problems with specific iso files. For ex: if you download from some American server that might not work but downloading from one in the Netherlands for examples works perfectly. Give more information as oilchangeguy said.

I got the version from shipit(or something called similar).

---

### Post by drs305 on 2008-12-15
> **Seasonal Wealth said:**
> It loads a screen when I double click the cd drive in My Computer. But after I click the prompts, nothing happens.

Make sure your computer's BIOS is set to boot first from CD, then insert the CD and restart your computer. The ubuntu CD is meant to be run from the initial boot, not from within Windows. (By the way, you aren't trying to install wubi are you?)

---

### Post by Seasonal Wealth on 2008-12-15
> **drs305 said:**
> Make sure your computer's BIOS is set to boot first from CD, then insert the CD and restart your computer. The ubuntu CD is meant to be run from the initial boot, not from within Windows. (By the way, you aren't trying to install wubi are you?)

First I click "Demo and Full Installation, then I select "I want to manually reboot later". After that I close all my programs, and folders, and restart. Ubuntu never loads, it goes to windows.

---

### Post by oilchangeguy on 2008-12-15
> **Seasonal Wealth said:**
> I have a Emachines T1840 running XP Home. Version 8.10 is what I'm trying to load.

that's not computer specs. cpu speed, amount of ram, and hard drive size.

---

### Post by Seasonal Wealth on 2008-12-15
> **oilchangeguy said:**
> that's not computer specs. cpu speed, amount of ram, and hard drive size.

1.80GHz, 512mb ram, 40GB

---

### Post by Seasonal Wealth on 2008-12-15
Bump

---

### Post by Seasonal Wealth on 2008-12-15
Bump

---

### Post by Seasonal Wealth on 2008-12-16
Bump.

---

### Post by drs305 on 2008-12-16
If you read through the links I provided and are still having no success I'd recommend trying the Alternate CD. You can download it by starting at this link and going to the Alternate CD section:
[http://releases.ubuntu.com/releases/intrepid/]("http://releases.ubuntu.com/releases/intrepid/")

---

### Post by Seasonal Wealth on 2008-12-16
Is there a way to order the alternate cd? I have dial-up.

---

### Post by Seasonal Wealth on 2008-12-16
Bump

---

### Post by oilchangeguy on 2008-12-16
> **Seasonal Wealth said:**
> Is there a way to order the alternate cd? I have dial-up.

if you'll do your own research, instead of waiting for someone to hold your hand, and spoon feed you the answers. you might find the answers more quickly. if you'd take the time to look at the [www.ubuntu.com](www.ubuntu.com) site, you'll note there is no option to order the alternate cd. doing your own research instead of bumping the thread will help you learn about ubuntu alot faster.

---

### Post by .arean on 2008-12-18
It sounds like boot from CD-ROM is not enabled in your BIOS. To enable it you need to restart your computer and at the POST screen (the first screen you see when you turn on your computer, there might be an emachines logo displayed over the POST screen, that's fine) and press the key to enter the BIOS. Which key it is varies from motherboard to motherboard but it's probably one of the following: del, esc, one of the F keys, or maybe the home button. If you still have the manual for your computer it you might be able to find out what key it is in there. Once inside navigate to the boot section and change the boot order to something like CD-ROM, Floppy, or any order where your CD-ROM is set to boot before your HDD. Now you should be able to boot from the Ubuntu CD.

---

