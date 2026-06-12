---
title: "Bluetooth turns XFCE into Gnome"
date: 2009-08-29
forum: Desktop Environments
---

### Post by HyperHacker on 2009-08-29
I've rediscovered an old problem: when I click "Browse files on device" in the Bluetooth applet, it launches Nautilus to do so - and that launches the full Gnome desktop replacing my XFCE desktop.

I had the same problem with 8.04 and 8.10, but there I found a workaround: going into desktop settings and unchecking and rechecking "let XFCE manage the desktop" would restart the XFCE desktop. However this option is no longer present in 9.04.

I later found a proper solution; a way to tell the Bluetooth applet to add the "--no-desktop" parameter to prevent Gnome taking over. However in this version I don't see any place to put that parameter.

What's the proper way to fix this in Xubuntu 9.04? Or is there a way to browse files on a Bluetooth device without bringing in all of Gnome?

---

