---
title: "Dell and 8.04, when?"
date: 2008-07-15
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Talon2 on 2008-07-15
I'm not seeing any information concerning when or if Dell is going to switch from 7.10 to 8.04.  Does anyone have any information they would like to share?

I'm considering getting a pre-loaded notebook but I want to get it pre-loaded with 8.04.  I've been waiting for some time now.

---

### Post by fragos on 2008-07-15
I can't answer but have been running 8.04 on my 1420n for some time. Check out [http://linux.dell.com/wiki/index.php/Ubuntu_8.04](http://linux.dell.com/wiki/index.php/Ubuntu_8.04). I did #3 and #4 on that page.

---

### Post by Cclips on 2008-07-15
> **fragos said:**
> I can't answer but have been running 8.04 on my 1420n for some time. Check out [http://linux.dell.com/wiki/index.php/Ubuntu_8.04](http://linux.dell.com/wiki/index.php/Ubuntu_8.04). I did #3 and #4 on that page.

Been running it on my 1420 since the day I got it (little over a week) and haven't noticed any real problems.

---

### Post by drsaamah on 2008-07-15
Honestly, I would say don't worry about Dell's 'n' series.  First of all, for whatever reason, the 'n' series have been more expensive than the windows loaded counterpart.  That's complete crap considering the fact that the operating system is completely free and the majority of the driver development and troubleshooting has been done for free by the open-source community (which is why "Dell's" ubuntu versions come out weeks if not months after that particular release).
Secondly, I personally didn't like the Dell version of 7.10 and switched back to the Ubuntu release of Gutsy after I broke my system.  As long as you can run the command "sudo apt-get install nvidia-glx-new" you'll be fine.  The Dell version just came with a random nvidia splash screen upon start up, and a whole bunch of shady looking hidden files in my home folder.
Thirdly, I've been running 8.04 (which I don't believe has been released by Dell yet) on my XPS M1330 and it has been working just great.  Despite my rant above, Dell does do a great job of making computers from a hardware persepective.  As long as the hardware has been commericially available long enough for the community to work with it, it'll work just fine with any Linux distribution.

---

### Post by PinkFloyd102489 on 2008-07-16
I got an Inspiron 1720 with Vista and dual booted Ubuntu on it. Had to ndiswrapper the wireless, but other than that it works great.

---

### Post by fragos on 2008-07-16
> **PinkFloyd102489 said:**
> I got an Inspiron 1720 with Vista and dual booted Ubuntu on it. Had to ndiswrapper the wireless, but other than that it works great.

The default WiFi card with a Dell Vista laptop is the issue. If you buy a Dell with Vista and want to run Ubuntu, order the optional Intel WiFi card. It works out of the box with Ubuntu.

---

### Post by Muflon on 2008-07-16
I agree with Fragos.  Get the Intel Wifi option for problem free Wifi using 8.04.

I have a 1525 running 8.04 and everything works.

```
No. Description Quantity
210-20647 Inspiron 1525 CORE 2 DUO T5750 2.00GHz,667,2M 1
230-10150 Display 15.4" Widescreen WXGA (1280x800) with TrueLife 1
319-10001 2.0 Mega pixel web camera NOT included 1
320-10176 LCD Back Cover Jet Black Matte 1
340-15081 Ship Accessories European Inspiron 1525 1
340-15092 Documentation English EMEA 1 (EN, AR, DU, FR, GE, IT, CR,SP) Inspiron 1525 1
340-15097 Resource DVD Inspiron 1525 - (Diagnostics & Drivers) 1
370-12184 Memory Dual-Channel 2048MB (2x1024) 667MHz DDR2 SDRAM 1
400-13453 Hard Drive 160GB Serial ATA (5400RPM) 1
429-12964 Optical Drive 8xDVD+/-RW Drive including SW 1
450-11244 AC Adapter 65W 1
450-11692 Power Cord UK 1meter 1
451-10521 Battery Inspiron Primary 6-cell 56WHr Li-Ion 1
460-10041 Not Included Carry Case 1
490-10775 Graphic Intel Integrated GMA X3100 1
506-10024 Dell Travel Remote control 1
530-10762 UK Modem Cable and Adapter Internal V.92 Data, Fax, Voice Functions 1
555-11010 Intel® Pro Wireless 3945 802.11a/b/g Mini-PCI Card EUR 1
583-11777 Internal Keyboard Uk/Irish (QWERTY) 1
619-10906 English - Vista Home Premium 1
630-11001 English Microsoft Works 9.0 (Word Processor, Database) with Recovery CD 1
640-10280 UK Internet Service Provider - Tiscali 1
640-10395 English - Adobe Reader 8.1 1
640-10551 Dell Support Center 2.0 1
650-10792 English McAfee Security Centre 9.0 - 30 Day Trial Version 1

```

---

### Post by Talon2 on 2008-07-16
> **drsaamah said:**
> Honestly, I would say don't worry about Dell's 'n' series.

Let's think about this for a moment.  Spending your hard earned $ is very similar to voting in an election.  We send the wrong message to those selling computers if we are not supporting the product we really want.  In my opinion it is very very important to worry about and buy the "n" series systems.

