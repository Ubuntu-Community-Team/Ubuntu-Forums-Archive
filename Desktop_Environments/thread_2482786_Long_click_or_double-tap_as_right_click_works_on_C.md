---
title: "Long click or double-tap as right click works on Chrome but not on Lubuntu desktop"
date: 2023-01-10
forum: Desktop Environments
---

### Post by elastufka on 2023-01-10
I have Lubuntu 22.04.1 installed on a tablet. Therefore I want to use the touchscreen (no mouse, no touchpad)

I've tried touchegg for the double-tap = right cilck , and gsettings set org.gnome.desktop.a11y.mouse secondary-click-enabled "true"

A long click with either a stylus or finger brings up the right-click menu on Chrome, but on none of the Lubuntu desktop/task bar / start menu options. 

Any idea how this can be enabled? The gesture is clearly recognized (since Chrome follows the desired behavior) but not implemented by whatever is running the desktop GUI (LXQT I presume)

---

### Post by TheFu on 2023-01-10
Gnome is GTK+.
LXQt is Qt.

By changing the Gnome settings, you've probably made most Gnome/GTK+ toolkit programs work the way you like.  But you haven't told any Qt programs anything.  I don't know if there's a similar setting in Qt or not. Have you looked?

LUbuntu switched to Qt sometime in 2020, which means they've probably switched most of the pre-installed programs over the Qt versions as well.  That would explain why it doesn't work for most of your other programs.  You could test it by installing a small GTK+ editor.  Kate is based on Qt.  I'm 100% positive that geany is gtk+ based:
```
$ apt depends geany
geany
  Depends: libatk1.0-0 (>= 1.12.4)
  Depends: libc6 (>= 2.27)
  Depends: libcairo2 (>= 1.8.0)
  Depends: libgcc-s1 (>= 3.0)
  Depends: libgdk-pixbuf2.0-0 (>= 2.22.0)
  Depends: libglib2.0-0 (>= 2.41.1)
 ** Depends: libgtk-3-0 (>= 3.21.5)**
  Depends: libpango-1.0-0 (>= 1.20.0)
  Depends: libpangocairo-1.0-0 (>= 1.14.0)
  Depends: libstdc++6 (>= 5.2)
  Depends: geany-common (= 1.36-1build1)
  Breaks: geany-plugins-common (<< 0.21)
  Suggests: libvte9
  Suggests: doc-base
```
So, if you install geany and run it, try the mouse stuff and it works, you'll know.  There are probably smaller apps or apps already installed on your system. I just don't know Lubuntu under Qt.

The Gnome guys seem to be friendlier to non-desktop GUIs from what I've read. I don't know if that is true, but I have read more about it for Gnome GUI programs. 

With all that, I googled a bit and found this [https://github.com/eichenberger/qt-widgets-touch-translation](https://github.com/eichenberger/qt-widgets-touch-translation) which is listed as a workaround.
> This is only a proof of concept. Don't use it 1:1.
Not exactly confidence building.

---

### Post by ne29914 on 2023-01-10
Preferences -> LXQt Settings -> Keyboard and Mouse

---

### Post by guiverc on 2023-01-10
Lubuntu switched to LXQt & Qt5 with the Lubuntu 18.10 release  (*the very start of the two year 20.04 cycle*).

The manual page for what ne29914 suggested can be found here - [https://manual.lubuntu.me/lts/3/3.2/3.2.8/keyboard_and_mouse.html](https://manual.lubuntu.me/lts/3/3.2/3.2.8/keyboard_and_mouse.html)   (for Lubuntu 22.04 LTS).  I'd explore what ne29914 provided first.

FYI:  if you've upgraded your LXQt using the Lubuntu backports PPA; the *stable* manual (22.10's) will better match your system  (ie. change the LTS in the URL to STABLE)

---

### Post by TheFu on 2023-01-10
> **guiverc said:**
>  The manual page for what ne29914 suggested can be found here - [https://manual.lubuntu.me/lts/3/3.2/3.2.8/keyboard_and_mouse.html](https://manual.lubuntu.me/lts/3/3.2/3.2.8/keyboard_and_mouse.html)   (for Lubuntu 22.04 LTS).  I'd explore what ne29914 provided first.


I agree completely.  +1 - ignore me.

The reason I read this at all was because I've run Ubuntu-Mate on a tablet, but used a chroot and VNC to get it working.  Felt odd running a VNC client and a VNC server on the same physical hardware just to have a GUI.  Alas, for the time, it was impressive, but the hardware 10+ yrs ago struggled.  Today is probably a completely different situation. Interesting option, if the form-factor works for you.

---

### Post by elastufka on 2023-01-11
Thanks for the explanation! I only had a vague idea before about Gnome/KDE/LXQT and what they all meant, only that Lubuntu was a bit weird. At least I know now how to Google things better.

---

### Post by elastufka on 2023-01-11
Re: Preferences -> LXQt Settings -> Keyboard and Mouse 				

.... I think I would've found it if it was there. It's not.

---

