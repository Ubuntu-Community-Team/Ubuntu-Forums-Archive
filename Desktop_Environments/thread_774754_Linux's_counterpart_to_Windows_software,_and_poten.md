---
title: "Linux's counterpart to Windows software, and potential hardware problems"
date: 2008-04-29
forum: Desktop Environments
---

### Post by Jordanwb on 2008-04-29
Hello again, so far I've had a good experience with Ubuntu 8.04 and I'd like to install it onto my main PC, however there are hardware devices that I have that may cause potential problems. Also I was wondering what Linux counterpart exists for a given program which I use.

Hardware:

ATI Radeon x1600 Pro AGP 8X 256 MB (Been told that's a problem)
Sound Blaster Audigy (can't remember model, it's a PCI card) with a Firewire port
Sony DVD+/-RW DRU-820A
Hauppauge TV tuner card (I pretty much never use it, the picture is fuzzy)
HP Scanjet 3670
Lexmark Z515 (heard thats a biggy too)
Logtech MediaPlay cordless mouse <- Not a biggy but bigger than the keyboard
BenQ x700 Pro keyboard <- Not a biggy

I know there's a lot

Software:

Nero Burning Rom
Adobe Premier & Encore (mainly subtitles and basic video editing, no fancy effects, burned to a DVD), I use the firewire port to record video off of my video camera
Maxthon Internet Browser (I don't like Firefox)

I'd probably have to dual boot XP anyways for Google Sketchup, Midtown Madness 2 and TrackMania United.

Thanks. When I get some blank CD's, probably tonight, I'll download the LiveCD and try, but I want to make sure. I saw a thread for the Lexmark.

Ubuntu :guitar: <- What he said. lol

[Edit] Oh also I have a network so the other computers (XP) need to be able to print to it. That's probably where Samba or Cups comes in.

[Edit #2] Regarding the Radeon I found this: [http://ati.amd.com/support/drivers/linux/linux-radeon.html](http://ati.amd.com/support/drivers/linux/linux-radeon.html) on the ati website. It says that the drivers are for X.org, now for some reason I think that that would be a problem.

---

### Post by Trance56k on 2008-04-29
You should not have a problem  with your ATI card....unless you need 3d acceleration. I gave up on ATI cards, The 3d drivers are awful!

---

### Post by Zorael on 2008-04-29
[list][*]Printers are, from what I understand, an iffy issue. If you found a thread for yours then you're likely in the green.
[*]It's possible to set up Logitech mice to use all buttons, but it takes a bit of tinkering. Of course, the mouse works as soon as you connect it, just not back/forward buttons, etc.
[*]Apps like K3b should prove more than sufficient for your basic burning needs.
[*]You can't, sadly, run Adobe Premiere under Wine (marked as garbage in the app db over at winehq.org). Someone else will have to comment on linux alternatives.
[*]As for non-Firefox browsers, there's a whole bunch of them. [http://en.wikipedia.org/wiki/List_of_web_browsers_for_Unix/Linux](http://en.wikipedia.org/wiki/List_of_web_browsers_for_Unix/Linux)
[*]X.org is the "server" upon which all desktop environments run (Gnome, KDE, Xfce, Fluxbox, etc etc). So you definitely want your drivers to be X.org drivers. :>[/list]

---

### Post by Jordanwb on 2008-04-29
I almost fully formatted my main hard drive and gave XP 15GB (Max of 300GB), I installed Ubuntu using the live installer, but it forgot Grub, so I'll use the Alternate installer. I'll take a look at the other browsers.

Thanks.

[Edit] I got a reply from HP reagrding drivers for my scanner and the guy said that the HP nerds are working on drivers.

---

