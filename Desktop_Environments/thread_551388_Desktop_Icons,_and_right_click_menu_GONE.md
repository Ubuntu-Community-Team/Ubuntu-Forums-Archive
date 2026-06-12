---
title: "Desktop Icons, and right click menu GONE"
date: 2007-09-15
forum: Desktop Environments
---

### Post by OotNAbootNewfie on 2007-09-15
Hi Guys!

I have read a few threads that pertain to this very problem however I am literally 24 hours new to Xubuntu, so the help that was given did not really make sense to me.

My right click menu has disappeared along with my desktop items.. in another thread they gave a code that I assume would fix it if typed/pasted into a terminal..but I can't open a terminal without the menu! ah catch-22.  I am so very woefully ignorant about Linux any (very detailed) help that can be offered would be very much appreciated.

-oot

---

### Post by dondad on 2007-09-16
If you can get to synaptic (system>administration>synaptic) try doing a search for nautilus. Click the box and mark it for removel. After it completes, find it again and reinstall it. After it completes, hit control-alt-backspace to restart x. This fixed the same problem for me.

---

### Post by mocoloco on 2007-09-16
You DON'T want to install nautilus, dondad probably missed the fact that you're using Xubuntu.  The program that controls your desktop icons and right-click is called thunar.  You can still bring up a run menu by pressing Ctrl+F2.  In that little run window type xfce4-terminal and press enter.  Now in the terminal you should be able to type thunar and see what output it gives you, which should explain why it won't run.
If it in fact doesn't run you can run synaptic and uninstall/reinstall thunar (At+F2, "gksudo synaptic").

---

