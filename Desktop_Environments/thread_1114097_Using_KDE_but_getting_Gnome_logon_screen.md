---
title: "Using KDE but getting Gnome logon screen"
date: 2009-04-02
forum: Desktop Environments
---

### Post by PedroRQ on 2009-04-02
Hi,

I've recently upgraded my Kubuntu 8.04 to 8.10 and I've been getting a strange behaviour on my logon screen.

Basically, when using Kubuntu 8.04, I used to get the normal KDE 3.5 logon screen. After the upgrade, I get the beige Ubuntu logon on screen instead (which I assume is the Gnome one).

After I log in, KDE 4.1 loads normally.

I tried going into the KDE system configuration to change the logon screen but to no avail: I always get the beige Ubuntu logon screen :-(

Can someone please help?

---

### Post by Giblet5 on 2009-04-02
Run:

sudo dpkg-reconfigure kdm

And select the kdm display manager.

You'll have to either reboot, or also run the following from text console (Ctrl-Alt-F1):
sudo /etc/init.d/gdm stop
sudo /etc/init.d/kdm start

---

### Post by PedroRQ on 2009-04-03
This worked! I had to stop gdm first, but then dpkg-reconfigure did the trick

Thanks!

---

