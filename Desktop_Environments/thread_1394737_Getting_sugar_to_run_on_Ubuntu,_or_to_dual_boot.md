---
title: "Getting sugar to run on Ubuntu, or to dual boot"
date: 2010-01-31
forum: Desktop Environments
---

### Post by rimshot4 on 2010-01-31
I posted this in the newbie forum, but no one answered. Maybe someone here will be able to help me.

My son loves the talking computer on Sugar and the interface would be safe for him to use. I think it could be a wonderful learning oppertunity. The thing is I can't get it to work on my main Ubuntu 9.10 box--not even with a live-image USB boot. 

I have a 24" 1900x1200 flat-screen monitor. When I start the computer I get Grub, choose my OS, hit enter, and immediately it flips to a blank screen and says "Input out of range." After about fifteen seconds the Ubuntu spash-screen comes up and I'm able to boot normally. This was a minor annoyance, but now I get "Input out of range" when I try to boot of a Sugar live-image USB thumbdrive (the same drive works on my laptop), and I now realize if I leave the DE via alt-cntrl-F1 I get "input out of range" there, too. Yet Gnome works without a hitch.

To work around this I tried to install Sugar as a desktop environment so I could boot into it via the drop-down menu (where you could choose Gnome, KDE, etc.) but whenever I chose Sugar it attempted to load, flashed black for a few seconds, then asked me to log in again. So I uninstalled everything Sugar and came here to ask.

Anyone have any ideas?

---

### Post by rimshot4 on 2010-02-03
Update: I'm now able to get Sugar on a Stick to run on my desktop by adding the boot line "nomodeset". 

For convenience reasons I'd love to get it to run as an Ubuntu DE, but Sugar as a DE continues not to work. I understand they're planning on packaging Sugar 0.88 for Lucid. Right now in the repository we have Sugar-0.84 and Sugar-0.86, neither of which work as a DE on either of my computers. Are the deprecated? Abandonware? Why do we have two versions in the multiverse anyway? I think I'll have to file a bug report on this one.

Does anyone else currently have Sugar successfully running as a DE? If so, how?

---

### Post by dfarning on 2010-02-08
Sadly, Until we get more volunteer help, everything prior to Sugar 0.88 on Ubuntu 10.04 is abandonware.

Until 10.04 comes out, [https://wiki.ubuntu.com/UbuntuSugarRemix](https://wiki.ubuntu.com/UbuntuSugarRemix) is the best, and most supported, way of using sugar on Ubutu.

Please ping the mailing sugarteam mailing list with additional questions.

david
ubuntu sugarteam

---

