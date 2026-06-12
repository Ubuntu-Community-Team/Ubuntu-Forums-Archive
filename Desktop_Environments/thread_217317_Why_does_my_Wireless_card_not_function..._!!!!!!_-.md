---
title: "Why does my Wireless card not function... !!!!!! :-?"
date: 2006-07-16
forum: Desktop Environments
---

### Post by Efrain Valles on 2006-07-16
I know there are many posts on this... but my question is... WHY does my card work on my LIVE run of ubuntu 5.10 and when I installed it didn't work... 

that doesn't make any sense...

Running Ubuntu Breezy
D-Link DWL-650+ on a compaq presario 1700t
:-?

---

### Post by Titus A Duxass on 2006-07-17
Welcome to the wacky world of wireless linux.

---

### Post by Neobuntu on 2006-07-17
...which is not nearly as "wacky" as the Windows world. Try and see how the fun starts when you don't buy a new card (use what you've got) with a new XP driver. Some old WiFi devices for Windows have old buggy drivers and some new devices with new drivers are poorly written as well. If you buy a software based device, it is HIGHLY dependant on the driver AND it's new revisions (if there is one for your particular card) and may or may not then make things worse. No, if you want stability AND automagic installation, just get what is known to work. No time wasted.

Note: If you just bought a new notebook and the WiFi just can't work with new Ubuntu Dapper then tell the vendor you want a real WiFi card! Dell sent us a newer Intel based (mini-pci) internal (easy to replace) WiFi replacement (FOR FREE) and it just worked via Dapper support AUTOMATICALLY. Now I hear the bain of chipsets, "Broadcom" has some new support too but I haven't tried it, nor would I want it's software based unstable POS.

Guess what? Get a known and supported Wifi today and it just works with Ubuntu. If you take into accout that SOME other WiFi device can be used in Ubuntu with it's actual XP driver, the offending (closed and poorly supported) devices left out, are few. Even with the super easy; point and click "Windows Wireless Drivers" package, you will need to be reselect (the the XP drivers) as a newer and better kernel for your CPU comes through.

Ubuntu does the best job of bringing past and new drivers (modules) with it, as it's core (Kernel) upgrades; automagically. With the addition of point and clickable "restricted-modules" per Kernel, Ubuntu just gets better and better.

As to your specific problem there are several possibilities.

1. Use Dapper.

2. Human error. Sorry but it is technically the most probable reason for working live and then not installed. WiFi requires many settings to line up. Let's assume though, this is not the case. 

3. Perhaps you are using a kernel image and it's matching modules that don't fit with your hardware.

4. Your model MAY be like one I have, in that it has the same internal chipset where it's maker is actually linux hostle. Mine works via said NDISwrapper. Install (using non-WiFi internet first) and then just click "Windows Wireless Drivers"(or type "ndiswrapper -h" if you prefer; from the CD.)

The thing is, if the native driver attempts to load automatically AND you are also running the ndiswrapper module, they conflict. You must remove one. Like this:

modprobe -r acx

...and reload the ndiswrapper

Many times it's just a matter of restarting networking.

sudo /etc/init.d/networking restart

...or just reboot.

In my case I had to move module "acx" out of the way because it works with "b" cards (acx100) and not my "g"(acx111). It was as simple as copying the  acx module to my /root directory to disable it on boot up. I've been using  this 802.11g card by ndiswrapper for years now.

I've just had to learn to reselect the XP driver (placed in my home directory) and also (by the way) switch my old Nvidia card to use the legacy driver for it, as a new kernel upgrades. It's the best of all worlds and I don't have to compile ANYTHING.

Again, it's amazing how well all this just works, matches and does so quickly with Ubuntu.

Remember uber-geeks, time is money AND we really do not want to support those chipset devices (companies) that require the NDISwrapper. So choose wisely. 

There is NO GOOD REASON for a device that only works in Windows. That really is a function of corruption, not an Ubuntu failing.  Why would you limit yourself? The open and supported ones are NOT more expensive. Now that all the hardware vendors are starting to jump on the Linux bandwagon, guess which ones I intend to support? (Hint: The first ones.)

Conversely, SOME vendors will NO LONGER even let you read what chipset is in the darn device. Belkin for example! Why would you think they would do that? This is a critical issue because different chipset makers are in the SAME device, just MAYBE having different revision numbers(so watch the versions.) Translation: They use a whole different driver so beware.

Summary: check first.

Hope that helps.

---

### Post by Efrain Valles on 2006-07-17
Gee..

Very Deep and Cool solution... 

thanks ... I'll give those a try

---

