---
title: "Is the Studio XPS 16 linux-friendly?"
date: 2009-09-01
forum: Dell Ubuntu Support (CLOSED)
---

### Post by cos85 on 2009-09-01
I'm looking to buy a laptop, and those Dells look pretty awesome. I'd like some opinions on how compatible this laptop:
[http://www1.euro.dell.com/uk/en/home/Laptops/laptop-studio-xps-16/pd.aspx?refid=laptop-studio-xps-16&cs=ukdhs1&s=dhs](http://www1.euro.dell.com/uk/en/home/Laptops/laptop-studio-xps-16/pd.aspx?refid=laptop-studio-xps-16&cs=ukdhs1&s=dhs)
would be with a mainstream *buntu install, before I take the plunge and get it.

There's a slightly outdated wiki page here:
[http://www.linlap.com/wiki/dell+studio+xps+16](http://www.linlap.com/wiki/dell+studio+xps+16)
that says the ATI HD 3670 doesn't play very well with it (what a surprise). The same laptop optionally comes with an HD 4670, which is supposedly supported by the ATI driver. If anyone has this laptop, can you please confirm if that is the case?

Finally, is there a chance I'd be able to convince them to give me a refund for Windows? I don't need it at all, and it would be a complete waste of money.

---

### Post by AliTabuger7 on 2009-09-01
Why not get one of the Dells that already have Ubuntu installed?

You're guaranteed  compatibility that way, and don't have to pay for windows.

---

### Post by cos85 on 2009-09-01
Alas, they only sell a couple of Ubuntu netbooks in the UK:
[http://dell.co.uk/ubuntu](http://dell.co.uk/ubuntu)

---

### Post by AliTabuger7 on 2009-09-01
Well, if you're still looking to avoid microsoft tax: 
[http://system76.com/index.php?cPath=28](http://system76.com/index.php?cPath=28)

Sorry I'm not answering your question, but I have no idea about that, so I'm suggesting alternatives.

---

### Post by cos85 on 2009-09-01
Thanks, but as I said I'm in the UK.

---

### Post by muteXe on 2009-09-02
[http://forum.notebookreview.com/showthread.php?t=342999](http://forum.notebookreview.com/showthread.php?t=342999)
[http://forum.notebookreview.com/showthread.php?t=342999http://www.linlap.com/wiki/dell+studio+xps+16](http://forum.notebookreview.com/showthread.php?t=342999http://www.linlap.com/wiki/dell+studio+xps+16)

Dunno how up to date that last page is, but i hope it helps.

mute

---

### Post by cos85 on 2009-09-02
Thanks, I've asked in that thread and they say it works pretty well. I'll get it and post my experience on here/UbuntuHCL for the record (wish me luck).

---

### Post by Sophont on 2009-09-07
Hi, 

I got myy XPS 16 last week and immediately installed Ubuntu 9.10 (Karmic Koala - warning: still in alpha) on it. Because of the 4GB of RAM I have, I choose the 64 bit version.

Installation was the usual pleasurable walk in the park.

Ubuntu works fine (pretty sure 9.04 would do just as well) with the following exceptions:
*  No 3D atm - I have hope that the proprietary fglrx driver will support 4670 soon (the desktop variant is already on list of supported cards). New  and shiny free RadenHD driver will take a few more months before it's ready.
2D works fine with the auto-installed old open source driver. Video and flash gave me no trouble.
* If you get the Blue Ray drive then CD/DVD work well - but you can'z rreadily play BR videos on Linux. There's a workaround posted on the ubuntu wiki that explains how you can watch the BR movie - but it's veryy inconvenient.
* Hibernation works, Standby is hit and miss (but I'm using an alpha version afer all).
* Bluetooth doesn't work after standby/hiberate - but the same is true on windows (I kept a shrunk Vista partition for games until 3D gets fixed.).
* internal DVB TV tuner card works - but then no channels are found. But again - same is true on windows. I had to download the firmware for the dvb card.

Everything else works and did so out of the box. That includes audio, media keys, touchpad, microphone, etc... I connected a Bluetooth mouse - works great.

It's a *great* laptop.

---

### Post by shrndegruv on 2009-09-11
I have an xps studio 16 with the 3670HD Ati card.

More things work than not.  Suspend/hibernate do not work, and to be specific, the return from suspend/hibernate is the part that is not working.

the mouse pad is a bit quicky, but i dont know if that is a linux issue.  

when i upgraded to 9.04 there was serious issues with resize/maximize windows, but installing xserver from a PPA fixed it.

I have seen 2 complete crashes.  I cant play urban terror with compiz on.  

other than that, things seem to work good.  I have not tried the blueray.  Screen is awesome.  Battery life sucks (a little more than an hour) with the six cell battery.

---

### Post by MALEADt on 2009-09-11
Working quite good in here, using 9.04.
I have the edition with the HD4670 in though, which wasn't correctly recognised with a stock 9.04. That way, it loaded Vesa and bumped me on a lower resolution. After installing the newest ddx (from the radeon ppa) I have the full resolution now (though with some cursor corruption). The xorg-edgers ppa crashed X, so it's not recommended.

The installation went perfectly, the wifi (an intel 5300) is detected correctly, bluetooth as well, and all multimedia keys seems to work too. Only the brightness keys seem to work a bit flaky, more specifically pressing "BRIGHTNESS UP" only raises the brightness from the lowest level to lowest + 1 (pressing it multiple times always goest back to the lowest level). Manually specifying the brightness (via the applet) works perfectly, a good replacement for now.

Webcam works as well, haven't tested the mic yet but I've read you need to specify the "digital input" in order to get the mic working.

Hibernate works, suspend works sometimes though the DVB tuner doesn't after resume. In order to get the DVB-T tuner working you need to download a firmware though, which according to [this](http://www.der-schnorz.de/?p=92) works if you download another and rename it (confirmed, the tuner works).

Battery life isn't excellent though, fully charged the laptop keeps on working for 1h30, with radeon's LowPowerMode enabled (on full brightness though). Not that good, but might get with time (radeon powersaving features are still a todo AFAIK).

All together: this laptop works pretty good under Linux, and the features which doesn't yet (3D accel, brightness keys) will probably get fixed soon or won't be difficult to fix.

---

### Post by shrndegruv on 2009-09-11
hmm.

to be clear, you are using the open source radeon driver?  

With fglrx suspend/hibernate does not work.

---

### Post by dFlyer on 2009-09-11
Can not answer for the Studio XPS 16, but I have the Studio 1735 that came with Vista. Spent the last 2 months searching the internet to see if ubuntu would work with it. I found pros and cons, 3 days ago I down loaded the Dell version of 9.04 and installed it. So far everything seems to work great, with no modification, only added additional software.

Gary

---

### Post by Sophont on 2009-09-12
Glad everything worked.

But next time you could just download the iso, burn a disk and boot the live version to see if it works. Googling in addition is a good idea - but you won't find much in 2 months that you didn't find in the first 2 hours.

---

### Post by cos85 on 2009-09-17
Many thanks for the replies everybody. I thought to myself "this is the prettiest of them all", so I just went ahead and got it in the end.

With some minor tweaks it works perfectly, including 3d support and hibernation (with Ubuntu 9.04 32-bit). I had to install the latest ATI binary driver manually to get the HD 4670 to work as intended (and it DOES work just fine!). The older fglrx driver from the repos had problems with screen brightness and couldn't resume from hibernation (it would freeze at the password prompt).

I've posted a review on UbuntuHCL for posterity:
[http://www.ubuntuhcl.org/browse/product?id=6714](http://www.ubuntuhcl.org/browse/product?id=6714)

Cheers all,
Cos

---

