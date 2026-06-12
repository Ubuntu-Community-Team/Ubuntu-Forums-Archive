---
title: "no desktop effects on ubuntu 7.1"
date: 2007-10-21
forum: Desktop Effects &amp; Customization
---

### Post by nima352000 on 2007-10-21
i just installed ubuntu 7.1 and im trying to get some desktop effects (cube and beryl or some other cool stuff) when i click on system> preferences , there is no such a thing as desktop effect :| do i need to download any package for that ? if so how should i do that ?
im new to linux i dont know much about it.

---

### Post by FuturePilot on 2007-10-21
It's now under System>Preferences>Appearance. Go to the Special Effects tab

---

### Post by ReloadedFusion on 2007-10-21
Hi,

In Ubuntu 7.10 this has now been moved to the System->Preferences->Apperance applet simpy run this then click the Visual effects tab and click on extra. The cube will however need more setup a good guide on this can be found here:

[http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion](http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion)

Hope this helps

---

### Post by Toadmund on 2007-10-21
System>Preferences>Appearance>Visual effects>Extra

That will get compiz working, pretty neat!

No cube yet, don't think compiz has a cube, let me check...

Isn't beryl and compiz merged now, or somethin'?

---

### Post by arron on 2007-10-21
Ok, tryen this and I get "The Composite extension is not available" and defaults back to none when i try to select "Extra".  I have the restricted drivers installed, with an ATI 200M video card.

Can anyone help?

---

### Post by Toadmund on 2007-10-22
Put this into terminal:

sudo apt-get install xserver-xgl

Then try again.
From this post here:
[http://ubuntuforums.org/showthread.php?t=569654&highlight=compiz+cube]("http://ubuntuforums.org/showthread.php?t=569654&highlight=compiz+cube")

---

### Post by nima352000 on 2007-10-22
Thanks guys , i got it all to work :P
one thing i need to get some cool themes . i install emerald theme maneger and i download some themes package but when u install it it just changes the window frame color and style, how can i get a themes that changes icons and background and everything ?

---

