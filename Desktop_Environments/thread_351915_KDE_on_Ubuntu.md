---
title: "KDE on Ubuntu"
date: 2007-02-02
forum: Desktop Environments
---

### Post by erugalatha on 2007-02-02
Hey there,

when I started out on this linux journey I didn't know there was a choice of desktops so I just downloaded ubuntu and went with that.  

I'm wondering now is it possible that I could run both gnome and kde on my ubuntu installation and just choose which one I wish to use at boot or login?

At the moment it's gnome running but would like to have the choice without reinstalling my whole system again if possible.

Thanks for any help.

---

### Post by kebes on 2007-02-02
You sure can! (Don't you love Linux?)

To install KDE, just go into the Synaptic package manager (Applictions > Add/Remove) and search for "kubuntu-desktop" and install it. If you prefer, you can use a terminal and go:

sudo aptitude install kubuntu-desktop


Once that's done, you should get a choice at login time (assuming you have not enabled autologin), where you can pick the type of session you want. You can then switch between Gnome and KDE whenever you want, trying them both out.

Have fun!

---

### Post by LotsOfPhil on 2007-02-02
I think all you need to do is type:

sudo apt-get install kubuntu-desktop

and your wildest dreams will come true.

---

### Post by erugalatha on 2007-02-02
that's so sweet!! :) thanks a lot

---

### Post by Frem on 2007-02-02
Just FYI, the code in the first reply, the one that uses aptitude (sudo aptitude install kubuntu-desktop) is better. This is because KDE is a ton easier to remove later if you used aptitude instead of apt-get.

---

