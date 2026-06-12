---
title: "I forgot a couple of commands. Anybody know them?"
date: 2013-05-26
forum: Desktop Environments
---

### Post by Moose on 2013-05-26
So like, I installed Ubuntu 13.04 with Gnome 3.4. And I remember a while ago I read on this website that there are two very useful commands for terminal. One of them downloads and installs all of the popular Gnome themes, and one that installs all of the add-ons. I forgot these commands and I would like to know, does anybody know what they are? I love to customise Ubuntu and these commands would give me a massive shortcut.

---

### Post by Frogs Hair on 2013-05-26
It reads like your'e describing a themes ppa and there are different ones available. I don't know what is meant by add-ons though and so you install compatible themes 13.04 uses Gnome 3.6 themes.  [http://www.noobslab.com/2011/11/themes-collection-for-ubuntu-1110-unity.html](http://www.noobslab.com/2011/11/themes-collection-for-ubuntu-1110-unity.html)

For audio codecs and flash player install the ubuntu restricted extras package from the software center.=

```
sudo apt-get ubuntu-restricted-extras
```

---

### Post by Moose on 2013-05-26
No, they were two specific commands that downloaded themes and add-ons that can be changed with the gnome tweak tool. It was specifically for Gnome shell. It automatically downloaded them and put them in the .themes folder.

---

### Post by Frogs Hair on 2013-05-26
There are such commands and themes available from various sites but you have some idea of what themes you installed because the web is a big place. Add-ons for what ?

PPAs install themes that can be changed from the Tweak Tool also.

---

### Post by Moose on 2013-05-26
Add-ons for the Gnome shell! u.u
This is the easiest I can explain it:
One command downloads and installs a whole bunch of Gnome shell themes automatically.
One command downloads and installs a whole bunch of Gnome shell extensions.
I can't explain that easier.

---

### Post by Frogs Hair on 2013-05-26
13.04 has a good number of extensions in the Ubuntu software center . 

```
sudo apt-get install-gnome-shell-extensions 
```

After running the command open the Tweak Tool and enable the ones you want. 

I can't help with the themes unless you know the source because the  Ubuntu repository only supplies the official default themes. Installation instructions often change from one release to another so knowing the name of some of the themes you had will help  . I have about 40 themes installed from different sources. 

Additional Extensions:   [https://extensions.gnome.org/](https://extensions.gnome.org/)

---

### Post by Moose on 2013-05-26
THAT'S IT! Thank so much man! The command for the themes is basically the same. Thank you man! &#9829;

---

### Post by Frogs Hair on 2013-05-26
Your'e Welcome 

If you can come up with a name of at least one of themes I might be able to help with that.

---

### Post by Moose on 2013-05-27
The last time I used Gnome it was about a year ago.. I can't remember s**t dude ahaha. I think one of the themes was Gaia?

---

### Post by Frogs Hair on 2013-05-27
That theme won't work properly with with gnome 3.6 on 13.04 . so, you may to check out some newer themes, The source for the themes you used is likely obsolete on your current version.

---

