---
title: "key remapping and shortcuts in GNOME"
date: 2009-07-21
forum: Desktop Environments
---

### Post by nexus_2006 on 2009-07-21
I would like to setup a shortcut key to toggle the touchpad on and off on my laptop.  I like the scrolling, but when I'm typing I'm constantly bumping the pad with the heel of my hand, causing the cursor to jump and all sorts of bad things to happen.  Any way to do this easily (i.e. without going into the keyboard config menu every time)?

---

### Post by nexus_2006 on 2009-07-22
Anyone know what commands the applet uses to turn the pad on and off?  Or is there a way to monitor the applet to find out how it does it?  I could probably cobble together a script and hotkey it if I knew what the commands were...

---

### Post by nexus_2006 on 2009-07-23
*sad, sorry, shameless bump*

---

### Post by Dullstar on 2009-07-23
I'd help you if I could.  Honestly, you appear to get the same problem as I do every time I use a laptop!

---

### Post by decomp on 2009-08-15
Well I can't help with a keyboard shortcut but I dealt with the annoying touchpad issue with this script I found as an answer to someone elses question about it.. I wish I could remember who provided the answer to give credit :( Anyways:

1. go to system > preferences > startup applications
2. click 'add'
3. Name it whatever you want & add 'syndaemon -d -i 0.5' (without quotes) to the command box.
4. logout & log back in (i think you have to log out? I forget)

This will make it so that after you hit a key, your touchpad will be disabled for a certain amount of time. I have mine set to 0.5 - i think 1 or 2 seconds is more common but whatever. You can find more info on
[http://linuxcommand.org/man_pages/syndaemon1.html](http://linuxcommand.org/man_pages/syndaemon1.html)
hope that helps!

---

