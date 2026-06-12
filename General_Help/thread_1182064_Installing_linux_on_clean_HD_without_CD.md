---
title: "Installing linux on clean HD without CD"
date: 2009-06-08
forum: General Help
---

### Post by Battletoads on 2009-06-08
I have wanted to switch from an XP user to a Linux user for some time now.  Basically I would like to have a fresh start on my computer and completely wipe my hard drive.  What I was planning on doing was taking out my hard drive placing it in an external hard drive enclosure and hooking it up to my desktop and directly implementing the os start up file in the hard drive.  I do not meen the OS by this, i meen the information that would normally be on the CD.  I am not positive this will work because I don't know if it would set up my bios.  Could someone please tell me if this is possible or an alternate way to approach this and have the same effect without the CD (The effect being to have a clean hard drive and installing linux on it).  Thank you.

---

### Post by maheshasolkar on 2009-06-08
I am not sure why you don't want to use the installation CD on the computer you want to start afresh on. If you install from the CD, it does give you an option to completely wipe out the hard disk and install Ubuntu on it.

Another option is to use USB drive to install, but your BIOS must support this.

---

### Post by DeMus on 2009-06-08
> **Battletoads said:**
> I have wanted to switch from an XP user to a Linux user for some time now.  Basically I would like to have a fresh start on my computer and completely wipe my hard drive.  What I was planning on doing was taking out my hard drive placing it in an external hard drive enclosure and hooking it up to my desktop and directly implementing the os start up file in the hard drive.  I do not meen the OS by this, i meen the information that would normally be on the CD.  I am not positive this will work because I don't know if it would set up my bios.  Could someone please tell me if this is possible or an alternate way to approach this and have the same effect without the CD (The effect being to have a clean hard drive and installing linux on it).  Thank you.

Well, installing Ubuntu on a clean hard disk is a good idea. It will make sure you won't have any left-overs from other installations which could interfere.
If I understand you correctly you want to have a copy of a CD on your old, and now external, hard disk, boot from it and install the OS onto your new hard disk? Is this what you want?
If so, it should be possible, IF your BIOS let's you boot from a USB port. Newer computer should be able to do so.

The installation files should be in the main directory of your external disk, just the way they normally are on the CD.

Question: why? Why not install from a CD?

---

### Post by Therion on 2009-06-08
Installing from the CD would be the simple solution here.  Just select the "Install - Use entire disk" option.  

Since your *entire* drive will then be formatted for a new file-system (Ext3 or 4 primarily) it accomplishes exactly what you want without all the extra steps.

---

### Post by Einsamkeit on 2009-06-08
You could always check out *unetbootin*, lets you install directly from the internet instead of having external support of any kind. Worked well on my desktop computer.

---

### Post by Battletoads on 2009-06-08
I don't plan on using the CD because of time.  I don't feel like waiting for weeks for the disk, or paying for it when there's a free alternative.

---

### Post by torgrot on 2009-06-08
Why don't you just down load it and burn the CD, I am sure that is what almost everyone here has done at one point.  The download is free and if you already have the image, why not just burn the CD?  I am so confused.
 
torgrot

---

### Post by Battletoads on 2009-06-08
> **torgrot said:**
> Why don't you just down load it and burn the CD, I am sure that is what almost everyone here has done at one point.  The download is free and if you already have the image, why not just burn the CD?  I am so confused.
 
torgrot

How would I go about burning an OS?  Would it require for me to have a DVD burner or could I do it with a run-of-the-mill cd burner?  Thanks.

---

### Post by Vaphell on 2009-06-08
hm, can't you download ubuntu iso file from the internet (1hr), burn it to a cd and proceed with normal installation?

ubuntu iso fits on CD (700MB), CD writer is enough

---

### Post by DeMus on 2009-06-08
> **Battletoads said:**
> How would I go about burning an OS?  Would it require for me to have a DVD burner or could I do it with a run-of-the-mill cd burner?  Thanks.

The installation files fit on a cd, so that's all you need: a cd burner and of course a program to do the work.
What are you using now? Windows or do you use some kind of Linux already?

---

### Post by Einsamkeit on 2009-06-08
> **Battletoads said:**
> I don't plan on using the CD because of time.  I don't feel like waiting for weeks for the disk, or paying for it when there's a free alternative.

*after a little research*

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

By selecting "Hard Drive" rather than "USB drive", it allows you to boot with unetbootin, who then downloads what it needs to install the distro you selected (May it be Ubuntu, OpenSuSe, etc).
For the Clean HDD aspect, well during the install process just dump the partition table and redo it entirely, it'll format everything, leaving you with a clean HDD for the installation to continue on.

;)

And it doesn't take much long to do the whole thing.

---

### Post by Battletoads on 2009-06-08
> **DeMus said:**
> The installation files fit on a cd, so that's all you need: a cd burner and of course a program to do the work.
What are you using now? Windows or do you use some kind of Linux already?

Windows XP professional.

---

### Post by torgrot on 2009-06-08
The iso is a CD-Image file, under windows you can use infrarecorder, Roxio, Nero, or any CD burning software and just burn the iso image to the CD.  You can then boot from that, and then install.
 
You only need a DVD burner if you downloaded the DVD iso.  You can tell because it says DVD in the filename somewhere like this ubuntu-8.04.1-dvd-i386.iso.  
 
torgrot

---

### Post by maheshasolkar on 2009-06-08
> **Battletoads said:**
> How would I go about burning an OS?  Would it require for me to have a DVD burner or could I do it with a run-of-the-mill cd burner?  Thanks.

You can always order one free from [https://shipit.ubuntu.com/](https://shipit.ubuntu.com/). It will take about 2 weeks to deliver though - But you get nice Ubuntu stickers with it :)

---

### Post by Iusedtowearatie on 2009-06-08
If you don't have a burner software that allows you to burn iso:s, this one is free, available for XP and will do the job:
[http://www.cdburnerxp.se/?lang=en](http://www.cdburnerxp.se/?lang=en)

---

