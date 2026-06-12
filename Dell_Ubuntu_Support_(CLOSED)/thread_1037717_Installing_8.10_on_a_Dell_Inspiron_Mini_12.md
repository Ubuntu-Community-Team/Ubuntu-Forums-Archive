---
title: "Installing 8.10 on a Dell Inspiron Mini 12"
date: 2009-01-12
forum: Dell Ubuntu Support (CLOSED)
---

### Post by catslaugh on 2009-01-12
These are my notes from getting my new Dell Inspiron Mini 12 (aka Inspiron 1210) to work with Intrepid.

Observations about the out-of-the-box system on the way to dusting off and nuking the site from orbit:
[LIST]
[*]It runs some mutant version of Hardy Heron with curious misbehaviors like not wanting to put the task bar up if your system isn’t already connected to the network.  (It looked really broken when I started it up and went looking for a way to tell it to talk to my wireless router; later on, when I had plugged in the wired ethernet when attempting to use the network boot image, it suddenly acted more normal.)  Without the task bar, there’s still a launcher, but not having the Ubuntu menu was rather bizarre, and ctrl-alt-F1 took me to a screen of garbage instead of a text console.
[*]The Dell launcher has a bunch of prearranged icons to take you to various services that probably paid for placement, like eBay.
[*]The 80GB hard drive arrived set up with three partitions:  a 32MB DOS partition with some Dell diagnostic widgets, an almost-78GB ext3 partition holding their Mutant Heron, and a 2GB partition holding what looks like a syslinux setup for reinstalling the ext3 partition.
[*]The system was able to go to sleep fairly gracefully and wake again on lid opening.
[*]Overall, it seemed pretty smooth, so someone who just wants Hardy Heron and starts the system up physically plugged in to the LAN should have a good experience.
[/LIST]
Since it has no CD-ROM drive, I tried installing from a USB stick, following various different sets of instructions, but it tended to fail on a combination of not finding the ISO image (requiring that I alt-F2 over to another console and start messing around with the mount command; note that you need to explicitly run “modprobe loop” before you can do a “mount -t iso9660 -o loop ...”) and that the X server can’t figure out the video setup; if anyone is taking notes for improving the install process, I think the #1 thing to take away from this is “fail more gracefully when the installer can’t figure out how to start the X server”, as it tended to dump me out in the command line without any diagnostics, and it never tried to bring up an X configurator like Fedora did back when I still used Fedora.  (Eventually I figured out how to delete “quiet” and “splash” from the kernel parameters, which gave me more clues.)  What *did* eventually work were [these instructions]("http://ubuntuforums.org/showthread.php?t=316093"), replacing “edgy” with “intrepid”.

Next step:  getting X working.  I'm attaching the Xorg.0.log files from a successful 8.04 startup and a failed 8.10 startup, in case anyone is curious; I’ll post the results of meddling with my xorg.conf to this thread, probably tomorrow night.  Many thanks in advance if anyone has suggestions for configuring X.

---

### Post by catslaugh on 2009-01-13
There&#8217;s no support in Intrepid for the Poulsbo (psb) drivers, and I have yet to figure out how to get VESA to handle the 1280×800 mode the way that Hardy could.  I&#8217;m attaching my current xorg.conf (which gets me to 1024×768 ) and the resulting Xorg.0.log.

---

### Post by catslaugh on 2009-01-14
People searching in the Dell forum for info on the Mini 12 may also find [this thread]("http://ubuntuforums.org/showthread.php?t=1014534") useful.

---

### Post by CrazyDesi on 2009-01-14
Hey.  Thanks for posting this.  I have a question.  I am interested in the Mini 12.  How long does the battery life last?  Is it able to run basic applications well?  How is youtube, openoffice, vlc, etc.

---

### Post by catslaugh on 2009-01-14
I’ve been mostly working on getting the X configuration working right.  YouTube runs just fine, but running in 1024×768 mode with VESA is causing it to exhibit an annoying flicker when it does rapid animation changes.  Scrolling Firefox with the touchpad “wheel” is a bit jerky; I’m messing with the wheel scrolling increments on the Synaptics configuration and in the Firefox about:config to see if I can speed that up.  Haven’t tried starting other major apps yet.  The one time I put it on battery power, it was estimating 4 hours of time, but I never got it below 90% charge.

---

### Post by CrazyDesi on 2009-01-14
Is that on full brightness and is it 6 cell or 3 cell?

---

### Post by catslaugh on 2009-01-14
I have the 6-cell (48WHr) battery; it was configured to automatically drop the brightness a bit as soon as it went onto battery power, but it was still quite readable.

---

### Post by CrazyDesi on 2009-01-15
Would you recommend it?

---

### Post by catslaugh on 2009-01-15
I’m pleased with it thus far as a replacement for my old Latitude L400.  I like the combination of the 12” screen, the light weight, and that it runs cool enough that I have yet to hear any fan noise from it.  Anyone who is *not* a Linux hacker should stick with the mutant version of Hardy on the shipping configuration.

---

### Post by CrazyDesi on 2009-01-15
Well I am more interested in simply getting it for note taking and stuff in class.  I have another computer at home for more heavy tasks.  I just wish the battery life was longer.  I usually keep it at minimum brightness, but I wanted a 3 cell because it was flush with the system and weighs less.  I hope it can last 3 hours ;(.

---

### Post by CrazyDesi on 2009-01-26
Any update on this?

---

### Post by catslaugh on 2009-01-26
No luck getting the Poulsbo support to work with the X11 server in Intrepid yet.  I had the Synaptics touchpad doing horizontal mouse wheel effects as well as vertical at one point, but that seems to have vanished, and neither fiddling with xorg.conf or writing XML for HAL has managed to get the SHMConfig to work yet.  I did get the webcam working, and am planning to fiddle around with the microphone soon so I can use Skype.

---

### Post by skunkbad on 2009-02-17
> **catslaugh said:**
> No luck getting the Poulsbo support to work with the X11 server in Intrepid yet.  I had the Synaptics touchpad doing horizontal mouse wheel effects as well as vertical at one point, but that seems to have vanished, and neither fiddling with xorg.conf or writing XML for HAL has managed to get the SHMConfig to work yet.  I did get the webcam working, and am planning to fiddle around with the microphone soon so I can use Skype.

How did you get the webcam working?

---

### Post by catslaugh on 2009-02-18
luvcview, from [http://linux-uvc.berlios.de/](http://linux-uvc.berlios.de/) , worked just fine.

---

