---
title: "k3b - single click to select"
date: 2007-11-20
forum: Desktop Environments
---

### Post by tmryan on 2007-11-20
I'm using K3b in Gutsy, and can't get used to the "single click to open" method. But I can't find anything in the K3b settings to change it to "single click to select". Is there a way?

Thanks.

---

### Post by happysmileman on 2007-11-20
> **tmryan said:**
> I'm using K3b in Gutsy, and can't get used to the "single click to open" method. But I can't find anything in the K3b settings to change it to "single click to select". Is there a way?

Thanks.

The KDE desktop uses single clicks for most things, so it might be a setting in the KDE configurations, which could be hard/impossible to change while using GNOME.

---

### Post by adieb on 2007-11-20
hey.

you won´t find anything in the k3b-options. you have to change general kde option. you are using gnome? and you have just installed k3b?
with k3b there was installed a bunch of other kde stuff like libraries etc...

i am sorry but i don´t remember the name of kde system settings

---

### Post by happysmileman on 2007-11-20
> **adieb said:**
> i am sorry but i don´t remember the name of kde system settings

The command "kcontrol" should bring up the control center for me, but no idea whether it's installed when you install KDE apps on GNOME or whether it's only a full KDE install that will include it

---

### Post by tmryan on 2007-11-20
Thanks for the suggestions everyone! I tried to bring up Kcontrol, but looks like it didn't get installed along with K3b. I'll probably install it when I use more KDE apps.

---

### Post by smarf on 2008-01-02
Old, but after searching exactly for the same answer, the solution may be interesting to others: it's in
  ~/.kde/share/config/kcontrolrc
in section
  [KDE]
the entry
  SingleClick=false

Good luck!

---

### Post by HwyXingFrog on 2008-06-09
If you are running Ubuntu Desktop

sudo apt-get install kcontrol

then run kcontrol by typing it in the command line

Peripherals->Mouse->General

and then run K3b, I didn't even have to restart Gnome

---

