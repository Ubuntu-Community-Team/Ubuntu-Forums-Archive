---
title: "Screen shifted to the left after last update"
date: 2006-12-13
forum: Desktop Environments
---

### Post by jazzgossen on 2006-12-13
I installed a bunch of recommended updates this Monday on my laptop running Edgy. During the update process, the screen was suddenly shifted to the left, about 50 pixels, leaving a black bar on the right. The mouse pointer was still using the "real" screen coordinates, so I had to click 50 or so pixels to the right of where I wanted. The update had hanged around this point. So I restarted X (that solved the problem) and ran the update again. 

Everything was fine. Until just now, the same thing happened again, without me doing anything suspicious.

Has anyone else seen this? I have a Dell widescreen laptop using 1680x1050 resolution.

---

### Post by jazzgossen on 2006-12-14
I notice that this seems to happen once after every hibernation. Yesterday, it happened once. I restarted X and logged in again. I hibernated overnight. When I resumed this morning, it worked for a few minutes, just like yesterday, and then the screen suddenly shifted to the left again. If I continue working, the screen shifts furhter to the left after a few more minutes. 

I wish I could post a screenshot of this, but from the screenshot, everything looks normal. Right now, the leftmost part of the display is showing on the right edge of the screen. Then there's a black border, and the right edge of the display is approximetly 90-95% to the right. I'm guessing that it's shifted around 100 pixels to the left on a 1680 pixel wide screen.

Am I the only one with this problem? I'm running the nVidia 8776 driver from the official repos, on a GeForce4 4200 Go graphics card.

---

### Post by jazzgossen on 2006-12-15
Just to add some more information: I don't need to restart X to get the screen right after it has started to shift. Simply logging out and logging in again is enough to get the screen to look right, until the next time I resume from hibernation.

Among the packages that were upgraded when this happened were xorg and xserver-xorg (from 1:7.1.1ubuntu6 to 1:7.1.1ubuntu6.2). I'm guessing that the problem has to do with those packages. How can I downgrade to the previous version? 

It's annoying that apt doesn't have a mechanism for undoing an upgrade. I've had other problems with upgrades in the past that I couldn't solve without doing a clean reinstallation.

---

### Post by jazzgossen on 2006-12-20
I've noticed now that the problem doesn't seem to be related to hibernation after all. Instead, it seem to happen when the daily updatedb is run. 

There is a bug about this on [Launchpad]("https://bugs.launchpad.net/distros/ubuntu/+bug/75214"). Please post there, if anyone else is experiencing this.

---

