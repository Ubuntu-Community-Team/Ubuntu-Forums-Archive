---
title: "Wayland with Enlightenment or any other WM ?"
date: 2017-09-03
forum: Desktop Environments
---

### Post by michael-z-freeman on 2017-09-03
Hi ):P,

Loving seeing Wayland working with Gnome. Or is it ? When I use "lg" to check window properties most show as "wayland", some are "x11" when wayland support is unavailable, but I was surprised to see "gnome-shell" show as X11. 

However I'm not a fan of Gnome. I read that Enlightenment has Wayland support however both it;s installation script for Ubuntu and the PPA does not start and it looks like it's trying to start with X11. Does anyone out there have Enlightement running on Wayland and how did you do it ? Build from source ?

What other WM's are out there that are functional with Wayland ? Anything. Cheers.

---

### Post by Frogs Hair on 2017-09-03
Looks like a work in progress.

[https://www.enlightenment.org/about-wayland](https://www.enlightenment.org/about-wayland)

---

### Post by michael-z-freeman on 2017-09-03
> **Frogs Hair said:**
> Looks like a work in progress.

[https://www.enlightenment.org/about-wayland](https://www.enlightenment.org/about-wayland)

From other messages I was seeing out there I got the impression that it was functional with Wayland, if not finished. But you could be right. I'll have to try some of the other WM's listed as Wayland compatible. It's great to see it working with Gnome but I feel stuck with it !

---

### Post by michael-z-freeman on 2017-09-04
There are actually a lot of WM's (or whatever we are supposed to call them now) out there ...

[http://way-cooler.org](http://way-cooler.org)

[https://liri.io/](https://liri.io/) (apparently included as part of this).

[https://i3wm.org/](https://i3wm.org/)

Many more and a lot of projects on Github but so far I've got none of them to work apart from Gnome.

Does anyone have anything working out there ? KDE ? Anything ?

In fact I'm going to try KDE now.

[U][B]EDIT:


[/B][/U]I just discovered that Way Cooler *is* working ! Just did not realise that it's a tiling WM which I'm not familiar with. It's based on i3 and "ALT -ENTER" opens a terminal - [https://i3wm.org/docs/userguide.html#_default_keybindings](https://i3wm.org/docs/userguide.html#_default_keybindings) so I'll see if the rest works from there.

---

### Post by Frogs Hair on 2017-09-04
I find a number of web hits for KDE plasma-workspace-wayland on Neon and Arch.

---

### Post by michael-z-freeman on 2017-09-04
Right. I just tried updating my Kubuntu desktop installation using a backports PPA but starting as Wayland led to a freeze and I had to hard reset.

_**EDIT:**_ I just found Gnome Flashback which could solve my problem..... I just need the environment I'm familiar with which is MATE (or any other traditional WM). It should work with Wayland because it's GTK3. AFAIK GTK3 adopted Wayland support early on, making any GTK3 based WM potentially compatible with Wayland. I looked at LXDE, actually LXQT but I think that's still in early development. I might try going back to Enlightement because I'm seeing reports that's its stable with Wayland. I only tried packaged binaries but have not tried building from source.

This seems to be best source of info so far as it lists supported toolkits: [https://wiki.debian.org/Wayland](https://wiki.debian.org/Wayland)

---

### Post by mc4man on 2017-09-04
Not important but curious - what do you mean by this?
> When I use [COLOR="#0000CD"]"lg" [/COLOR] to check window properties

---

### Post by michael-z-freeman on 2017-09-04
> **mc4man said:**
> Not important but curious - what do you mean by this?

This is a Gnome application for checking window properties. It was recommended as a way to show if apps are running Wayland native or through the "xwayland" wrapper (if that's the terms) for non wayland compatible applications. I was surprised to see Gnome-shell listed as running "X11" but I'm not sure what it means as I'm not familiar with Wayland and Gnome-shell.

---

### Post by michael-z-freeman on 2017-09-05
So has anyone built Enlightenment with Wayland support ? Currently having problems on how to add recommended wayland build options to autogen command line - [https://www.enlightenment.org/about-wayland](https://www.enlightenment.org/about-wayland)

I could really do with an in depth guide on how to do this and/or any help here. Determined to say my good byes to Xorg. Xorg, you served me well but your day is over !

[U][B]EDIT:

[/B][/U]So I tried Enlightenment again with the Niko2040 PAA and ***BINGO ! ***It works OK and appears to be running using Wayland. I don't know what happened the first time but I think I updated some libraries since I first tried it. There are some slight problems with losing keyboard focus with Chrome as well as loss of mouse pointer focus with applications using xwayland. But that's solved by ALT TABBING out and then back into the application in the case of Chrome. Xwayland apps are a little more tricky. But I'm seeing fixes for these problems in latest Enlightenment releases so will have to compile from source unless the PPA updates quickly. Cheers !

---

