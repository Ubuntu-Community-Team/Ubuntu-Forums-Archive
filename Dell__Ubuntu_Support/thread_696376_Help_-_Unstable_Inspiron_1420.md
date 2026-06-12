---
title: "Help - Unstable Inspiron 1420"
date: 2008-02-13
forum: Dell  Ubuntu Support
---

### Post by Acapulco on 2008-02-13
Hello. I recently bought a Dell Inspiron 1420 with a Core 2 Duo T7500. Unfortunately there was no choice but to order it with Vista, so I dual boot Vista Business and Ubuntu 7.10.

Everything was working like a charm and suddenly I started having this issues with hibernate and suspend, which I realized it's a common problem after reading the forums.

HOWEVER, since yesterday my machine has been behaving very weird. Specially after installing ClamAV to check my Windows partition, out of nothing the wireless kind of drops out and freezes while trying to reconnect. Even if I startup the connection manually by clicking the icon and then "Connect to other..." it won't respond.

The bad thing is, while the current windows seem to work (Firefox, terminal, etc), if I try to open a new terminal window it stays some time at "Starting Terminal..." but then it closes. Any new program will behave like so. 

I can't even poweroff or reboot the system in a normal way. The top-right red poweroff button won't do anything so I have to switch to tty1, and do "sudo poweroff now" or "sudo reboot now".

AFTER that, it freezes again at wich point I do the dreaded windows-technique of ctrl-alt-del which seems to bring down the system nicely. I get the Ubuntu logo and progress bar which after finishing stays there frozen again, empty but doing nothing. I then have to either poweroff (just push the button, not the 5-second one) or ctrl-alt-del again to reboot immediatly.

After booting up everything seems fine. 

What can I do? should I go back to 7.04?

I need help please, I am trying to work on my theses : /

Thanks a lot! :)

---

### Post by natehall on 2008-02-14
[Here ]("http://ubuntuforums.org/showthread.php?t=587576")is a thread that might help on the wireless problem. My power shutdown worked fine until I went and tried to change things. Logging in as a different user and leaving the power settings alone is one workaround.

---

### Post by carnagex420x on 2008-02-14
i bought a 1420 with Vista on it too. However i was quick to delete it and dual boot XP and Gutsy with no problems. When i first go it, Gutsy was only a beta and i had lots of problems but its pretty seamless now. Do yourself and your laptop a favor and delete Vista. lol

---

### Post by Acapulco on 2008-02-14
> **carnagex420x said:**
> i bought a 1420 with Vista on it too. However i was quick to delete it and dual boot XP and Gutsy with no problems. When i first go it, Gutsy was only a beta and i had lots of problems but its pretty seamless now. Do yourself and your laptop a favor and delete Vista. lol

Hey, I bought a WindowsXP too but can't install it because it won't recognize my hard drive, as if I needed SCSI drivers or something similar. How did you do this?

Did you get any special drivers? if so, can you point me out where to get them?

Thanks

---

### Post by notwen on 2008-02-14
Check [this]("http://news.softpedia.com/news/Install-Windows-XP-On-SATA-Without-a-Floppy-F6-47807.shtml") out.  The Inspiron 1420n's SATA drivers can be found [here]("http://support.dell.com/support/downloads/driverslist.aspx?os=WW1&osl=EN&catid=-1&impid=-1&servicetag=&SystemID=INS_PNT_PM_1420&hidos=UBLN&hidlang=en").  The XP install CD does not have SATA drivers included on it, so XP wil not recognize your laptop's SATA HDD, the above guide will show you how to create a XP installation CD including the drivers you'll d/l form the second link I posted.  The application, nLite will make your new XP install CD for you.  Post back if you run into any issues.  Best of luck.  =]

---

### Post by carnagex420x on 2008-02-14
I used Nlite also because Vista wa not an option for me, and i can not slipsteam drivers w/o a 3rd party app....cuz im no Windows guru. lol

-also the Dell website has XP drivers now, wen i first did the install they only supported Vista so i had 2 do sum running around, it should be fairly simple.

---

### Post by Acapulco on 2008-02-15
> **Acapulco said:**
> Hey, I bought a WindowsXP too but can't install it because it won't recognize my hard drive, as if I needed SCSI drivers or something similar. How did you do this?

Did you get any special drivers? if so, can you point me out where to get them?

Thanks


Hi again notwen, I'm about to build my custom Windows cd (thanks a lot btw :] ) but I'm not sure about the SATA drivers, are these the ones?

Intel Matrix Storage Manager Driver R154200.EXE	324 KB??

I'm guessing it *must* be it, since the only other option is 20m. Just making sure.

Thanks again. You made me Vista free finally

---

### Post by fragos on 2008-02-15
I'd down;oad and install the Dell Ubuntu DVD rather than creating it piecemeal.  My 1420n works great with it.

---

### Post by Acapulco on 2008-02-20
> **fragos said:**
> I'd down;oad and install the Dell Ubuntu DVD rather than creating it piecemeal.  My 1420n works great with it.

I got 7.10 working just fine (*cough* except for some suspend/hibernate issues and network card issues *cough*) but I need XP for some things like trying out Processing programs in both platforms.

---

