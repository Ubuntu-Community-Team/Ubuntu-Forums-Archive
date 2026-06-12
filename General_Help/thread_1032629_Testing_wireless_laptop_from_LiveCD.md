---
title: "Testing wireless laptop from LiveCD"
date: 2009-01-06
forum: General Help
---

### Post by rudy.elgato on 2009-01-06
Hi,

I've converted 2 wired desktops to Ubuntu several months ago and am completely satisfied and have no intention of ever reverting them back to Windows.

Now, I have an older Dell laptop still running Windows XP Pro that my daughter uses.  Lately I can see "junk" accumlating on it and figure it's only a matter of time until reaches the point where some serious scrubbing will be required or it just plain hoses up.  At that time (or sooner?) I'd like to go ahead and switch it to Ubuntu as well.  My only concern is getting the wireless to work properly on it.  

The other day I burned a new copy of LinuxMint 6 (which is really just 8.10 will most of the restricted multimedia packages already included, right?) and loaded ran that livecd on the laptop.  I'm extremely pleased with what I saw and the way things ran and the only issue is wireless.  The laptop has a Broadcom BCM4306 device and works perfectly fine under Windows XP.  When running from the livecd I have no wireless connection at all.  I thought maybe there's be some restricted drivers already installed on the system that merely needed to be enabled, but nothing appears under "Hardware Drivers". 

Searching around here I see alot of mention of "ndiswrapper" or "fwcutter", but it seems like the only time I'll be able to even try some of these fixes is after Ubuntu/LinuxMint has been installed on the laptop.  Then, I'll need to hardwire the laptop to my wireless router to connect to the internet and start downloading the packages needed to try and get wireless to work.  

Does this sound right?  I really do not want to commit the laptop to a real install until I'm certain I can get wireless to work.  Can anyone provide some hints how to test wireless from the livecd?  Any advice is appreciated.

Thanks...

---

### Post by cowboys2010 on 2009-01-06
As far as I know, Linux must be installed on the laptop to do anything with the wireless. NDiswrapper is a great program for wireless cards in Linux. What it does is use a windows driver to work with linux. Once you download the ndiswrapper, use these directions to get your card working. 
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

Sorry I couldn't provide more info. I know the ndiswrapper works, cause I've used it a bunch of times, and it works like a charm.

---

### Post by compman25 on 2009-01-06
I can boot with a live cd and use my intel wireless card without any problems.

---

### Post by rudy.elgato on 2009-01-08
compman25, cowboys2010, thanks for taking the time to reply...

Anyone else have any ideas on how to test wireless from a livecd?  Should it work right from the livecd as compman25 mentions?

I did have a close look at the thread and instructions cowboys2010 mentions, and man that seems mighty convoluted just to get wireless working.  And the real ugly part is that it can only be attempted after having fully installed the system.

Something, reading some more (alot more actually...) on this issue with wireless and broadcom, I've come across several threads that with 8.10 it might be as simple install 8.10 using a hardwired ethernet connection (which I can do).  Then after the install is complete make sure all synaptic reposities are enabled and run an update.  There will be some updates made to the system including "b43" which should now be available under "Hardware Driver".  Now unplug the hardwired ethernet connection and enable the driver, and magically wireless should start working.  Does this sound right?

---

