---
title: "Ubuntu Ideal for Acer Mini?"
date: 2009-05-13
forum: General Help
---

### Post by JCPInney on 2009-05-13
I recent purchased an Acer mini for various reasons.  Primarily going to be used for school work and quick easy access to internet, I got Ubuntu 8.10 for it.  Right off the bat after partitioning my hard-drive and reformating with Ubuntu I encountered many issues.  Most likely solved by experiance with the OS, but regardless still annoying.  

I'm not new to the computer scene, but Ubunutu dumb-founded me!
Mabye its just the screen rez due to the size of the laptop, but the Next buttons for various windows dont fit on the screen, and when going to resize to fit properly, they cant get any smaller.

Also Is there not a wireless auto find feature?
I looked through the user manuel, as well as the comprehensive guide for Ubuntu and I could simply not figure out how to connect to the internet.  I'm currently in deployed overseas in Iraq, so wi-fi is the only means of internet.  The ISP requires you log in to acess the internet.

So I suppose my questions are:

How do I locate hotspots, because they have repeaters all over the base here that send out wi-fi, so how do I lock onto one withh Ubuntu.
How do I resize the windows?  or am I shafted because Ubuntu wasn't desighned for a mini?

Any help would be very appreciated!

---

### Post by prem1er on 2009-05-13
For your wireless problem.  What version of ubuntu are you using?  Is there a restricted wireless driver that needs to be enabled...Click on system > administration > restricted drivers.  Is the light for the wireless card lit up? Also, open up a terminal and post the results of this command.  

```
lspci
```

Also, thanks for your service.

---

### Post by mikewhatever on 2009-05-13
No, Ubuntu proper isn't right for netbooks. Use [UNR]("https://wiki.ubuntu.com/UNR") or derivatives such as EasyPeasy. Here is another useful link.
[https://help.ubuntu.com/community/AspireOne](https://help.ubuntu.com/community/AspireOne)

---

### Post by JCPInney on 2009-05-13
> **mikewhatever said:**
> No, Ubuntu proper isn't right for netbooks. Use [UNR]("https://wiki.ubuntu.com/UNR") or derivatives such as EasyPeasy. Here is another useful link.
[https://help.ubuntu.com/community/AspireOne](https://help.ubuntu.com/community/AspireOne)

Wow ok URN sounds nice in all, but im totally confused as to how to download and get it running.

Is it an entirely new OS?

If so how do I install it?
The steps listed are far to advanced for a newbie ubuntu user.

---

### Post by prem1er on 2009-05-13
It is a variation of Ubuntu created for systems with lower resources and small screen (netbooks).  You should download the image file [http://cdimage.ubuntu.com/ubuntu-netbook-remix/daily-live/current/]("http://cdimage.ubuntu.com/ubuntu-netbook-remix/daily-live/current/") and create a bootable usb with that image.  You can follow this tutorial in order to create the bootable usb.  [https://help.ubuntu.com/community/Installation/FromImgFiles](https://help.ubuntu.com/community/Installation/FromImgFiles).

---

### Post by mikewhatever on 2009-05-13
I think it's better to download a stable 9.04 image, then a daily testing.
Check out ubuntu.com for downloading links, and [https://wiki.ubuntu.com/UNR#Help%20and%20documentation](https://wiki.ubuntu.com/UNR#Help%20and%20documentation).
There is also another derivative [http://www.eeebuntu.org/](http://www.eeebuntu.org/).

---

### Post by JCPInney on 2009-05-16
Still having loads of issues with my Acer mini + Ubuntu 8.10.

I cant seem to get the wifi to activate for the life of me.
What are the steps to installing drivers for hardware on a laptop running Ubuntu?

Because the little orange signal LED doesnt even light up or anything, so im convinced the laptop doesnt even know there is a wireless adapter inside.

Questions:

How do I update drivers?
Does URN fix the sizing issues with using a Mini?  As it stands Ubuntu has a ton of sizing issues that cant be solved by resizing.

Thanks everyone!

---

