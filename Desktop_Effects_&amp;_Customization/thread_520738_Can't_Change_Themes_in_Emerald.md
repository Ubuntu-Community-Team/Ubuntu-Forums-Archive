---
title: "Can't Change Themes in Emerald"
date: 2007-08-08
forum: Desktop Effects &amp; Customization
---

### Post by Benzin on 2007-08-08
Hello,

I just did a fresh install of Ubuntu.  I have medium-low experience with Linux as a whole.  I installed Beryl and Emerald with Synaptic.  When I go to Emerald Theme Manager and click on a new theme, nothing happens.  I've tried clicking on a new theme then reloading window decorations with beryl-manager, it didn't work.  What gives?

Thanks guys.

---

### Post by gavin72 on 2007-08-08
When you right-click your beryl manager icon in the tray, and pick Select Window Manager, which one is selected ?

---

### Post by Benzin on 2007-08-08
> **gavin72 said:**
> When you right-click your beryl manager icon in the tray, and pick Select Window Manager, which one is selected ?

Beryl

---

### Post by gavin72 on 2007-08-08
Did you follow all of the instructions here ? (Depending on ATI or Nvidia).?

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#OpenCompositing:_Beryl_and_Compiz](http://ubuntuguide.org/wiki/Ubuntu:Feisty#OpenCompositing:_Beryl_and_Compiz)

(Not just a simple synaptic install)

---

### Post by Benzin on 2007-08-08
I have an nVidia 7900, I followed the directions on that site, it didn't help at all.

I don't have frames around my windows, I forgot to mention that, I have to move windows with <Alt>Left-click drag.

---

### Post by gavin72 on 2007-08-08
I'm not sure them. Perhaps someone with more experience in beryl can help ....

---

### Post by waldorsockbat on 2007-08-08
do you have it in sessions to load at start up?

---

### Post by Benzin on 2007-08-08
Yep.  Beryl is definitely loading (I can use the cube), I'm reasonably sure Emerald is (it's listed as a window decorator option).

---

### Post by waldorsockbat on 2007-08-08
Is Emerald Themes loading at start up?

If not then go to  SYSTEM>PREFERENCES>SESSIONS
in the start up programs if emerald is there make sure the box has a check in it

if not then ckick on NEW
name is emerals
commands is  emerald --replace
make sure the box by emerald themes has a check in it if not just click the box and Emerald will load at startup and you can apply themes.

---

### Post by psyopper on 2007-08-08
First try this:
```
gtk-window-decorator --replace
```
This will tell you if you are having window decoration issues or Emerald issues. Run it in a terminal and post the output.

If it fails you likely need to add something (or things) to your /etc/X11/xorg.conf

Most likely is that you are missing the following line in either your Screen or Device section depending on how your xorg is layed out:

```
    Option         "AddARGBGLXVisuals" "True"
```

Here's the complete device section for my Nvidia 6200:
```


Section "Device"
    Identifier     "PNY GeForce 6200"
    Driver         "nvidia"
    Option         "NvAGP" "2"
    Option         "AddARGBGLXRootClipping" "True"
    Option         "AddARGBGLXVisuals" "True"
    Option         "RenderAccel" "True"
    Option         "AllowGLXWithComposite" "True"
    Option         "backingstore" "True"
    Option         "TripleBuffer" "True"
    Option         "DisableGLXRootClipping" "True"
    Option         "AllowDDCCI" "True"

```

To edit the file:
```
sudo gedit /etc/X11/xorg.conf
```
You will DEFINITELY want to back up a copy of your xorg.conf before editing. If you copy and paste this DO NOT use my Identifier, use the Identifier already in your file.

To restart X and try any changes press [Ctrl]+[Alt]+[Backspace] on your keyboard.

I would start with the AddARGBGLXVisuals line only to see if your decorations start working. Try the others as time (and courage) permit.

---

