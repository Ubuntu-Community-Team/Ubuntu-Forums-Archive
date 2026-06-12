---
title: "install win98 on 1505n"
date: 2007-06-30
forum: Dell  Ubuntu Support
---

### Post by Denny Johnson on 2007-06-30
Hi, 
I’ve never used Linux, but I like the idea and what I’ve read about it.
I plan on buying a laptop soon, am considering a 1501 or 1505N.
I prefer the idea of an up and running Ubuntu machine, at present my programming skills are basically nil, but feel the need to wean myself from Windows as I don’t want to lose any options I now have while I transition to Ubuntu.
Not that my options are great now, I’m still running a Win 98 Dell Dimension V400c desktop. I have concerns about getting my Canon S300 printer and Ridata flash drive working w Ubuntu, also not sure I can move all my files and documents to Ubuntu.
I have the Win98 disc, is it reasonable to think that a good solution would be to get the 1505n and install the Win98 til I can learn enough to completely transition to Ubuntu?
Thanks

---

### Post by HermanAB on 2007-06-30
Install Ubuntu - or buy a laptop with Ubuntu pre-installed.  Then set Qemu up and install Windows in that.  Qemu is an emulator that is very easy to use and it allows you to run a complete Windows system in a X window on Ubuntu.

I run Qemu and Windows XP on my laptop once a year to do may taxes.

Cheers,

Herman

---

### Post by neptho on 2007-06-30
To follow up: The chances of making the E1505 work with Win98 is nearly nil.  There are no wireless, ethernet, and likely no functioning video drivers for the E1505 with Windows 98; that's why they're not offered on Dell's Support site.  The only way you'll be able to use Win98 is, as mentioned, through software emulation.

---

### Post by dfreer on 2007-06-30
If you are buying an dell 1505, why not just use the windows XP/vista that comes preinstalled until you are ready for ubuntu? or better yet, you can dual-boot the two until you are finally ready to get rid of windows entirely.

---

### Post by technikalKP on 2007-06-30
If you think you'll need Windows, then buy a machine with XP or Vista already installed.  Then you'll have the Windows license and the option of dual booting/running a Windows Virtual Machine.  The price difference isn't that much, and it's a lot cheaper to buy it with the machine than to have to purchase it separately later if you do find you need it.

I personally wouldn't bother trying to install Win98 on any modern machine.  You'd have a harder time finding drivers to support it than you would finding drivers to support Linux/Ubuntu.

---

### Post by Denny Johnson on 2007-06-30
Thanks all, glad I asked, Linux is all new to me, any suggestions greatly appreciated.
It's sounding like I'd better start w a new windows machine. Thinking a 1501.
If so, would I want to configure it any special way to ease into Ubuntu?
For example the 1505n [Dell's Ubuntu version] comes w an Intel chip, Intel 3945 wireless, and Intel 950 graphics
Are AMD chips, dell wireless and most common graphics cards Ubuntu compatible?

---

### Post by dfreer on 2007-06-30
Stay away from broadcom wireless cards unless you like headaches, the intel PRO 3945 wireless works great on my hp dv6000 machine so you are ok there.
Intel graphics are ok if you don't need games, anything new wil require a beefier card (ATI cards are also harder to deal with than nvidia, so I recommend nvidia). The only issues I know of are some intel cards don't display widescreen resolutions by default, although it is an easy fix.
Intel and AMD chips are both supported by ubuntu, so either one is fine. However most AMD chipsets come with ATI cards and broadcom wireless, and most Intel chipsets come with Nvidia cards and of course intel wireless in my experience.

The dell ubuntu version should work just fine, as they made it for ubuntu.

---

### Post by ljonesj on 2007-06-30
i can attest to the pain a broadcom card does

---

### Post by Denny Johnson on 2007-06-30
I've never seen a broadcom card listed as a Dell option.
Are the "Dell" cards Broadcom?

---

### Post by dfreer on 2007-06-30
I'm pretty sure the Dell wireless Mini-cards have broadcom chipsets...
[http://configure.us.dell.com/dellstore/config.aspx?c=us&cs=19&l=en&oc=DNDWKA2&s=dhs&sm=2](http://configure.us.dell.com/dellstore/config.aspx?c=us&cs=19&l=en&oc=DNDWKA2&s=dhs&sm=2)
On this page, it shows you can upgrade to the intel 3945 wireless from the dell wireless 1390 mini-card.

---

