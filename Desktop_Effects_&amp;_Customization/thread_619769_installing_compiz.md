---
title: "installing compiz"
date: 2007-11-21
forum: Desktop Effects &amp; Customization
---

### Post by btownsox13 on 2007-11-21
I need full step by step for installing Compiz on gusty with an ATI card
THNX

---

### Post by Afkpuz on 2007-11-21
Goto System>Administration>Restricted Driver Manager

Check the box by "ATI accelerated graphics driver"

After that installs, goto System>Administration>Synaptic Package Manager

Search for "xgl"

Install "xserver-xgl" and "gnome-compiz-manager"

Reboot

Now, System>Preferences>Appearance

Goto the effects tab.  Select "Custom". Compiz should work now.  
System>Preferences>Advanced Dektop Effects is where you can change effects settings

---

### Post by patryk77 on 2007-11-22
That's a good way to break 3d rendering with ATI cards.

After installing the restricted drivers, don't install "xserver-xgl"

install the compiz packages (along with the gnome manager), and the emerald themes.

Just do a search for "compiz" and "emerald" in synaptic, that'll take care of what you need.

---

### Post by Forlong on 2007-11-22
> **btownsox13 said:**
> I need full step by step for installing Compiz on gusty with an ATI card
What card exactly?
> **patryk77 said:**
> After installing the restricted drivers, don't install "xserver-xgl"
Then you wouldn't be able to use Compiz.

---

### Post by psyopper on 2007-11-22
I'm not an ATI guy but I thought the new ATI drivers had fglrx integrated which would mean not needing the xgl layer.

But I may be wrong.

---

