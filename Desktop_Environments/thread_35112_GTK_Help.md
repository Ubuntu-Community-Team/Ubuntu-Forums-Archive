---
title: "GTK Help"
date: 2005-05-17
forum: Desktop Environments
---

### Post by YaAqoB on 2005-05-17
Hello All. I'm very new to linux and I'm wondering if someone could please explain GTK to me. How do I install it or do I only have to install the GTK themes not the actual program?
What can it do?
etc etc.
Cheers

---

### Post by JonahRowley on 2005-05-17
GTK is the GUI toolkit that powers Gnome.  If you're using Gnome, you're already using it.

What exactly are you trying to do?

---

### Post by YaAqoB on 2005-05-17
Thank you. I was just looking at gnome-look.org and saw some very nice gtk themes and was wondering if it was like superkaramba where you had to install it first so it could manage the themes.
THanks heaps. :)

---

### Post by duff on 2005-05-17
If you want an program that makes it easy to download and install new themes, try [GNOME Art](http://www.miketech.net/gnome-art/).

---

### Post by YaAqoB on 2005-05-18
CHeers for that.
I have tried to install a theme and I get the following error.

checking for gtk+-2.0 >= 2.0.0... Package gtk+-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtk+-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtk+-2.0' found
configure: error: GTK+-2.0 is required to compile clearlooks-engine

Anyone have any clues?

---

### Post by tread on 2005-05-18
Download the theme you want from gnome-look.org onto the desktop, then start:

System->Preferences->Theme

from the top menu.
Drag the downloaded theme onto the theme manager window, and its installed. You can select it by clicking on "Theme Details"

---

### Post by YaAqoB on 2005-05-18
Thanks heaps for that :) When I manage to get Linux working again I'll do it. :)
I tried to install ruby and now when I log in it says that i have been logged in for less than 10 seconds and then kicks me. :(
THanks for your help though.

---

### Post by tread on 2005-05-18
np .. how did you try to install ruby?

---

### Post by YaAqoB on 2005-05-18
I went to the package manager and clicked Mark for install.
Half way through it just stalled and my desktop disappeared.
Now I can't boot into my login, only into root
I have tried deleting my account and creating a new one but still the same result.
I'll pasite the log roport when I can find it

---

### Post by tread on 2005-05-18
Ow .. that doesn't sound good! Log in as root on one terminal (you can get to a terminal by doing ctrl-alt-f1 from gdm) and type "tail -f /var/log/messages"

Then on another console (alt f2) try to login, and see if any error pops up in /var/log/messages.

---

### Post by YaAqoB on 2005-05-18
This is the error I get.

Warning unable to read ICE authority file: /home/james/.ICEauthority

I have look around and think this will fix it. I'll try when I get home and back to Ubuntu.
I did run k3b in root. :(
-------------------------------------------------------------------------------------
Are you sure it is corrupt and hot that the ovnership has been
changed? Have you recently run k3b as root (this will change the
ownership of this file)?

Try the following

Ctrl+alt+F1 to get a text console and log in.

ls -l .ICE*

Is the ovnership root? if so do

sudo chown _username_ .ICEauthority
sudo chgrp _username_ .ICEauthority

Ctrl+alt+F7 to go back to GDM

---

