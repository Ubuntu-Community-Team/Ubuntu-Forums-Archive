---
title: "Using GTK CSD/headerbars"
date: 2016-04-22
forum: Desktop Environments
---

### Post by MarkBauer on 2016-04-22
I've recently started engaging in GTK3 development and would like to equip my small app with headerbars for use outside of Ubuntu/Unity.
Unfortunately, I can't seem to get them to work anywhere in Ubuntu 16.04. No matter whether I actually use Unity or not.

The headerbar itself shows up and the file menu even works, but I'm unable to drag the window itself. This is true no matter if I run the app inside Unity or fvwm.

Is there anything that needs to be switched on in order to be able to use client side decorations inside Ubuntu 16.04?

---

### Post by vasa1 on 2016-04-23
> **MarkBauer said:**
> I've recently started engaging in GTK3 development and would like to equip my small app with headerbars for use outside of Ubuntu/Unity.
Unfortunately, I can't seem to get them to work anywhere in Ubuntu 16.04. No matter whether I actually use Unity or not.

The headerbar itself shows up and the file menu even works, but I'm unable to drag the window itself. This is true no matter if I run the app inside Unity or fvwm.

Is there anything that needs to be switched on in order to be able to use client side decorations inside Ubuntu 16.04?

Have you looked at Ubuntu MATE? According to [this]("http://www.omgubuntu.co.uk/2016/03/ubuntu-mate-16-04-client-side-decoration"), the dev has all bases covered.

One other long shot is to try some other theme making sure it's written for gtk 3.18 and not lower or higher. gtk 3.20 is breaking quite a few themes currently ;)

---

### Post by MarkBauer on 2016-04-23
I found out that the place to switch GTK themes outside of Unity is > ~[COLOR=#333333][FONT=sans-serif] /.config/gtk-3.0/ settings.ini[/FONT][/COLOR][COLOR=#333333][FONT=sans-serif]
Putting  [/FONT][/COLOR]> gtk-theme-name = paper[COLOR=#333333][FONT=sans-serif] i[/FONT][/COLOR][COLOR=#333333][FONT=sans-serif]n there fixed the broken theme inside fvwm (Ambiance looked kind of broken to me).

Unfortunately, while I'm now able to properly move GTK3 CSD apps like the Gnome Tweak Tool, my own UI remains static. I suppose I need to read up on header bars and figure out what is missing from my code.[/FONT][/COLOR]

---

