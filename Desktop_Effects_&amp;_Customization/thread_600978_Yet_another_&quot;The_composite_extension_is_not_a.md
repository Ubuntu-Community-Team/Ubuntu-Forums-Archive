---
title: "Yet another &quot;The composite extension is not available&quot; when I try to enable effects."
date: 2007-11-02
forum: Desktop Effects &amp; Customization
---

### Post by SlaughterDog on 2007-11-02
Well as you can probably guess, I've got an ATI card, it's a X1900AiW. I'm using restricted drivers installed by the restricted drivers manager. When using them, I can't enable desktop effects because it says "The composite extension is not available". If I disable the restricted drivers from the restricted drivers manager, then I get a message saying "desktop effects could not be enabled" and the screensavers lag horrendusly.

---

### Post by dthomasdigital on 2007-11-03
I get the same thing with a ati x600 card

---

### Post by Forlong on 2007-11-04
> **SlaughterDog said:**
> Well as you can probably guess, I've got an ATI card, it's a X1900AiW. I'm using restricted drivers installed by the restricted drivers manager. When using them, I can't enable desktop effects because it says "The composite extension is not available". If I disable the restricted drivers from the restricted drivers manager, then I get a message saying "desktop effects could not be enabled" 
You _have_ to use the restricted driver with that card.
So enable them again and install Xgl:
```
sudo apt-get install xserver-xgl
```
> **dthomasdigital said:**
> I get the same thing with a ati x600 card
No, you could use the open radeon driver, if you want.
If you want to use the proprietary fglrx, you need to install Xgl as well.

---

### Post by SlaughterDog on 2007-11-06
What's xgl and why doesn't it come preinstalled?

---

### Post by smartboyathome on 2007-11-06
> **SlaughterDog said:**
> What's xgl and why doesn't it come preinstalled?

It basically provides you with most effects that compositing manager uses (in newbie terms).

In geek terms, visit Wikipedia: [http://en.wikipedia.org/wiki/XGL](http://en.wikipedia.org/wiki/XGL)

I don't think it comes pre-installed because not all graphic cards need it.

---

### Post by SlaughterDog on 2007-11-06
Thanks. I got it working and cranked up the special effects to extra. Rather nifty. Where's the place where I configure it all and figure out how to use the desktop cube?

---

### Post by Forlong on 2007-11-06
> **smartboyathome said:**
> I don't think it comes pre-installed because not all graphic cards need it.
Yes, only ATI users with the proprietary fglrx driver need it (which is about to change).
But the main reason why it's not preinstalled or a dependency of fglrx is that it's in universe (and it's a little buggy too).
> **SlaughterDog said:**
> Where's the place where I configure it all and figure out how to use the desktop cube?
See [here](http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion).

---

### Post by Lager_Monster on 2007-12-09
**Warning** if you have X600 and installing xserver-xgl

I run a HP nx8220 and xserver-xgl stops gnome after you login.
The fix is to select options (bottom left) and Gnome Safemode when you login
Uninstall xserver-xgl then restart, select Gnome (normal) on when logging in.

---

### Post by Pgi947 on 2007-12-15
Thanks installing XGL solved it for me using an ATi card. Works perfectly. Also love the fact that I no longer have to change sessions to use the visual effects....:-)

---

