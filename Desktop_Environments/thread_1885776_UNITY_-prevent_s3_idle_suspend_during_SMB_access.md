---
title: "UNITY -prevent s3 idle suspend during SMB access"
date: 2011-11-23
forum: Desktop Environments
---

### Post by fredknex on 2011-11-23
So back before the switch to unity there was a command that reset the idle timer

"gnome-screensaver-command --poke"

that could be set up to stop the computer from suspending itself when the SMB share is being accessed.


This doesnt work in Unity, is there an equivalent? 


Thanks for any help

---

### Post by fredknex on 2011-12-07
---

---

### Post by thaelim on 2011-12-07
You can use the Gnome session dbus interface:

[http://live.gnome.org/GnomePowerManager/DbusInterface](http://live.gnome.org/GnomePowerManager/DbusInterface)

It has an Inhibit method you can call to prevent idle. There is even an example file of how to do this.

---

### Post by fredknex on 2011-12-07
great! Except none of the links on that page seem to be working. 
But its enough I feel like I'm on the right track now, thanks!

---

