---
title: "Appearance settings reverting by themselves"
date: 2011-03-17
forum: Desktop Environments
---

### Post by poldie on 2011-03-17
I've got Ubuntu 10.04 64 bit on my Dell laptop, and on my Appearance/visual effects tab I've selected None.  But when I reboot, it changes by itself to Normal.    How can I make it stay on None?

Edit:  I just created another user on this pc.  After reboot it stays on None for this user, suggesting it's a per-user setting I need to fix, not a system wide one.

---

### Post by Krytarik on 2011-03-17
Although it is odd that those setting gets reverted on re-login, those are the possible easy workarounds:

- If you want to remove Compiz (which handles those desktop effects) completely, purge it and any associated packages with Synaptic.

- If you want to just disable it, try this:

Run those commands in a terminal:
```
gconftool-2 --type=string --set /desktop/gnome/applications/window_manager/current /usr/bin/metacity
gconftool-2 --type=string --set /desktop/gnome/applications/window_manager/default /usr/bin/metacity

```The setting for Compiz is "/usr/bin/compiz".

---

### Post by poldie on 2011-03-21
> **Krytarik said:**
> Although it is odd that those setting gets reverted on re-login, those are the possible easy workarounds:

- If you want to remove Compiz (which handles those desktop effects) completely, purge it and any associated packages with Synaptic.

- If you want to just disable it, try this:

Run those commands in a terminal:
```
gconftool-2 --type=string --set /desktop/gnome/applications/window_manager/current /usr/bin/metacity
gconftool-2 --type=string --set /desktop/gnome/applications/window_manager/default /usr/bin/metacity

```The setting for Compiz is "/usr/bin/compiz".


Hmm.  I did that (ie used synaptic to uninstall all compiz related apps) and I lost my title bars.  Also, only one window would accept keyboard input.   For example, I googled for 'missing title bar' and saw results saying to type this or that into terminal, but I could type nothing into terminal.   Additionally, most of the missing title bar help involved using compiz to change settings; that's clearly not going to work if I don't actually have compiz installed!

It's as if something is trying to load/run Compiz when I boot up (or login, perhaps), and if it's not there it chooses a crap setting (ie not the setting I had before I removed Compiz and rebooted, because at that point it's fine).

You seem to understand this pretty well - could you suggest/recommend another way of solving this please?

---

### Post by Krytarik on 2011-03-21
> **poldie said:**
> Hmm.  I did that (ie used synaptic to uninstall all compiz related apps) and I lost my title bars.  Also, only one window would accept keyboard input.   For example, I googled for 'missing title bar' and saw results saying to type this or that into terminal, but I could type nothing into terminal.   Additionally, most of the missing title bar help involved using compiz to change settings; that's clearly not going to work if I don't actually have compiz installed!

It's as if something is trying to load/run Compiz when I boot up (or login, perhaps), and if it's not there it chooses a crap setting (ie not the setting I had before I removed Compiz and rebooted, because at that point it's fine).

It's weird that it behaves as such, are you using the "Netbook Edition"?

The removal of Compiz only comes into effect after you re-login.

As I saw the edit of your OP, did you try the commands I stated?

---

### Post by poldie on 2011-03-21
> **Krytarik said:**
> It's weird that it behaves as such, are you using the "Netbook Edition"?

The removal of Compiz only comes into effect after you re-login.

As I saw the edit of your OP, did you try the commands I stated?

I tried uninstalling compiz completely; I didn't try the disable commands as I want it gone!

I have the regular install, as the laptop is reasonably powerful (with 4 gigs of ram, which is part of the reason I went for the 64bit version).

I've posted elsewhere and someone told me to get the compiz fusion icon, and use another window manager.  I've tried this, and it seems to have sort of done the trick, in that I can get windows to open/close immediately without zooming in/fading etc, but all 3 options in the Appearance dialog are empty now.   It just seems a bit strange that, once compiz is installed, you have to use a compiz add-on to persist an attempt to turn it off.    What was the default window manager before I started fiddling?  Can't I just go back to that, and have "none" selected?   I've spent a bit of time looking for anything which could be loading compiz files (it in /etc/modules or whatever) but I can't see anything.

---

### Post by Krytarik on 2011-03-21
> **poldie said:**
> 
I've posted elsewhere and someone told me to get the compiz fusion icon, and use another window manager.  I've tried this, and it seems to have sort of done the trick, in that I can get windows to open/close immediately without zooming in/fading etc, but all 3 options in the Appearance dialog are empty now.
First, you don't need Compiz Fusion Icon to disable Compiz. Which window manager are you running currently?
> **poldie said:**
> 
What was the default window manager before I started fiddling?
The default window manager is "Metacity".
> **poldie said:**
> Can't I just go back to that, and have "none" selected?   I've spent a bit of time looking for anything which could be loading compiz files (it in /etc/modules or whatever) but I can't see anything.
That is exactly what the mentioned commands would do, switch back to Metacity.

---

