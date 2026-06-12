---
title: "external USB Hard Drive does not mount"
date: 2009-02-15
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Bezvardis on 2009-02-15
Hi, 
I have a Dell Latitude D400 laptop. Recently bought an externl usb hard drive (Western Digital, My Passport). It mounts fine on all other computers (Windows and Ubuntu PCs as well as Apple Mac) except mine (ubuntu 8.10). A couple of times I have made it mount on my computer but most of the time the hard drive clicks as if it was turning on and off (stops spinning, docks the heads, then again starts spinning) on an interval of about 5 seconds or so.

Does anybody know what I can do about it?

---

### Post by ugm6hr on 2009-02-15
I have seen this before.  Is your USB HD a 2.5" device without an external power supply?

If yes - it is likely that your laptop USB port does not supply enough power to the HD.  I believe this is commonly described with some Mac laptops, but I have had intermittent identical problems with my old Dell Inspiron 500m.

I'd suggest using it predominantly with the laptop power supply plugged in, if that still doesn't work, then you may have to look into options for external power supplies.

---

### Post by ublondie on 2009-11-08
I know this is some time after the original post, but I have exactly the same problems with a Western Digital 160G ext usb hard drive. (MyBook or MyPassport or something?).

I was doing it with Ubuntu 9.04 and is still doing the same thing with 9.10. ...and same as original poster, it works fine on Windows and Mac's.  ...there is no external power supply to it.

Someone mentioned I should try a 'double' type USB cable so I'll give that a try. Will post back here if it is any success. Very frustrating though as it is my main backup storage!

---

### Post by ugm6hr on 2009-11-08
> **ublondie said:**
> Someone mentioned I should try a 'double' type USB cable so I'll give that a try. Will post back here if it is any success. Very frustrating though as it is my main backup storage!

Indeed, a double USB cable takes power from both ports, so that should help.

Does it work OK on Windows on the same hardware?  If so, that is unusual, since the issue is often hardware rather than software in this situation (with the clicking).

---

### Post by ublondie on 2009-11-08
I don't know if all USB cables are the same. I have a double adapter type here that came with a mobile broadband modem, but that didn't work with my hard drive (well, it didn't make any difference). I'll have to go and get another cable just to make sure.

The drive still works fine on *other* Windows machines and I guess to be really thorough with the diagnosis, I would have to re-install Windows on my machine here ....and that ain't going to happen unless I can really help it!  :)

When I first installed Ubuntu on my computer a few months ago (9.04) the ext drive did actually work fine for a while, but then all of a sudden it 'clicked' off one day and that was it. Have had troubles with it ever since ...while it still works fine on other machines.

When you say the issue is often hardware related and not software.... how do you mean. With the computer running the device or the ext drive itself?   ...I've also found the the cd/dvd drive on my computer is very temperamental with Ubuntu. It didn't work at all with 9.04, but at least now works sometimes with 9.10. At worst I have to re boot the computer with the CD in the drive!  :/

...I did find this bug report and started to wonder if it could somehow be HP laptop related?
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/400207](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/400207)

---

### Post by Bezvardis on 2009-11-09
My experience so far is that it is not an Ubuntu fault. Rather the machine does not get enough power through USB slot to the drive. I have also a mac PowerBook and have similar problem only that the drive sometimes works on one of the USB slots and almost never on another. And the drive works just fine on my desktop Ubuntu machine. But I cannot be 100% sure that it is so. For that I would need a better comparison - same machine with windows or ubuntu.

---

### Post by ublondie on 2009-11-09
OK. Thanks for the info. I just never had any problems with the drive in the previous 6 months I was using it with Windows on the same machine. Of course, a hardware fault could have happened in the mean time following the Ubuntu installation I guess?

I'll have to see what I work out. Maybe if I get *really* bored sometime, I'll re install windows just to see if it works. That would eliminate one part of the problem at least!  :/

---

### Post by drseuk on 2009-11-09
I have several similar WD Passport PC-powered drives for backup use. The issue is likely the USB port you're using not being able to provide sufficient power as has been suggested by other posters.

That said, with 9.10 I have (once) experienced a failure of USB auto-mount (for another type of USB stick) though I'm I'm fairly confident this was due to the very limited RAM (and no swap) on the machine I was using at the time.

---

### Post by ublondie on 2009-11-09
OK ...the evidence for lack of USB power is mounting!  :)

For info's sake, I have a seperate 2G swap partition so there shouldn't be any shortage there. I'll get back with reports on how the double USB cable goes.

---

### Post by TriniSource on 2010-01-11
I have been using my Dell Latitude D820 for a couple years along with my 2.5" SATA External Drive, I recently wiped my machine and installed Ubuntu. Although the experience has been overwhelming, my only issue remains the external drive.

It seems to work "when it feels like". If I boot with it - it might work (1 out of 10 times). I have tried all sorts of commands found on similar forums to no avail. I can feel the drive continuously spinning, unlike if I plug it into my Fujitsu Lifebook A series which seems to lack power (starts up then spins down in iteration - never mounted).

I have tested this drive on other machines that mount it seconds after being attached.

---

### Post by Thatlinuxguy on 2010-06-21
I seem to be having the same problem I have a Western Digital 320 gig My passport HDD and it will not mount under Ubuntu but it will mount under windows and this is on my Dell optiplex 755 and Ubuntu also doesn't notice that I have a windows partation anymore to.

---

