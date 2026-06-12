---
title: "Dell Inspiron 8500 Laptop &quot;Load Error - Boot Error&quot;"
date: 2013-12-28
forum: Dell Ubuntu Support (CLOSED)
---

### Post by cool3 on 2013-12-28
I have this old Dell Inspiron 8500 Laptop and each time I try to boot from a USB or disc it wont' boot and says,

> Load Error - Boot Error

I've tried Lubuntu, Xubuntu, and Linux Mint.  Linux Mint booted from a USB but I didn't see any graphics except for an off looking mouse cursor then the laptop just shutdown. Maybe this Dell doesn't like the fact I'm trying to replace the OS? 

Here are the Dell Inspiron's specs;
[LIST]
[*]1gb RAM @266 Mhz
[*]Pentium 4 processor
[*]Level 2 Cache 512 kb
[*]CPU Speed 2.20 Ghz
[*]60gb harddrive
[*]CD-RW/DVD Combo
[/LIST]

If anyone has any solutions or tips I'd be happy to hear them.  Thanks in advance!

---

### Post by cool3 on 2013-12-28
When I try to boot from a disc it will bypass it and go into Windows XP.

---

### Post by monkeybrain20122 on 2013-12-28
I had exactly the same one. Last I was able to install lubuntu 12.04 successfully form an usb, but if I remember correctly 12.10 didn't work, probably kernel too new(?).It had an old Nvidia card on which nouveau didn't work (graphic all smudged up) so needed to install Nvidia 96 (is it still around?)  it worked but slow. It was made before the time of multitab browsing so opening a few tabs in Firefox would freeze it. mine had only 512MB of ram, you have double that so performance should be better.

It was an old piece of junk but sound was good and could also play some youtube reasonably if use a script to replace flash and go for 480p max. Playing dvd rip offline was fine, I could even rip dvds with handbrake but took a long time. I gave it to someone and a month later it just died. If I remember correctly it also had a broadcom wifi card so it was a bit of a hassle to get it working.

Edited: It came with XP and froze a lot and ran very hot, I remember I could use it as a heater in  the Winter. Lubuntu worked a lot better even though it was still kind of crappy.

---

### Post by cool3 on 2013-12-28
> **monkeybrain20122 said:**
> I had exactly the same one. Last I was able to install lubuntu 12.04 successfully form an usb, but if I remember correctly 12.10 didn't work, probably kernel too new(?).

Edited: It came with XP and froze a lot and ran very hot, I remember I could use it as a heater in  the Winter. Lubuntu worked a lot better even though it was still kind of crappy.

Actually I tried to install Lubuntu 12.04 on it even though I know it's not supported anymore.  I attempted with a disc though so maybe I'll try a usb and see how it goes.  

The Dell Inspiron 8500 definitely runs hot.  I doubt this has much life left in but it's just a fun Linux project.

---

### Post by cool3 on 2013-12-28
There is another problem with this Dell.  If you unplug the power cord from the laptop it turns-off.

---

### Post by mörgæs on 2013-12-28
Before removing Windows you should consider upgrading the BIOS. 

Which graphics card does it have? 
Are you able to install using the [minimal ISO]("https://help.ubuntu.com/community/Installation/MinimalCD")?

---

### Post by cool3 on 2013-12-29
I got Lubuntu booted from a DVD by pressing F12 on the start-up screen.  I didn't have the right version installed on the disc originally.  Some graphics are a bit funky which includes the home icons and the mouse.  Other than that Lubuntu works pretty well.  

The graphics card is a Nvidia GeForce4 4200

How would I upgrade the BIOS on this Dell?

---

### Post by monkeybrain20122 on 2013-12-29
You need to install the Nvidia-96 driver for that graphic card to work. There was a Nouveau bug filed many years ago and it was simply forgotten as the card has become obsolete.

As for the computer shutting down if you remove the power cord, maybe just because the battery is broken.

P.S. Not sure what would be the point of upgrading the BIOS. The thing is more than 10 years old.

---

### Post by mörgæs on 2013-12-29
A DVD is not necessary for Lubuntu. It fits to a CD.

As the problem is solved now there's no need to upgrade the BIOS. Especially old hardware often benefits from a new BIOS, and for this particular one a lot of bugs related to booting were corrected in version A06.
[URL="http://www.dell.com/support/drivers/us/en/19/DriverDetails?driverId=R103836&fileId=2731130900"]
http://www.dell.com/support/drivers/us/en/19/DriverDetails?driverId=R103836&fileId=2731130900[/URL]

---

### Post by cool3 on 2013-12-29
I know you can fit the ISO files onto a CD but I have DVDs.

The BIOS version is A08.

---

