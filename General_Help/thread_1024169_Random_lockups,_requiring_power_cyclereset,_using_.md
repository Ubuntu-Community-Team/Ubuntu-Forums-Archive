---
title: "Random lockups, requiring power cycle/reset, using OpenGL"
date: 2008-12-28
forum: General Help
---

### Post by Bootsy Collins on 2008-12-28
I recently installed Intrepid, moving over from Debian.  Three times now, I've experienced a hard lockup:  the screen went black, a few sounds from whatever I was doing before got generated (buffer flush?), and then nothing; no keyboard or mouse action produced any obvious response.

On the theory that it's purely a video issue, I've tried to switch over to one of the virtual terminals (ctrl alt F1-F6) and, even though I can't see anything, I've acted as if it was functioning normally and tried to log in and reboot manually.  No luck.

The fact that sounds stopped, despite the fact that twice this has happened while I've been in an app that should be generating sound constantly (bzflag), makes me think that I was experiencing a hard lockup at the kernel level; but there's no trace of this in system logs.  In particular, if I let it sit, I see MARK entries in the syslog file when I look in later.  But still, as far as any input and output is concerned, the thing is dead, and the only course of action that's made any difference is the reset button on the case.

ubuntu intrepid 8.10 32-bit
2.6.27-9-generic
nvidia-glx-177 177.80-0ubuntu2
ASus A8N-SLI w/ Athlon64 3800
eVGA GTX-260

Any advice would be much appreciated.  Thanks.

---

### Post by oxman on 2008-12-29
I am subscribing to this thread.

---

### Post by Bootsy Collins on 2008-12-31
Bump.  Any advice on how to run this problem down would be very very helpful.

---

### Post by Bootsy Collins on 2009-01-14
Bump again.  Recently the nvidia drivers made available on Ubuntu package mirrors changed, so I upgraded to 177.82-0ubuntu0.1; but this is still going on.  In fact, this is happening to me every time I use an OpenGL app in a fullscreen mode under Ubuntu Intrepid.  It's tremendously frustrating.

---

### Post by fbnaia on 2009-01-18
I also have an asus a8n-sli premium, with same cpu (A64 3800+) kernel 2.6.27-9-generic and nvidia drivers 177.82 with ubuntu intrepid 8.10 32-bit.

When my computer locks up, it's completely, no alt+f#, and no REISUB either. But i also get lock ups in  windows and on another custom install of ubuntu intrepid 32 bit on the same computer. Sometimes it's playing a game, sometimes it's just watching some videos on youtube or sometimes just doing nothing in particular.

I also don't get any relevant logs either. But i am guessing this could be a bios configuration issue, i remember when trying to install a sblive sound card i had to have a specific settings or the sound card would freeze the whole system either in Ubuntu or windows, i just ended using the integrated sound so... i will try several bios settings and maybe check the ram just to make sure...

I will report back to this thread if i find any relevant info...

---

### Post by oxman on 2009-01-18
Thank you fbnaia. I will be looking forward to your information.

It seems we have similar tastes in computers. I also have a sb card in my system. Although I must say that I could run Dapper without a hitch with this sytem and did so for a couple of years without a single lockup! It was when I a clean install of hardy that my nightmares began.

a8n sli delux
opteron 175 64 2x 
sbaudigy2
nvidia 7900gto
samsung lcd
1 terrabyte storage
2 gig ram
750 watt powersupply

I get lockups whenever I drag a window. I do have things going on behind the scenes like downloads or other operations. I just can not access them via the keyboard or screen. I suspect an xorg problem. 

I will be watching closely for your bios settings adjustments and the results.

---

### Post by fbnaia on 2009-01-22
Ok.. just for an update....

I reseated the Ram and cleared the bios settings.

Using the default settings detected on the bios, i still had random lockups in Ubuntu ***and*** Windows.

Then i went to tweak the bios settings to the usual stuff i use, disable unneeded devices/stuff, etc. and now i'm not getting any lockups so far...

Probably going to a lanparty in 2 days, so i will be testing to make sure the issues are resolved....

Again, in my case, it does appear to be a Hardware/settings issue.

To be more specific about the bios settings, i just disabled all the sata/raid stuff i dont use, disabled firewire, not using usb 2.0 because of some usb drive compatibility, game controller/midi also disabled, all other stuff is at auto/as detected by bios.

---

### Post by oxman on 2009-01-22
Thanks fbnaia, for the update. I've just done a complete backup of my data on an external hard drive and plan on doing a clean install. I have never used the raid functions.I do keep the midi on but turn off LAN and other ports that I do not use (I'm on dialup). That is how I have set it up from the beginning. I have been very curious about the acpi function on the motherboard. It is grayed out (taking my option to manipulate it away) which I did not notice happening with dapper.

---

### Post by Bootsy Collins on 2009-01-31
> **fbnaia said:**
> I also have an asus a8n-sli premium, with same cpu (A64 3800+) kernel 2.6.27-9-generic and nvidia drivers 177.82 with ubuntu intrepid 8.10 32-bit.
Hi.  You don't mention which nVidia card you have.

I'll try disabling unneeded BIOS stuff, but I'm starting to wonder if my problems aren't power supply-related.  The GTX-260 requires 36A on the 12V rail.

---

### Post by fbnaia on 2009-02-01
Hi, i'm using a  XFX GeForce 8500 GT 512 ram, so it's not really "power hungry" as a GTX-260. Currently I'm using a Coolermaster Real Power Pro 750W power supply.

I did resolve my lock up/freezes issues, all i did was reinstall the ram again, and now no more freezes. I guess with all that moving around the computer, lanpartys etc, it was just bound to happen.

When i was researching the a8n-sli premium motherboard, i remember that the most critical parts for getting a stable system was using the correct ram and a powerful enough power supply. I was originally trying to get a Turbo-Cool 860 ESA, that one will give you 64A on the 12v rail!, but life got in the way :), but i'm happy with a stable system.

---

