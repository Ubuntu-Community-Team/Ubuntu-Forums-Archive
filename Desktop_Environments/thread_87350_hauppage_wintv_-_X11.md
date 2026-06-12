---
title: "hauppage wintv - X11"
date: 2005-11-07
forum: Desktop Environments
---

### Post by n_hendrick on 2005-11-07
I've just install ubuntu for the forth time thinking that I made an error somewhere in the install process, but to my dismay ubuntu will only run under the nv driver and not the nvidia driver. I didn't have this problem until I installed my wintv card. X will run just without 3d accelleration. Has anyone come across this problem under ubuntu before? I know the Tv card works because I use it under winxp and damn small (both of which work splendid). I'm just a little on edge about ubuntu not allowing me to run the nvidia driver and have a tv card installed for an X session. If anyone can think of a reason why I can't login to X, with the nvidia driver, under ubuntu 5.10 with my tv card installed, let me know. I guess I'm just gonna have to run Damn Small Linux now, didn't want to switch but I guess ubuntu just isn't ready for all the new gadgets I have on my pc. thanks in advance,
                                                               Nathan
ps the card is a 878 WinTV pci board and my video controller is a nvidia fx5700le

---

### Post by SickTwist on 2005-11-07
Could you please clarify which specific Hauppauge WinTV card is giving you trouble?

---

### Post by 91004 on 2005-11-07
I'm no expert in TV installations, however my card card is also a hauppage wintv card.  I installed Tvtime and it works fine

```
sudo apt-get install tvtime
```

---

### Post by n_hendrick on 2005-11-08
I can't log into X to install tvtime, weird that yours works fine, something with the nvidia driver is all messed up.

---

### Post by Stereotypical Rage on 2005-11-08
[QUOTE=n_hendrick]I can't log into X to install tvtime, weird that yours works fine, something with the nvidia driver is all messed up.[/QUOTE]
You don't need X installed to get to the bash prompt. Hit CTRL+ALT+F2, you'll then be thrown out of X or whatever and into a console.

If you know your way around the command line, you'll be fine. At this time you may want to re-install the nVidia driver as well. Sometimes it can use a swift kick in the rear.

---

### Post by poptones on 2005-11-08
I have an nvidia nf2 motherboard and my five year old hauppauge wintv pci card (still!) works like a champ. (Been almost a decade now since I bought a tv...)

You don't happen to have a via motherboard, do you? Sometimes they don't behave with tv cards and sound cards...

---

### Post by n_hendrick on 2005-11-09
Figured out what messed up ubuntu....I was running the 386 kernel and not the k7 kernel, I'm not sure why this made the difference in letting me log into X but for some reason all is good now.

---

### Post by poptones on 2005-11-10
Ahhh.. because somewhere along the line you "upgraded" to a k7 kernel which also "upgraded" you to an X11 system compiled for that new kernel. If X ain't linked with the proper kernel, ain't gonna happen.

---

