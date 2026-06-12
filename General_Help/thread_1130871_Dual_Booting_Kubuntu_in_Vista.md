---
title: "Dual Booting Kubuntu in Vista"
date: 2009-04-20
forum: General Help
---

### Post by teamsupreme on 2009-04-20
Hey. I own an Acer Aspire 5520 Laptop,and I was wondering how to dual boot Kubuntu in Vista without having to uninstall Vista. Thanks!

---

### Post by kiridude on 2009-04-20
Do you want to run it inside Windows, or install it on a separate partition with an option to boot into vista or into Linux?

---

### Post by teamsupreme on 2009-04-20
Well, I want them to be separate, meaning choosing each partition...I think.

EDIT: I have Vista currently installed.

---

### Post by kiridude on 2009-04-20
Ok, 
- download the ISO image and burn a cd of Kubuntu (or Ubuntu).
- restart your computer and it should boot straight into the new OS. (If it doesn't, you will need to modify the boot order in the bios).
- Then just follow the instructions until you get to the partition stage. Here you will have the option of creating a separate partition for the new OS without affecting Vista.

From then on, when you restart your computer, you will be able to boot into Vista or Linux as you wish.

NOTE: Although you most probably will have no problems, back up any important data before this procedure. All partitioning programs recommend a backup - just in case.

---

### Post by teamsupreme on 2009-04-20
Well...I have an empty internal HDD. Can I use that as my partition?

---

### Post by kiridude on 2009-04-20
If you install it on another disk, that would not be a partition as you would use the whole disk (unless you wanted to partition it for other reasons). In this case you should have no problems, but do not disconnect the disk with Vista as Ubuntu should recognise it and grub should list it as an option at startup.

(I say Ubuntu as that is what I use, but it is basically the same as Kubuntu.)

---

### Post by teamsupreme on 2009-04-20
Okay...so that means I have to partition the drive? Also, using Kubuntu, am I able to access the programs from Windows (C Drive) using Wine?

---

### Post by bladeswords on 2009-04-20
Yes, you will have to have the drive partitioned.  Also you will be able to use wine to run *most* programs from your windows partition.

---

### Post by teamsupreme on 2009-04-20
Awesome. Will the partitioning take place during Kubuntu's installation?

---

### Post by bladeswords on 2009-04-20
Sure will.  If that is the device that you are installing to.  Just make sure you get the right drive!

---

### Post by teamsupreme on 2009-04-20
Okay...I'm gonna do it right now...I'm using the D Drive.

EDIT: Okay...it's not booting...now what do I do?

Alright...I got it to install...but I just realized that I prefer Ubuntu...so how do I uninstall this?

---

### Post by bladeswords on 2009-04-20
Just chuck ubuntu in and boot up, then install over the partition where you installed kubuntu.  Or you could just install ubuntu from kubuntu just run "sudo aptitude install ubuntu-desktop" from a terminal if you don't mind a bit of a download.

---

