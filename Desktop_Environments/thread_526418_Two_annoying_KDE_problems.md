---
title: "Two annoying KDE problems"
date: 2007-08-15
forum: Desktop Environments
---

### Post by Zalbor on 2007-08-15
I just installed KDE, I only had GNOME before. Maybe I'll switch to KDE, so I wanted to try it.
Right now it seems fine, but there are two things that are very annoying:
1)I want to have only one desktop (because I'm running compiz, so there are 4 viewports anyway). So I keep setting the amount of desktops to 1, but whenever I log in again it's suddenly set to 4, which because of compiz makes 16 squares appear on the taskbar. It also happens randomly sometimes, when I'm logged in. Can't it be 1 permanently?
2)I don't want the icons for mounted devices on my desktop, and I've set it so that they won't appear. And they still do.

Are these bugs in KDE? I hope not, because I'd want to switch to KDE but especially 1 is very annoying.

---

### Post by luisromangz on 2007-08-15
Umm, I have 4 viewports in KDE and 4 in Compiz. Try setting "horizontal virtual desktops" (or whatever is called in English, I'm seeing the spanish translation) to 4 and "number of desktops" to 1 in Compiz Settings Manager.

I have compiz that way and I don't have problems.

About the drives, don't know if it is a bug.

---

### Post by Zalbor on 2007-08-15
> **luisromangz said:**
> Umm, I have 4 viewports in KDE and 4 in Compiz. Try setting "horizontal virtual desktops" (or whatever is called in English, I'm seeing the spanish translation) to 4 and "number of desktops" to 1 in Compiz Settings Manager.
That's what I keep doing, but it goes back to 4 as well.

---

### Post by miggols99 on 2007-08-15
You can disable the drives by doing this (if you haven't already):

Right click desktop >> Configure Desktop >> Behaviour >> Tab: Device icons >> Untick "Show Device Icons"

---

### Post by GeneralZod on 2007-08-15
> **Zalbor said:**
> That's what I keep doing, but it goes back to 4 as well.

I've heard that KDE and Compiz don't always work well together (never tried it myself).

Look in ~/.kde/share/config/kwinrc; there should be a [Desktops] entry, with the desktops you have configured and a "Number=" line.  What does this say?

---

### Post by Zalbor on 2007-08-15
> **miggols99 said:**
> You can disable the drives by doing this (if you haven't already):

Right click desktop >> Configure Desktop >> Behaviour >> Tab: Device icons >> Untick "Show Device Icons"
I said I did that already. That problem solved itself apparently though, without me doing something about it.

---

