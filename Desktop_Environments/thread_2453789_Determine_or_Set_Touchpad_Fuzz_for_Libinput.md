---
title: "Determine or Set Touchpad Fuzz for Libinput"
date: 2020-11-17
forum: Desktop Environments
---

### Post by chrisgr99 on 2020-11-17
I'm new to Ubuntu, trying the most recent version booting from a USB stick, and I'm trying to find if I can reduce the hysteresis of the touchpad pointer.  

I found the ID of the touchpad with "xinput --list" but I can't figure out how to determine or set the touchpad fuzz factor. 

I found suggestions that the currently set value can be determined with "sudo libinput measure fuzz" and can be set with "sudo libinput measure fuzz --fuzz=8".
However these commands don't work in the Ubuntu terminal.  Is there a way to do this?

---

