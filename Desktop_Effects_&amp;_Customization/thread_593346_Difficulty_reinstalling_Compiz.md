---
title: "Difficulty reinstalling Compiz"
date: 2007-10-27
forum: Desktop Effects &amp; Customization
---

### Post by QuacoreZX on 2007-10-27
I used this guide to try and upgrade to Compiz Fusion 0.6.0 / Compiz 0.6.2 ( [http://phorolinux.com/how-to-install-compiz-fusion-060-from-sources-on-ubuntu-710-gutsy-gibbon.html](http://phorolinux.com/how-to-install-compiz-fusion-060-from-sources-on-ubuntu-710-gutsy-gibbon.html) ), but I got some big troubles as I can't get titlebars to reappear now without running "metacity --replace".  I used "sudo make uninstall" in each of the folders of the sources I compiled / make installed, and then completely uninstalled via synaptics for all compiz related packages, then reinstalled, and I still can't get it to work when I run "compiz --replace".  Anyone have any ideas? x_x

---

### Post by QuacoreZX on 2007-10-29
bump...

---

### Post by rundee_f on 2007-10-29
r u using emerald or only gtk-window decorator? have u installed ccsm?

---

### Post by QuacoreZX on 2007-10-29
I tried using both gtk-window-decorator and emerald, and CCSM is installed.  Still nothing.

---

### Post by justsomedude on 2007-10-29
Sorry to ask, but I'm not sure if I understand your problem correctly: Do you have trouble running compiz at all or do you just have problems getting the window decorations to show up?

---

### Post by QuacoreZX on 2007-10-29
Compiz runs fine, I believe.  My problem is really in the fact I have no title bars (and therefore probably a decorator issue).

---

### Post by justsomedude on 2007-10-30
Ok, open CCSM, find *Window Decoration* (make sure it's enabled), and add 

```
gtk-window-decorator
```

under *Command*. Then start Compiz and see if your decorations are back.

If you got an Nvidia card you could also try 

```
sudo nvidia-xconfig --add-argb-glx-visuals -d 24
```

Sometimes, CCSM doesn't remember settings so check for "Window Decorations" again if it doesn't work.


> **QuacoreZX said:**
> Compiz runs fine, I believe.

What do you mean by "I believe"? Do any of the key combinations work? If not, could you post the terminal output of

```
compiz --replace
```

?

It might be he complains about /usr/local/bin/compiz missing or something...

---

### Post by QuacoreZX on 2007-10-30
Oh well, it's alright now.  I didn't have much installed on Ubuntu, so I did a clean reformat. Thanks for the help though!

---

