---
title: "Is someone working on the Firefox / Flash Problem?"
date: 2008-12-06
forum: General Help
---

### Post by jakobtritten on 2008-12-06
Dear Ubuntu Community,

It seems like a rather common problem that flash non-free 10 is causing a lot of problems in Firefox 3.0.  [B]Is there some amazing person out there who is working on this or holds the answer to this problem? [-o<

[/B]I have spent the past month trying to convince my mom and brother that Linux (Ubuntu, at the moment) is tremendously better than any windoze OS.  They're not convinced.  ](*,)

Due to this recent issue with flash, Firefox is running like an old rusty steamroller with a bad fuel pump.  (Forgive the lame analogy; but you get the picture, don't you?)  

By reading through the forums, i know i'm not the only one dealing with this.  I've parsed through UbuntuForums for an answer, but to no avail.  I read one thread and found a hopeful temporary fix. \\:D/...

[http://ubuntuforums.org/showthread.php?t=856291&highlight=latest+flash-nonfree+update](http://ubuntuforums.org/showthread.php?t=856291&highlight=latest+flash-nonfree+update)

The following is supposed to fetch flash non-free 9 so we can revert back to it.  

> wget [http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz)
The problem is that it only fetches this ...
> 
--14:56:38--  [http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz)
           => `install_flash_player_9_linux.tar.gz'
Resolving fpdownload.macromedia.com... 69.192.2.70
Connecting to fpdownload.macromedia.com|69.192.2.70|:80... 
connected.
HTTP request sent, awaiting response... 404 Not Found
14:56:38 ERROR 404: Not Found.   :-(

It appears that it worked for some people, but i suppose the link is dead now.  **Any insight on this?  Or is there another place to download the package "install_flash_player_9_linux.tar.gz"?  **

We owe many thanks to those of you who have the knowledge and the patience to solve these kinds of frustrating issues.  =D>  Thank you *very* much for your time and efforts!

jakob

P.S.  My system is a Dell Inspiron 5100 cinder block.  It contains a blazing Intel(R) Pentium(R) 4 running at 2.4GHz with a whoppin' 376.3 MB of RAM.  I'm running 8.04.  My mom's computer is a Dell Dimension 4100 with 502 MB RAM with a 900MHz (?) processor.  I put 8.10 on hers.  Both of our Firefox browsers are having similar symptoms (i.e., freezing, lagging, and just not working).

---

### Post by mhh91 on 2008-12-06
what is wrong with version 10 of the flash player??


it's running OK on my computer

---

### Post by kostkon on 2008-12-06
> **jakobtritten said:**
> Dear Ubuntu Community,

It seems like a rather common problem that flash non-free 10 is causing a lot of problems in Firefox 3.0.  [B]Is there some amazing person out there who is working on this or holds the answer to this problem? [-o<

[/B]I have spent the past month trying to convince my mom and brother that Linux (Ubuntu, at the moment) is tremendously better than any windoze OS.  They're not convinced.  ](*,)

Due to this recent issue with flash, Firefox is running like an old rusty steamroller with a bad fuel pump.  (Forgive the lame analogy; but you get the picture, don't you?)  

By reading through the forums, i know i'm not the only one dealing with this.  I've parsed through UbuntuForums for an answer, but to no avail.  I read one thread and found a hopeful temporary fix. \\:D/...

[http://ubuntuforums.org/showthread.php?t=856291&highlight=latest+flash-nonfree+update](http://ubuntuforums.org/showthread.php?t=856291&highlight=latest+flash-nonfree+update)

The following is supposed to fetch flash non-free 9 so we can revert back to it.  

The problem is that it only fetches this ...
   :-(

It appears that it worked for some people, but i suppose the link is dead now.  **Any insight on this?  Or is there another place to download the package "install_flash_player_9_linux.tar.gz"?  **

We owe many thanks to those of you who have the knowledge and the patience to solve these kinds of frustrating issues.  =D>  Thank you *very* much for your time and efforts!

jakob

P.S.  My system is a Dell Inspiron 5100 cinder block.  It contains a blazing Intel(R) Pentium(R) 4 running at 2.4GHz with a whoppin' 376.3 MB of RAM.  I'm running 8.04.  My mom's computer is a Dell Dimension 4100 with 502 MB RAM with a 900MHz (?) processor.  I put 8.10 on hers.  Both of our Firefox browsers are having similar symptoms (i.e., freezing, lagging, and just not working).
What problems exactly do you have with Flash 10?

How did you install Flash 10?

It works OK here btw.

---

### Post by danwood76 on 2008-12-06
Most of the problems are caused when using the 64 bit version of ubuntu.
This is because up until now flash was unable to run on 64 bit and so has to be loaded in a 32 bit wrapper.

A new alpha version of flash has been released by adobe and works flawlessly under 64 bit.
Ive had no issues since I started using it.
[http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

---

### Post by spcwingo on 2008-12-06
If all you're looking for is flash player 9...well, that's an easy one:

[http://fpdownload.macromedia.com/get/flashplayer/installers/archive/fp9_archive.zip](http://fpdownload.macromedia.com/get/flashplayer/installers/archive/fp9_archive.zip)

Enjoy!

---

### Post by danwood76 on 2008-12-06
Flash player 9 is not good and a lot worse than 10!

---

### Post by toejamfootball on 2009-03-18
Try setting "Visual Effects" to none in Appearence Preferences.

I have on-board graphics and this solved the lagging when on pages with Flash.

---

### Post by jakobtritten on 2009-03-18
Many thanks to all of you who replied to this thread i started way back when.  For some reason, i didn't realize i was getting responses to it; that's why i haven't interacted.  My sincere apologies for inadvertently being a jerk.  

I somehow succeeded in getting Flash functioning properly with Firefox on my laptop ... which is now running 8.10 ... but i wasn't able to get it running on the same Ubuntu release on my mom's computer.  She caved and purchased a copy of windoze.  :-?

As i recall, the problems i was having were things like no audio with Flash, or Flash wouldn't play, or Flash apps would run as if i were executing 32-bit programs on an old 8088 or 286 machine (e.g., jumpy and painstakingly slow).

We weren't able to use any of those Flash-based websites online, like Homestarrunner.com, ElfYourself.com, and other stuff like that ... stuff that my mom would like to use without all of those problems and glitches.  

As far as how i fixed the problem, i honestly think i just kept uninstalling and reinstalling Firefox and Flash through Synaptic until the two programs finally seemed to work together.  No science to it, that i could find ... which i hate.  I like to know how things work so i can repeat the process if needed.  

Okay.  Shutting up.  Thanks again everyone!

jakob

---

### Post by a fenderson on 2009-03-18
You can also download and install the flash player .deb directly from adobe.

---

### Post by Zorael on 2009-03-18
It would help if Adobe would open up Flash so the community could help work out its kinks. But, yeah.

Flash 10 seems to work okay for me, but with an obvious difference in performance compared to when running it in Windows. I'm running a 32-bit installation on my netbook and a 64-bit on my bigger laptop, and while it technically "works" in a 64-bit environment, it could certainly use improvements.

---

### Post by jakobtritten on 2009-03-19
Thank you for your input, a fenderson and Zorael.  I appreciate that folks are still offering insight and opinions on this matter.

---