> **drsaamah said:**
> The 'n' series have been more expensive than the windows loaded counterpart.  That's complete crap considering the fact that the operating system is completely free and the majority of the driver development and troubleshooting has been done for free by the open-source community (which is why "Dell's" ubuntu versions come out weeks if not months after that particular release).

I've compared the prices of the system I'm looking at with Ubuntu and Vista.  The prices generally end up very similar though it can take a while to compare apples and apples given the system Dell uses.  Dell coupons are available and should be used.

Just because Ubuntu is "free" does not mean that it is the low cost solution for a manufacturer.  Vista pre-loads come with a lot of Bloatware.  Companies pay Dell to put that Bloatware on their systems.  This $ offsets a lot of the cost of Vista...maybe even more than the cost of Vista in some cases.  Unfortunately Ubuntu does not have this same advantage which is a major reason it is important to buy the "n" series systems.  

There is no good excuse in my mind for the delays in switching over to a new release of Ubuntu on the pre-loaded Dell's.  The development process should include testing on the pre-loaded Dell's during the dev cycle.  For that matter, many, if not most, of the Ubuntu developers should be working on Dell systems.  What I see is a lone major pre-load agreement that is treated as a second class citizen.

---

### Post by PinkFloyd102489 on 2008-07-16
Does that card support monitor mode? Ive been through hell and back trying to get the bcm43 drivers working, including recompiling the kernel, which broke the installation completely.

If it does support it, I might send it back and have them replace it.

---

### Post by Gringexican on 2008-07-16
> **Talon2 said:**
> Let's think about this for a moment.  Spending your hard earned $ is very similar to voting in an election.  We send the wrong message to those selling computers if we are not supporting the product we really want.  In my opinion it is very very important to worry about and buy the "n" series systems.

**Well put.**  Which is why I have a 1420n laptop running Hardy (my baby) and a 530n tower which I just upgraded to Hardy (so I'm having to work through a few issues with the 2.6.22-18 kernel).  I LOVE running Ubuntu, which is a *major* reason I bought 2 n-series Dells.  Granted I bought a second HD for the 530n so I could keep a copy of WinXP in a 'sandbox' environment for the apps I need to run out of Win -- otherwise most things are easily done in linux.

If I could get VMware to recognize my HD1 partitions I wouldn't have to dual boot at all, but it works remarkably well at emulating the primary programs I need to reduce my need to shutdown and reboot into Win.

Until and unless other computer manufacturers want to expand my options by jumping on the bandwagon and producing quality computers with linux on them (and offer decent support for proprietary problems) Dell will continue to have my dollars when it comes time to purchase a system.

---

### Post by fromgi on 2008-07-18
Dell FINALLY updated their site with 8.04 and new hardware options.  Finally!

---

### Post by LMP900 on 2008-07-18
> **fromgi said:**
> Dell FINALLY updated their site with 8.04 and new hardware options.  Finally!

Thanks for the heads up. :) Although after checking out the site, I see that the 1420n is no longer available. Hopefully, their Studio line will be preloaded with Ubuntu soon.

---

### Post by Talon2 on 2008-07-18
> **fromgi said:**
> Dell FINALLY updated their site with 8.04 and new hardware options.  Finally!

Yes, I see they are shipping 8.04 now.

Unfortunately I don't see the 1420 listed any longer.  I'm reluctant to order a 1525 or 1330 as the net is full of user reviews speaking bad about the hardware quality on these systems.  While the 1420 has been banged in some reviews, most of the problems reported have to do with customer support or Vista.  All in all, reports tend to indicate that the 1420 may be the best bet as far as hardware quality goes... and it was the only option where I could order the matte (non-glossy) screen.

I like good hardware.  My current notebook is an IBM T23 which is still going strong after 6+ years.  My wife has stolen it so I'm looking for something new.

---

### Post by nanog on 2008-07-18
Dell now offers the quadcore capable 530ns!!!!


Flash the bios and you can upgrade to 8 gb of RAM!

---

### Post by RedRat on 2008-07-20
According to Dell they are now shipping Hardy 8.04 LTS as of July 18.
Check this out:
[http://www.dellcommunity.com/supportforums/board/message?board.id=sw_linux&thread.id=14330](http://www.dellcommunity.com/supportforums/board/message?board.id=sw_linux&thread.id=14330)

---

### Post by brons2 on 2008-07-20
> **Talon2 said:**
> 

I like good hardware.  My current notebook is an IBM T23 which is still going strong after 6+ years.  My wife has stolen it so I'm looking for something new.

I have a ThinkPad R32 at work, it's still goin strong and now with Hardy.  Unfortunately the new ones after the Lenovo takeover are not as good.

---

### Post by bryncoles on 2008-07-22
i have an inspiron 1525n, bought with gutsy and upgraded to hardy. had it about a month now and theres no problems with it at all (except one issue with a dodgey battery which dell resolved very speedily). 

so from my experience i can say theres nothing wrong with the 1525n

---

