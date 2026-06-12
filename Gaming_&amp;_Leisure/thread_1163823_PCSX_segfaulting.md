---
title: "PCSX segfaulting"
date: 2009-05-19
forum: Gaming &amp; Leisure
---

### Post by Pixel on 2009-05-19
Well, I've been using pcsx without any problem for a few days, then overnight something happened and now I can't play anything anymore.

I've tried removing it via synaptic and deleting any files left over and reinstalling it, but it still segfaults.

Here's the log of it:

```
kyager@mobilebox:~$ pcsx
Checking plugin_is_available - libDFXVideo.so
Checking plugin_is_available - libDFSound.so
Checking plugin_is_available - libDFIso.so
Checking plugin_is_available - libDFInput.so
Checking plugin_is_available - libDFInput.so
  CDR: Setting CD file to 
Loading memory card /home/kyager/.pcsx/memcards/epsxe000.mcr
Loading memory card /home/kyager/.pcsx/memcards/card2.mcd

(<unknown>:25029): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(<unknown>:25029): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
Checking plugin_is_available - libDFXVideo.so
Checking plugin_is_available - libDFSound.so
Checking plugin_is_available - libDFIso.so
Checking plugin_is_available - libDFInput.so
Checking plugin_is_available - libDFInput.so
  CDR: Setting CD file to 
RGB not found.  Using YUV.
DFInput: starting thread...
DFInput warning: device already initialized.
Segmentation fault

```Running on 9.04 64bit.

It runs fine up until I go to actually load a game, then the segfault happens.

---

### Post by hikaricore on 2009-05-19
Did you install any updates on Ubuntu?

These things never happen for no reason.  Something has changed on your system.

---

### Post by Tested on 2009-06-10
I don't know much about Linux terms, as I've just made the jump from windows, but I installed PCSX from the app-get program that came with Ubuntu 9.04, and it runs fine, but for some reason, a minute or so into playing, it just turns off. Is that a segfault?

---

### Post by hikaricore on 2009-06-10
Run it from a terminal and find out.

---

