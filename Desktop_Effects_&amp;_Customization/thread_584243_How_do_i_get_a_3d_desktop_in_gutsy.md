---
title: "How do i get a 3d desktop in gutsy?"
date: 2007-10-20
forum: Desktop Effects &amp; Customization
---

### Post by Soujiro Seta on 2007-10-20
Hey everyone. Its been several days since im running gutsy... And i clearly have achieved getting the "desktop effects", but i cannot customize the effects, make more desktops, make them cubical, etc. 

I used to have beryl, so i know how to get it done. I get a fast opening icon somewhere, right click on beryl symbol and get it totally customized, but thats not how it goes in here. There is no fast access buton, no way to customize nothing.

Heck, ive even tryed unistalling compiz, and trying reinstalling, but all i did was f*** compiz up and having to resintall ubuntu again. Ive also went googling the deal, but all i did was downloading unauthorized stuff that ruined my window manager, reinstalling ubuntu again.

Im really sick and tired, and want to get this done, i just need a link, a cmd, a guide something... Im already starting to think that all those people saying that compiz fusion came default in gusty, was a scum. I dont like to be fooled and being told that im getting 3d desktop by default and then seeing that i dont. 

So, i give one more chance to ubuntu, the last one, but if this is not what expected (a lot of people expected the same thing i am now...) i will go back to windows and/or gentoo (sabayon linux) where i am sure i will get the beryl and other stuff like that i have always desired.

---

### Post by NeoLithium on 2007-10-20
I'm not sure which turorials you used, though there's a section available here.
[https://help.ubuntu.com/community/CompositeManager/CompizFusion](https://help.ubuntu.com/community/CompositeManager/CompizFusion)

---

### Post by Soujiro Seta on 2007-10-20
If I'm not wrong that is for Feisty. I run gutsy.

---

### Post by Espreon on 2007-10-20
Enter this in a terminal:

```

sudo apt-get install compizconfig-settings-manager

```

Then goto: System>Preferences>Advance Desktop Effects Settings

Then u can configure CF.

---

### Post by Soujiro Seta on 2007-10-20
I get this as reply:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package compizconfig-settings-manager

```

---

### Post by Zalbor on 2007-10-20
You need to enable universe. The easiest way is to go to System>Administration>Software sources, and check the relevant box there. I'd recommend to check them all, it gives you the biggest choice of programs to install.

---

### Post by durand on 2007-10-20
You have to enable the extra repositories. Gnome Panel > System > Administration > Software Sources. Tick universe and multiverse. Then try that command again.

---

### Post by Soujiro Seta on 2007-10-20
Wow, this clearly makes a change, a lot of stuff downloading. Thanks.

---

