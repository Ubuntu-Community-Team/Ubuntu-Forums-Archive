---
title: "XFCE Graphical Corruption Problems"
date: 2007-03-25
forum: Desktop Environments
---

### Post by Mr_Pag on 2007-03-25
Hi Forum, 

I've been having problems with a black box of garbled lines appearing in the top left hand corner when launching Xfce (4.4beta2). This is remedied by moving one of the desktop panels, although to actually physically move them is not required, just clicking the icon to do so removes the annoying graphical artifacts. I have not encountered this anywhere else on the forums

I installed Ubuntu 6.06 using instlux on to a Thinkpad X20. This particular machine has no CD-ROM or floppies, cannot boot from USB pendrives and the PXE is unfortunately knackered due to an ancient BIOS which I cannot upgrade due to the aforementioned lack of a floppy drive. Instlux was the only way to go at the time and I'm not sure how I'll reinstall the thing if it goes belly up.

However, after installing I upgraded to 6.10 pretty much immediately and then set about installing xubuntu-desktop via aptitude as the machine is pretty much lightweight by todays standards (P3-600, 192Mb RAM, 4Mb ATI mobility). I got the evolution-notify bug fixed and the only one outstanding is the annoying black box. Has anyone encountered this and have they been able to fix it? 

Thank you for your time.

Regards,

Alan

---

### Post by x1a4 on 2007-03-27
Hi,

Do you have compositing enabled?  I had this once and disabling then enabling compositing fixed it.  

Menu > Settings Manager > Window Manager Tweaks > Compositor

If this doesn't work see if resetting all Xfce settings will correct the problem.
To reset Xfce configuration remove the ~/.config/ directory

*mv ~/.config ~/.config.bkp*

and restart Xfce.

---

### Post by Mr_Pag on 2007-03-28
Hi there,

Thank you very much for your help x1a4. Your solution worked. Although I do not have compositing enabled, or available due to the ancient chipset in the laptop your second suggestion of resetting the XFCE config worked a treat. No more annoying black box.

Thank you!

Regards,

Alan

---

### Post by x1a4 on 2007-03-28
Glad I could help.  Since you still have the beta version of Xfce, you may want to upgrade to the latest release version of Xfce 4.4.

To do this, add the following repositories: 

[B]deb [http://ubuntu.tolero.org/](http://ubuntu.tolero.org/) edgy xfce-4-4-0 main
deb-src [http://ubuntu.tolero.org](http://ubuntu.tolero.org) edgy main[/B]

and reload your packages.  

If you're using *synaptic* or *apt-get* add the above repositories to _/etc/apt/sources.list_

then run: 

[I]sudo apt-get update
sudo apt-get upgrade[/I]

---

