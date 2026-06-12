---
title: "How to get old an Dell with an ATI card to output S-video to tv/use an extra monitor"
date: 2008-10-27
forum: Dell Ubuntu Support (CLOSED)
---

### Post by nokrater on 2008-10-27
This post is for any of you who have an old dell with an ATI card to output through the S-video or VGA port or whatever for a second monitor.  My story was that I wanted to get an old 600m laptop to be able to output to a T.V. so that you know the context...


Basically, when it comes to these old computers, the most important thing to know is the type of graphics card you have and the specifications.  

To find what kind of graphics card you have, open a terminal and type the command "lspci."

Now in my case, I dealt with an ATI Radeon 9000.  If you happen to have a non-Radeon card, the general idea is the same: you have to find the drivers and then setup the xorg.conf file as I'll describe below.  But I'll stick to the case of the ATI Radeon here.


The next most important piece of information for people with ATI Radeon cards is the card's model number.  This is important because both Ubuntu and ATI changed their driver package with the Radeon 9500 series.  See these links:

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

If you have a card that is 9500 or newer, you will want to use the fglrx driver and follow the directions as explained in the FIRST link.

If you have a card that is older than 9500, you will want to use the Radeon driver which is bundled into an ATI driver package.  In this case you will want to follow the instructions on the SECOND link.  

Both of these links go into the details of how to modify the xorg.conf file so as to get what is called "dual-head" working, i.e. video output to two monitors.

I would also recommending looking at the man pages for xorg.conf as they are useful in describing the organization of that file.

---

### Post by RGPerson on 2009-02-13
Will this work with a Diamond Radeon 4550 HD?  We'd really like to use the DVI to HDMI to connect it to our HD TV.

I'm a Windows tech (certified by MS) but fairly new to Linux.  When we did the lspci command we got 

01:00.0 VGA compatible controller [0300]: ATI Technologies Inc. Unknown device [1002:9540]

Thanks

Gabrielle

---

