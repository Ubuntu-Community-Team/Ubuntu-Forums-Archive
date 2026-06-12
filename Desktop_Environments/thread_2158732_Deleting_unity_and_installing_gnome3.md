---
title: "Deleting unity and installing gnome3"
date: 2013-06-30
forum: Desktop Environments
---

### Post by uSquad on 2013-06-30
Hi, would anyone help to delete unity and install gnome 3 desktop environment ? I found something on the net but that didn't worked for me. Thanks in advance.

---

### Post by vanadium on 2013-06-30
What did you try? Where did it not work?
Using ubuntu software center, you can install gnome shell. This is the easiest aproach to switch to gnome shell rather than Unity. Alternatively, you can do a clean install of the Ubuntu-gnome edition to end up with a pure gnome 3 system.

---

### Post by buzzingrobot on 2013-06-30
If you're on 13.04, the instructions here ([http://www.omgubuntu.co.uk/2013/04/gnome-3-8-ppa-for-ubuntu-gnome](http://www.omgubuntu.co.uk/2013/04/gnome-3-8-ppa-for-ubuntu-gnome)) worked fine for me.

I don't recommend trying to uninstall Unity.  Gnome Shell runs just fine without deleting it.   

Many, many dependencies hang off Unity. Those will vary based on what you may or may not have installed on top of the baseline system. That's probably why online howto's about removing Unity are so problematic.

---

### Post by cybergalvez on 2013-06-30
gnome 3 is in the standard repo, just install gnome, no need to remove unity, I don't care much for it, but its nice to have in case gnome3 get weird or some extension breaks your system.

---

### Post by markbl on 2013-07-01
You don't need instructions. Just "apt-get install gnome-shell" on a standard Ubuntu installation and then select GNOME (= GNOME 3, i.e. GNOME Shell), or Ubuntu (= Unity) at the login screen. Try each for a while and see which you prefer.

---

### Post by cybergalvez on 2013-07-01
on 13.04 I had to do apt-get install gnome

---

### Post by deadflowr on 2013-07-01
Whenever I want to install the gnome-desktops(because Ubuntu already runs all the gnome programs, as it's gnome based)
I install gnome-tweak-tool(In the menu system it'll be called advanced settings)
This installs the tweaker and the desktops.
If you want to go a step further, you can even install gdm and use it instead of lightdm.
[http://askubuntu.com/questions/152256/how-do-i-switch-from-lightdm-to-gdm](http://askubuntu.com/questions/152256/how-do-i-switch-from-lightdm-to-gdm)

Anyhoo, deleting unity can cause more problems than most people would want.
And the fact that it'll only be a dead program when not running will only make it the equivalent of the several other programs sitting on the system in similar states.

---

### Post by markbl on 2013-07-01
> **cybergalvez said:**
> on 13.04 I had to do apt-get install gnome

I don't see why you "had to" do that? That pulls in a lot more packages than you need for gnome shell. Just "apt-get install gnome-shell" should work.

---

