---
title: "Different backlight levels: Unity vs Kde"
date: 2012-09-20
forum: Desktop Environments
---

### Post by humilleitor on 2012-09-20
I've come across a very intriguing issue regarding screen brightness, and I haven't found anything similar anywhere in any forum:

In my laptop (Toshiba with Intel graphics) I have four OS's in separate partitions:
1. the original Windows 7
2. Ubuntu 12.04 (Unity desktop)
3. Kubuntu 12.04 (Kde deskto, obviously)
4. OpenSUSE 12.2 (Kde).

When I change the screen backlight with the Fn+F6/Fn+F7 keys (standard in Toshiba), while in Windows or Ubuntu Unity, I can adjust the brightness in 20 different levels, which is great because I have a very accurate control of the precise light I need.

However, when doing the same thing in Kubuntu or OpenSUSE-Kde, I can only adjust the brightness in 10 different levels. How come?

As this brightness issue works differently in Kde and in Unity, I guess it is _not_ a distribution issue (*buntu vs Suse) but a desktop environment issue, Kde vs Gnome.

Now, does anybody know why this can be? What is Unity doing right that Kde is doing wrong? Is there any particular file where the brightness increase is set? Which one is that file? Which particular software is taking care of the increase?

A hint: when in Unity, in /sys/class/brightness there are two subdirectories: "intel_backlight" and "toshiba". In each of them there are (among others) two files called "actual_brightness" and "max_brightness". Every time I hit Fn+F6/Fn*F7, the corresponding values in the "intel_backlight" subdirectory change, but those in the "toshiba" subdirectory don't change.

Anyone can shed some (back)light on this? ;) My particular interest is to make Kde behave the same as Unity behaves. I mean: please don't offer me solutions of the type: "echo N > /some/file/in/the/sys/tree", nor "create a script with this or that content and associate it to a key". I just want 20 brightness levels controlled by the Fn+ keys in Kde, exactly the same as I have them in Unity. I must be darn easy; but of course I'd need to know which is the particular module or file where the brightness levels are set...

---

