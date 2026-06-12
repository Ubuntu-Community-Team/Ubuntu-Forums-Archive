---
title: "How I installed Ubuntu with Compiz using Gnome...Successfully.."
date: 2007-10-29
forum: Desktop Effects &amp; Customization
---

### Post by jonray74 on 2007-10-29
Hi everyone,

I finally was able to successfully install Compiz-Fusion using Gnome. I didn't know it was that easy. Anyways, I just wanted to share this.

1.) Install Ubuntu 7.10 CD
2.) Install Gnome
[I]sudo apt-get update 
sudo apt-get install ubuntu-desktop[/I]
3.)When installation is done, I did not reboot yet so I typed in the ff:
*sudo apt-get install dist-upgrade*
4.) Do a reboot.  When you login, just go to Synaptec and install CCSM or the (compizconfigsettings-manager) or do it in the command-line by typing *sudo apt-get install compizconfigsettings-manager*
5.) Open up CSSM, and select the effects you like. Close it, and then Open up your Desktop Settings and choose the last one in your Desktop Effects tab.

That should be it, I didn't have to do any Restricted drivers installation whatsoever since fglrx works well with Ubuntu 7.10, nor did I even touch my xorg.conf file. When Ubuntu Desktop installs, you will notice that the effects are already there, it's just a matter of installing the CCSM to add wobbly effects and all the rest and Cubes.

Anyways, this worked for me, personally and I have a Sapphire Radeon 9600 Pro 256Mb AGP card. Just easy breeezy installation.

Thanks,
John

---

### Post by boeing777 on 2007-11-01
my graphic card is ATI X1300, first installation, compiz didn't work.  Then a fresh installation, enabled restricted graphics card, and compiz didn't give me any error message.

---

### Post by jonray74 on 2007-11-02
i tried enabling the Restricted driver, but for some unknown reason, my session sometime freezes with that driver being on. 

So what I did, I just did a fresh install of Gutsy and Gnome. And since Gutsy comes with compiz installed, I just checked my Rendering by doing "glxinfo | grep rendering" and when it said Yes, I installed the CCSM, opened it up and enabled all the desktop effects. I Reboot, and after that it was already on, all the effects and all that. The thing I noticed though is that, when the ScreenSaver comes up, 3d rendering is very very slow, too slow that it just stops right there, but it doesn't crash my session.

I'm happy with my installation for now, as long as I can play all my favorite apps, play DVD, listen to music, see all the Compiz effects, no need to put the Restricted driver on.

:D

---

