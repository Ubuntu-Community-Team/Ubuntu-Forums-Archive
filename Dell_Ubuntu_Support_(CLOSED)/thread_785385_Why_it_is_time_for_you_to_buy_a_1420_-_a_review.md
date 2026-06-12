---
title: "Why it is time for you to buy a 1420 - a review"
date: 2008-05-07
forum: Dell Ubuntu Support (CLOSED)
---

### Post by ejw2076 on 2008-05-07
Dell Inspiron 1420 with Ubuntu Linux 8.04 LTS

  I recently purchased an Inspiron laptop from Dell's outlet store.  The laptop has a T8300 dual core processor that runs at 2.4GHz with 3Mb of cache, 4Gb of pc5300, Nvidia Geforce 8400M GS, 320Gb 5400rpm HD, Intel 4695AGN and the glossy TrueType 1440x900 resolution display.  All this came in at about $840 with a 15% off coupon; a price I couldn't match anywhere else for similar specs.

  The laptop was purchased on a Thursday afternoon, shipped Friday, and came in Monday.  When I opened the box I found the laptop in packaging that looked to be for a 15&#8221; model.  It wasn't secured and was allowed to bounce around a bit.  No damage was done, and even for a refurb, the laptop looks brand new.

  As far as the hardware goes, the first thing I noticed was how heavy this thing felt; it was actually a little bit deceiving.  The display is bright and crisp, but very glossy, and unfortunately, the glossy comes standard with the higher resolution.  The keyboard is incredible and has absolutely no give.  When you hit a key, it actually feels like it could take a beating.  In fact, I think it may be more solid than the Thinkpad keyboards.  I also like the blue led's that light up the various buttons on the laptop, and the dual headphone ports will also come in handy (I never have a splitter when I need one.)

  When I fist turned it on, I was greeted with Windows Vista Home Premium.  Having never had a chance to actually tour the operating system at great length, I wanted to play.  I gave it my info then logged in.  It took a while for everything to load up, but I was pleased to see that the battery arrived fully charged.  When it had finally settled I took it to my desk and hooked up an Ethernet cord.  That is when the laptop blue-screened and rebooted on me.

  So I got on my desktop and downloaded a copy of Ubuntu 64-bit 8.04 Alternate.  I got the alternate cd because I do plan on using disk encryption and this is the easiest way to do so.  I turn it on and put in the cd.  When it first turns on it gave me two options: F2 for bios settings, and F12 for boot menu.  I know this is pretty much the standard now, but I like not having to go into the bios just to boot from a cd.

  I press F12, select CD, and am quickly greeted with the Ubuntu menu.  I hit enter and go through the motions.  When I get to format disks, I choose manual and set up a 250Mb boot partition, and the other 319 gigs encrypted; I'm not worrying about swap space with 4 gigs of memory.  It takes a bit of time to complete, but after a while, it finally asks to reboot.

  It restarts quickly then asks me for the password for the encryption.  I give it the pass and it loads into the Ubuntu login screen in about 30 seconds, but it isn't running in the correct number of colors.  It takes about 15 seconds to go from the login screen to a settled desktop where it tells me to download updates and that I can use a proprietary Nvidia driver for my graphics card (which is good news because I know the network card works.)  I enable the driver and it gets the packages and installs them, then I go through all the updates and reboot.  All very easy.

  There were a few things that weren't working.  The LCD brightness control would only make huge increments, the second headphone jack wasn't working, the wifi light wasn't coming on (which I assumed meant wireless wasn't working) and the fn number pad wasn't working.  After a couple quick searches, I found out that the wifi light won't come on, even if the wireless was working (which it was, actually.)  The headphone jack (which so happens to be the surround channel) just needed to be unmuted by running alsamixer in the console, and the lcd brightness issue is fixed by adding &#8220;blacklist video&#8221; to /etc/modprobe.d/blacklist.   I haven't found a fix for the fn num pad, but I might be able to map the key presses, and if not, I really don't use it that often.  

  As far as software goes, Installing Java and getting Eclipse running was fairly painless other than a security alert that would pop up when I would run eclipse (fixed by adding ~/.mozilla/eclipse.)  Everything else was easy with no hiccups at all.   Overall, configuring the software to my own needs was incredibly easy.

  And one final thing I would like to mention is the headphone jacks.  They actually sound pretty good on my Shure e3c's.  No, these aren't super audiophile ear buds, but they will display the creaks in *The Wall*, and this laptop had no background noise, even when the cd is spinning.  I'll have to try it with some AKG 701s, but I think that I could use this as my source rather than a dedicated mp3 player (while traveling, of course.)

  Overall, I am very satisfied with this purchase.  The fact that almost everything works with so little modification is a testament to how far Linux has come in the past couple years.  If you are considering getting a laptop, I must suggest this one, especially if you are looking to install linux.

---

### Post by ejw2076 on 2009-01-16
Alright, so I had to send the laptop to dell due to a problem with the screen and motherboard.  I went ahead and zero-filled the hard drive before shipping it to them:

[COLOR="Red"]Zero-fill a hard disk:[/COLOR]
```
dd if=/dev/zero of=/dev/(drive to fill) bs=1M
```

When I got the laptop back, I upgraded to 8.10.  I had a problem with the 4965AGN Wireless card under this version.  It would connect, but would lose connection after a few minutes.  After searching for a fix, I gave up and rolled back to 8.04LTS.  The install went smooth, but there was a problem with the sound - only one of the front audio ports was working.  This is the same problem I had before, except when I run alsamixer, the surround channel wasn't present.

The fix to this is to double click the speaker in the system tray - this will bring up the audio controls.  Select edit>preferences and make sure that the surround channel is set as visible.  You can then unmute this channel to activate the second headphone jack.

If anyone has any luck with the wifi card under 8.10, please post it.

---

### Post by timcredible on 2009-01-16
> **ejw2076 said:**
> 
If anyone has any luck with the wifi card under 8.10, please post it.

have you tried ndiswrapper?

---

### Post by ejw2076 on 2009-01-19
> **timcredible said:**
> have you tried ndiswrapper?

I didn't give it a shot.  I needed my computer for class, so after playing around with the provided drivers and not finding anyone else with too much success I decided to roll back.  I had 8.04 running on this laptop for about 6 months without any issues at all, so I figure I might as well go with what I know works.

---

### Post by ejw2076 on 2009-04-23
I upgraded to a 30gb OCZ Vertex SSD today and installed 9.04.  The Vertex has been flashed with the latest firmware and is a little more than 3 times faster than the 5400 rpm western digital that was in there.  Install has gone smooth, with only one exception.  The wireless card is not working well.  It will connect, but it keeps dropping connection at random intervals.  I've read about this online already, but can't find anything that works.  I'll work on it and post it here if I find a solution.

---

