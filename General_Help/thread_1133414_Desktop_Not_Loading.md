---
title: "Desktop Not Loading"
date: 2009-04-22
forum: General Help
---

### Post by TheWiseNoob on 2009-04-22
After using the command

```
sudo nvidia-settings -l && compiz --replace&
``` in jaunty, an error says compiz can't load, as well as the rest of my desktop. Could somebody help me with a way to fix/reverse this?

---

### Post by joeyknuccione on 2009-04-22
> **TheWiseNoob said:**
> After using the command

```
sudo nvidia-settings -l && compiz --replace&
``` in jaunty, an error says compiz can't load, as well as the rest of my desktop. Could somebody help me with a way to fix/reverse this?
If you have gnome, start in a prompt and type 

```

gdm

```
This should load the Gnome desktop, from there you can at least start looking into the problem.

or

```

sudo gedit /etc/X11/xorg.conf

```
And look in your xorg file for possible errors.

---

### Post by TheWiseNoob on 2009-04-22
Okay, let me clear this up. The desktop does load, in a way. The background loads, but nothing else other than an error telling me compiz didn't load. I am able to enter keyboard shortcuts, so I opened up terminal and loaded compiz and gnome-panel from there. Everything works fine from that point, but logging in, like I said, only brings me to the background. This is what I need help fixing. I can post my xorg.conf, if that helps.

---

### Post by TheWiseNoob on 2009-04-23
I still haven't figured out my problem.

---

