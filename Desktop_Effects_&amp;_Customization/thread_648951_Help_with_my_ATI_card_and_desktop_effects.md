---
title: "Help with my ATI card and desktop effects"
date: 2007-12-24
forum: Desktop Effects &amp; Customization
---

### Post by snypercore on 2007-12-24
well im still new to linux so try and keep instructions simple :D

but i have an ATI radeon X1950 and i cant get any desktop effects, before i let ubuntu install restricted drivers i get a kinda "white screen of death" and after i install the restricted drivers i get "no composite extension" and ive tried quite a few guides that just end up screwing my ubuntu setup up, any ideas im dieing to have all the effects.

thanks

---

### Post by divague on 2007-12-24
you have to install sxerver-xgl to have effects with ati card and the driver that comes in the repos

---

### Post by Dark_X on 2007-12-24
> **divague said:**
> you have to install sxerver-xgl to have effects with ati card and the driver that comes in the repos

type this into the terminal.  You should have the restricted driver installed.
```
sudo apt-get install xserver-xgl
```
Then you will have to restart.

---

### Post by snypercore on 2007-12-24
wel thanks for the replies but i tried that and then restarted and still "no composite extension" any other ideas?

---

### Post by Dark_X on 2007-12-24
Are you using gutsy?

---

### Post by SyntheticXTC on 2007-12-24
snypercore, I do not think that the ati drivers support composite extention yet.  As soon as I get home from work I will link you to the How-To that I used.  I have the same video card in my pc that you are using.  I am just using the restricted drivers that Gutsy provided.

---

### Post by snypercore on 2007-12-24
thanks and no i am using feisty fawn

---

### Post by sYnOnYx on 2007-12-26
i am having the same problem now , and im running a radeon x1600 card.

---

### Post by Forlong on 2007-12-26
What's the output of ```
compiz
``` in a terminal?

---

### Post by snypercore on 2007-12-26
never mind i upgraded to 7.10 and now it works :D im happy

---

### Post by Casual Fan on 2007-12-26
The ATI drivers do support the composite extension, even the old ones available in the repos for Feisty. I'm running Feisty and Compiz fusion right now.

This thread might help:

[http://ubuntuforums.org/showthread.php?t=580748&highlight=ati+compiz](http://ubuntuforums.org/showthread.php?t=580748&highlight=ati+compiz)

There are lots of other threads on the forum that are similar if you do a search.

---

### Post by babil on 2007-12-26
not all ati cards are supported ... i have a dell latitude d610 with "radeon mobility x300" ... i tried installing xserver-xgl with latest drivers from ati ... doesn't work ... with xserver-xgl everything in X runs soo slow ... i could barely scroll down menus 'n webpages ... bad luck !

---

### Post by D_invictus on 2007-12-28
I'm on a Toshiba Sattelite, with an ati radeon as well, and I don't know how to update my driver.

---

### Post by D_invictus on 2007-12-28
Nevermind, the second method worked for me!
Thanks!

---

### Post by msdark on 2007-12-29
try with the latest ati driver from  official web site [www.ati.com](www.ati.com)

I have 2 pc.. in the desktop i hava a ati rade(on 9550 with these driver and i run compiz fusion very well (maybe sometime i have some cras h)...

and in the notebook i have a ati radone XPress1100.. and compiz fusion run good

These driver support AIGLX you don't need to disable the composite extension

just build the deb packages and install.


you need install before dkms linux-restricted-modules-$(uname -r) build-essential fakeroot dh-make devhelper

---

