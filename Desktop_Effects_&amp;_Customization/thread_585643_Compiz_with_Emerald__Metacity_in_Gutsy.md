---
title: "Compiz with Emerald / Metacity in Gutsy"
date: 2007-10-21
forum: Desktop Effects &amp; Customization
---

### Post by Gerontius on 2007-10-21
Here is my problem:
If i have emerald installed, turning on desktop effects uses only emerald windows decorations. That's cool because there are many cool looking themes.
However... i use "Soffice" GTK theme ( available on [www.gnome-look.org](www.gnome-look.org) ) and it looks the best with "blended" windows decoration which is a Metacity decoration.

The only way i can use metacity decorations with Compiz is uninstalling emerald via synaptic :confused:
Is there a way i can choose which window decoration engine to use?

Thank you

---

### Post by Happy_Man on 2007-10-21
Install the compiz settings manager ```
sudo apt-get install compizconfig-settings-manager
```

It puts itself under Preferences, then all you have to do is go the Window Decoration settings and choose which one you want.

---

### Post by Gerontius on 2007-10-21
sorry... but that's not the case here
here's a screenie:

[IMG]http://img140.imageshack.us/img140/1658/screenshotcompizconfigssa8.png[/IMG]

i remember that in feisty i just used different command-line options to start compiz with or without emerald as a window decorator. i'd like to be able to do it in gutsy via GUI

---

### Post by Drone4four on 2007-10-21
I just installed compizconfig-settings-manager using apt-get as you instructed.  Now how do I start the app? What's the command?

---

### Post by ReloadedFusion on 2007-10-21
Gerontius

The command field on the picture you just posted is where you choose your window manager..

To use emerald simply add:

emerald --replace

Drone4four:

You can start the settings manager by typing ccsm in the terminal or it should appear under System->Preferences->Advanced Desktop settings

---

### Post by Gerontius on 2007-10-21
> **ReloadedFusion said:**
> Gerontius

The command field on the picture you just posted is where you choose your window manager..

To use emerald simply add:

emerald --replace


the problem is... when i have emerald installed... it's ALWAYS the window decorator

i'd like to use metacity's window decorations but keep all the effects

---

### Post by ReloadedFusion on 2007-10-21
Hi,

Try using this instead of metacity --replace

gtk-window-decorator --replace

This might not action straight away... I had to go ALT-F2 then type it in the run command first off. but after then switching between emerald --replace and gtk-window-decorator --replace in the ccsm worked on the fly

Hope this helps

---

### Post by chozoboy on 2007-10-21
you can use the [Fusion Icon]("http://tombuntu.com/index.php/2007/08/26/compiz-fusion-tray-icon/") to choose which window manager you use. it also gives you access to some other options for compiz fusion stuff.

---

### Post by ferrocene on 2007-10-21
Why isn't that icon isntalled by default?

I had Emerald running fine with Beryl, but now in Emerald I have only 4 themes, one is a theme I modified, two are the unmodified version, and one is the human-looking theme.  Where are the dozens of other themes in Emerald?

And if I don' tuse emerald, where are the Compiz-fusion themes?  GL Desktop does nothing when I run it, and gtk-window-decorator does nothing.

---

### Post by DanaG on 2007-10-21
If you don't want to remove Emerald, but don't want to use it, edit /usr/bin/compiz.  Look at around line 70:
# Use emerald by default if it exist
USE_EMERALD="yes"

Change that to 'no'.

---

### Post by Drone4four on 2007-10-21
> **ReloadedFusion said:**
> Hi,

Try using this instead of metacity --replace

gtk-window-decorator --replace

This might not action straight away... I had to go ALT-F2 then type it in the run command first off. but after then switching between emerald --replace and gtk-window-decorator --replace in the ccsm worked on the fly

Hope this helps

Right now beryl/emerald loads by default. How do I set gtk-window-decorator --replace to load at startup?

---

### Post by Gerontius on 2007-10-22
thank everyone for their help... i think i'll install the compiz tray applet

---

