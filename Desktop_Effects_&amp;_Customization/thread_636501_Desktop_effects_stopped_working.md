---
title: "Desktop effects stopped working"
date: 2007-12-09
forum: Desktop Effects &amp; Customization
---

### Post by Ryan Cacophony on 2007-12-09
FF, 7.10

Somewhere between mounting my windows drive (I'm 99% sure it wasn't this, but just in case), and changing my desktop background, the desktop effects on my computer stopped working.

Let me get a bit more specific:  whenever I set the desktop effects to "normal," I am not able to drag windows.  I can minimize, maximize, rotate the cube, wobbly windows when it's minimized/maximized.  But I can't move the windows at all.
//Edit: I actually don't have a cube, when I switch it defaults my windows to two windows and it does the flip thing.  how do you change it to 4/the cube? (I had it like this before I upgraded from 7.04)

So, If I shut all effects off, I can drag the windows, but this is reaaaally boring.

I was also wondering: how do you edit what desktop effects you have?  They give no hint as to what the difference between normal and Extra are, and don't appear to list the key shortcuts.

---

### Post by Ryan Cacophony on 2007-12-10
If needed, I can post my xorg.conf, but I don't think that will help

---

### Post by Ub1476 on 2007-12-10
Install the Advanced Desktop Effects:

```
sudo apt-get install compizconfig-settings-manager
```

Set Visual Effects to custom.

Open System>Preferences>Advanced Desktop Effects>Window Managment>Move Window.

You should be able to move window now.

To get the Cube back, go to Desktop>Check Cube and Rotate cube.

Now go to General>General options>Desktop size>Set horizontal to 4.

All key settings for the plugins is in the "actions" tab.

---

### Post by Ryan Cacophony on 2007-12-10
Thanks so much.  Adding that allowed me to customize my settings, but it did not fix my moving windows problems, but I found out my own fix:

For those who might look at this thread with the same problem:  After getting that package, go to the custom settings and search for the filter "move window" and make sure it's checked.  That's it.  :D

---

### Post by Ub1476 on 2007-12-10
Yes, I know. I said that:)

> Open System>Preferences>Advanced Desktop Effects>Window Managment>Move Window.

---

### Post by Ryan Cacophony on 2007-12-10
Oh wow, I'm dense.... I think I just assumed where you were pointing me to xD

---

