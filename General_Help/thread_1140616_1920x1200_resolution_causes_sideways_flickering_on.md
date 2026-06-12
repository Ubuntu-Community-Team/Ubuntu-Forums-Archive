---
title: "1920x1200 resolution causes sideways flickering on intel graphics card"
date: 2009-04-27
forum: General Help
---

### Post by personjerry on 2009-04-27
I have an Intel factory installed graphics card, and when used it often causes some flickering (left/right one pixel or so, then back). I use it at 1920x1200 resolution, 60hz refresh, matchign my monitor exactly. The strange thing is the flickering stops after a while of computer usage, then randomly appears again. It also disappears after I switch the appearance options for visual effects (usually I choose none, but if I switch it fixes the flicker even if I switch back... at least for a while). I have an ATI x800 card but it crashes and often causes my computer to be unable to boot altogether, thus I usually just use my intel card. Any ideas how to fix this flicker?

Possibly related, Jaunty seems to have made games in Wine (at least the openGL ones) run much slower, such that my intel card which used to be adequate for Warcraft III under Hardy lags very much in Jaunty. In addition, even with my ATI card, the game lags for a second or so every few seconds and flickers all the time (normal flicker against background, even with compiz off). This lag does not always appear, occasionally I can start Warcraft III and never have it happen during the session.

---

### Post by Meow27 on 2009-04-28
i have the same problem, though its usually stimulated when i open up a window, a Wine application in particular.

im using an intel g915
1280x800 screen

---

### Post by personjerry on 2009-04-28
I think for me it also triggers similarly. Happens when I open firefox too, though. Lasts even after I close it though.

---

### Post by Meow27 on 2009-04-29
for me, i se quick morphs (boxes) coming in and out of the scree, like resizing the view. it only happends when i open and close apps in wine.

it hurts the eyes >_<

i can demonstrate if i had a desktop recorder than have 60+ fps

---

### Post by VastOne on 2009-04-29
> **personjerry said:**
> I think for me it also triggers similarly. Happens when I open firefox too, though. Lasts even after I close it though.

Having same issues as these but am not using any wine apps at all.  I too am at 1900 * 1200 60Hz using an ATI 3300 card

VastOne

---

### Post by personjerry on 2009-04-29
1900 * 1200? Perhaps you mean 1920 * 1200? Otherwise that may be the reason why...

---

### Post by personjerry on 2009-04-30
bump

---

### Post by personjerry on 2009-05-01
bump

---

### Post by personjerry on 2009-05-03
bump

---

### Post by personjerry on 2009-05-04
bump... kind a sad how most of my beans are from bumps

---

### Post by freonchill on 2009-05-04
i have a flicker on the lower left of my screen

dell insipiron 1150
intel p4m chipset (845?) with integrated video
1024x768 laptop LCD

especially aware of it when there is a window that has shades of grey or horizontal banding in that corner

---

### Post by VastOne on 2009-05-04
> **personjerry said:**
> 1900 * 1200? Perhaps you mean 1920 * 1200? Otherwise that may be the reason why...

yes 1920 * 1200

Disabled the ATI, enabled the nVidia, problem solved

---

### Post by personjerry on 2009-05-06
alas not everyone has an ATI and a nVidia card :/

---

### Post by personjerry on 2009-05-08
bump

---

### Post by personjerry on 2009-05-09
bump

---

### Post by AndThenWhat on 2009-05-09
Your problem if you are using Ubuntu Jaunty 9.04 may have to do with the new kernel's poor performance with Intel video cards.  
I have an Intel video card and I was getting choppy video so I changed to the newest kernel "2.6.30-020630rc4-generic" and I haven't had the problems.

---

### Post by personjerry on 2009-05-10
Any hints on how to do that?

---

### Post by personjerry on 2009-05-10
Nevermind. This is how I did it.
> echo 'deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic main restricted' | sudo tee -a /etc/apt/sources.list

sudo apt-get update

sudo apt-get install linux-generic

sudo gedit /etc/apt/sources.list # erase the last line

And there, installed the latest kernel.

---

### Post by zilu54 on 2009-05-13
same as mine...i already made a thread but still, no replies.
im using intel p4vmm2 (motherboard built-in graphic/video card)

please guys help me how to change it into 1024x720

---

### Post by personjerry on 2009-05-14
update your kernel and use it

---

