---
title: "How go I replace openbox with metacity in LXDE?"
date: 2008-05-17
forum: Desktop Environments
---

### Post by NULL712 on 2008-05-17
I am working on a school project at C-Tech. I need to have ubuntu instaled on alder computers with a light DE. I found LXDE and it's perfect for what I need to do. But openbox is to complicated. You see these computer are going to people that need them, and I want to keep every thing basic and simple with out buying new hardware. I would like to usu metacity insted of openbox, but I have no idea how to do the swich.

Have any ideas? 

Thanx 
Craig.

---

### Post by PCMan on 2008-05-18
> **NULL712 said:**
> I am working on a school project at C-Tech. I need to have ubuntu instaled on alder computers with a light DE. I found LXDE and it's perfect for what I need to do. But openbox is to complicated. You see these computer are going to people that need them, and I want to keep every thing basic and simple with out buying new hardware. I would like to usu metacity insted of openbox, but I have no idea how to do the swich.

Have any ideas? 

Thanx 
Craig.

If you are using lxsession, edit /etc/xdg/lxsession/LXDE/default.
Replace openbox with metacity. That's all. (Of course you need to install metacity.)
If you are using lxsession-lite, edit /etc/xdg/lxsession/LXDE/config. Then, replace openbox-lxde with metacity and it's done.
Very easy. This should to be well-documented, though.
We already set up a wiki. So there will be better documentation in the future, I guess.

Good luck!

---

### Post by NULL712 on 2008-05-26
Thanx for the reply I will do that I am using LXSession ot LXSession-Light. Thanx for the help i get it a sorted out know that i know what to do. :)

---

### Post by PCMan on 2008-05-27
> **NULL712 said:**
> Thanx for the reply I will do that I am using LXSession ot LXSession-Light. Thanx for the help i get it a sorted out know that i know what to do. :)
LXDE comes with a set of sensible default config for openbox.
So, normally you don't need manual configuration.
Otherwise, you can install obconf, which is a GUI config tool for openbox.
If you just want to modify its looks & feels, or the behavior, there is 
no need to edit the complicated xml config files.

Metacity, IMHO, is not simpler since its config is done through 
editing config values via gconf-editor unless you're using gnome
where there is some sort of (not very useful) GUI config tool with 
few options.

Of course, metacity will work well with other components of LXDE.
It's tested on my own machine previously.

---

### Post by NULL712 on 2008-05-27
I understamd what your getting at but I am comfortable with metacity. I not saying openbox isn't great, I just need some time to get use to it. But more impartantly I hvae issues with lxsesion. When I click the logout buton lxpanel dies and nautlus & metacity stay running. I don't even get a dialog asking what I would like to do. Ex. logout reboot ect... And also I have to start metacity and nautilus manuely every time. any ideas?

Thanx alot 

Linux just flat out rules. Even it's errors keep me intertained! :lolflag:

---

### Post by scottro on 2008-12-18
I realize this is an old thread, but I've been looking all over for the files to do this.  I don't see the little medallion at the lower right to give thanks to PCMan, but if I could find it, I would certainly click on it.  (I haven't frequented these forums for awhile, so perhaps the method of thanking has changed.)

---

