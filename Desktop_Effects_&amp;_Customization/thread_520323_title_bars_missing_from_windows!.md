---
title: "title bars missing from windows!"
date: 2007-08-08
forum: Desktop Effects &amp; Customization
---

### Post by Ins0mau on 2007-08-08
For eery application I now open, there is no longer a title bar above the menu bar. You know, that bar you use to drag windows around.

Also, many of the programs now seem to load at the very top left hand corner for some odd reason...

This is really weird.. :confused:

---

### Post by Vague on 2007-08-08
This is just a shot in the dark, but you haven't by any chance recently started using Beryl or Compiz, have you?

---

### Post by Ins0mau on 2007-08-08
> **Vague said:**
> This is just a shot in the dark, but you haven't by any chance recently started using Beryl or Compiz, have you?

Ah. Yes actually. Both.

I turned them off and it's all fixed.


Thanks heaps!!

---

### Post by Hospadar on 2007-08-08
If you want to keep using them, try using beryl (with beryl-manager running) and if you loose title bars or buttons, try reloading the window manager and/or decorator through beryl-manager (by right-clicking on the icon in the tray)  sometimes my windows don't load up properly and this generally straightens in out.

---

### Post by skymera on 2007-08-08
do u have emerald themes?

---

### Post by igknighted on 2007-08-08
If you have nvidia graphics, add this line to the screen section of your xorg.conf to fix this:
```
Option  "AddARGBGLXVisuals"  "true"
```

---

### Post by darell_m on 2007-08-08
> **Ins0mau said:**
> For eery application I now open, there is no longer a title bar above the menu bar. You know, that bar you use to drag windows around.

Also, many of the programs now seem to load at the very top left hand corner for some odd reason...

This is really weird.. :confused:

This has to do only wit Nivida
I had no borders and tried every forum advice, FAILED

At last gasp, I reloaded FF 7.04 clean.  from live disk

ThenI first of all download  ENVY  you can find it or look around -- simple

Then go to Compiz site and and download - magic all works great

I think if you mess with xorg ot xserver  you annot recover - gosh I tried

Bottom line - go for it = mine works with borders now an emeald.

Bye:)

---

### Post by gurubob on 2007-08-17
I don't think it's an nvidia only problem - I'm running an ATI X900 and I have this problem after installing Emerald.  Still getting my head around the config for it (and can't stop shaking those windows!) but hope to find the answer soon.  Certainly not considering a reinstall for the sake of this....

---

### Post by kraylus on 2007-08-17
compiz was workin great when i was usin whatever the devs setup as the default in "desktop effects".

then i decided to upgrade to the latest most badass version and it sorta worked. til i rebooted.

no more title bars, and all windows load from the top left. uninstalled, and put back the safe version that i assume was in apt-get. this one does the same thing now.

not sure wtf the deal is, but it seems that if somethings broke in linux it stays broke.

***edit***

as a side note, the option "desktop effects" is now removed from System>Preferences... anyone know how i can just restore that part back to the way it was when i installed? i miss the wobbly windows... desktop just isnt the same now.

---

### Post by 5h4rk on 2007-08-19
> **kraylus said:**
> compiz was workin great when i was usin whatever the devs setup as the default in "desktop effects".

then i decided to upgrade to the latest most badass version and it sorta worked. til i rebooted.

no more title bars, and all windows load from the top left. uninstalled, and put back the safe version that i assume was in apt-get. this one does the same thing now.

not sure wtf the deal is, but it seems that if somethings broke in linux it stays broke.

***edit***

as a side note, the option "desktop effects" is now removed from System>Preferences... anyone know how i can just restore that part back to the way it was when i installed? i miss the wobbly windows... desktop just isnt the same now.

I'm gettin exactly the same problem, just did an upgrade for CF, and title bar gone :( 

And when a do ctrl + alt + backspace, it get frozen... :(

---

### Post by zenrov on 2007-08-26
I'm having the same problem. Beryl was working just fine for the last several months. Last thing I was doing before it happened, was trying to install kiba-dock.  Everything was working fine until I restarted a day later. Now, title bar disappears, no animation, and can't switch between desktops when I get into beryl.  I removed kiba-dock and have tried reinstalling beryl but that didn't help. 

Another thing I noticed is that when I switch to beryl and try changing the emerald theme, the theme never changes.

Any suggestions?

Zenrov.

---

