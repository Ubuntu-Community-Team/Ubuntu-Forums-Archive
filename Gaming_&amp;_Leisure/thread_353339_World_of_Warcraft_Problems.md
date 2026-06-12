---
title: "World of Warcraft Problems"
date: 2007-02-04
forum: Gaming &amp; Leisure
---

### Post by Zuph on 2007-02-04
Up to this point, my conversion to Linux has been entirely painless.  This one small problem is going to keep windows installed on my machine, though, which I don't like.

Following the excellent guides posted on this forum, I got WoW installed and updated with absolutely no problems.  After updating to 2.0.6, Sound stopped working, but the alsa-oss app fixed that problem.

My problem is as follows:  WoW starts up wonderfully.  There are no lag issues with the log-in UI, realm selection, character selection, any of that.  It works flawlessly.  As soon as I select a character and log in, it hard-locks my computer.  This seems to happen right before my own character model loads.

My computer:  Inspiron 6000 with ATI Radeon Mobility X300.  1.5 gig of ram, 2ghz Pentium M.
My install:  Ubuntu 6.06 with the fglrx drivers from the repositories.  Installed flawlessly using this guide:  [http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)
Wine 0.9.9 installed from the repositories.

Troubleshooting steps I have taken:
I have reinstalled the drivers countless times, I've modified the xorg.conf file with various modifications posted throughout the forums here.  I have tried running the game in D3D mode and it works with some graphical flaws, but it works for an indefinite period of time.  I have installed the registry patch.  Nothing has worked.

Important parts of the xorg.conf file:
Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
EndSection

I don't have the command line output from Wine because everything hard-locks when I try and run in OpenGL mode, so I'm not sure what errors are popping up.

Any information on this problem or how to troubleshoot it further is very appreciated.  I've dug through the past 4 months of posts here looking for a solution, and haven't found one yet.

---

### Post by Ferrat on 2007-02-04
Have you tried alt-tab to your terminal window just as you enter so you can see what is says when it locks?

---

### Post by Zuph on 2007-02-04
> **Ferrat said:**
> Have you tried alt-tab to your terminal window just as you enter so you can see what is says when it locks?

It shows this:

FATAL: fglX11CMMFreeSurface: firegl_FreeBuffer() failed!
FATAL: fglX11CMMFreeSurface: firegl_FreeBuffer() failed!
FATAL: fglX11CMMFreeSurface: firegl_FreeBuffer() failed!

---

### Post by Sammi on 2007-02-04
Have you seen this guide: [https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft) ?

You should try installing a never version of wine. Try the newest(0.9.30) first, then version 0.9.25 if the newest one doesn't work, as that version was considered pretty stable for WoW. You can find the debs here: [http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)

Or just use the repositories found in the guide.

---

### Post by Zuph on 2007-02-05
> **Sammi said:**
> Have you seen this guide: [https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft) ?

You should try installing a never version of wine. Try the newest(0.9.30) first, then version 0.9.25 if the newest one doesn't work, as that version was considered pretty stable for WoW. You can find the debs here: [http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)

Or just use the repositories found in the guide.

That was the guide I followed to the letter to install it originally.  Installing 0.9.30 from the repositories resulted in the problem as described above.

I just tried doing apt-get remove wine, then installing 0.9.25 from the .deb files from the site you linked, and this resulted in the exact same problem.

---

### Post by cdevilrun on 2007-02-05
Have you tried running it with just the open-source ATI drivers?

---

### Post by Zuph on 2007-02-05
> **cdevilrun said:**
> Have you tried running it with just the open-source ATI drivers?

Yes.  It ran so slowly that the game would have been unplayable, so I didn't bother trying to go further than the log-in screen.

---

### Post by Zuph on 2007-02-07
I think at this point I'm just going to give up at getting it to work.  For (hopefully) the benefit of anyone else unfortunate enough to have this problem, here are the steps I followed, exactly, for it not to work:

Install according to the guide posted in this thread.
Update everything.
Game runs at sub-1fps levels, unable to navigate menus, let alone try entering the world.  Solution:  Install fglrx drivers from repos.
After updating, sound stopped working.  Installed Also-oss package from Repos, sound starts working again.
Menus look fine, work fine.  Game freezes upon entering the world.
Try different fglrx drivers, no change.
Try different xorg.conf configs posted in easy-to-find topics in this forum, no change.
Try different versions of Wine, no change.
Give up hope of deleting windows partition.

---

### Post by Sammi on 2007-02-07
I know nothing about ATI drivers, but according to this page:
[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsAti](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsAti)

...Radeon Mobility doesn't support 3d :(

---

### Post by Elvish Legion on 2007-02-07
> **Sammi said:**
> I know nothing about ATI drivers, but according to this page:
[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsAti](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsAti)

...Radeon Mobility doesn't support 3d :(

*Sigh* my card isn't even listed (or on ati linux drivers)

Oh well, taxes come back soon, desktop with an nvidia card ftw!

---

### Post by Zuph on 2007-02-07
> **Sammi said:**
> I know nothing about ATI drivers, but according to this page:
[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsAti](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsAti)

...Radeon Mobility doesn't support 3d :(

According to ATI's site, the version I'm pulling from the repositories supports my 3D Card (Mobility X300 running the M22 chipset), so unless in the process of being put into the repositories functionality was removed, then it works.  The fact that Wolfenstein Enemy Territory worked without issue also tells me this.

---

### Post by T3h_Dohtem on 2007-03-05
same problems, same install/troubleshooting steps, same disappointment in ATI and my X300 card

before burning crusade came out I could play fine, but now I crash as soon as the world loads, sometimes on the loading (progress bar) page

ive spent days of my life crawling forums for a solution :/ anyone had any luck yet?

---

### Post by daller on 2007-03-08
See the great wiki-page on WoW: [https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

I have an issue with the 10-day trial thing!

Do I actually subscribe to a payment account afterwards? - $14 a month? - I just want to test the game! - No obligations!

---

### Post by Sammi on 2007-03-09
> **daller said:**
> See the great wiki-page on WoW: [https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

I have an issue with the 10-day trial thing!

Do I actually subscribe to a payment account afterwards? - $14 a month? - I just want to test the game! - No obligations!
There are no obligations if you sign up for the 10 day trial. You just have to cough up the 14$ if you want to keep playing after that.

---

### Post by Zuph on 2007-03-09
> **T3h_Dohtem said:**
> same problems, same install/troubleshooting steps, same disappointment in ATI and my X300 card

before burning crusade came out I could play fine, but now I crash as soon as the world loads, sometimes on the loading (progress bar) page

ive spent days of my life crawling forums for a solution :/ anyone had any luck yet?

My solution ended up being partitioning off a small bit of space and installing TinyXP, installing the firewall, and blocking every port EXCEPT the ones World of Warcraft uses.  This should keep the box reasonably pristine.

---

