---
title: "1505n Widescreen Woes"
date: 2007-06-12
forum: Dell  Ubuntu Support
---

### Post by bunted on 2007-06-12
Recently, I bought an e1505n Ubuntu Edition notebook.  Just about everything works fine, except for the fact that I couldn't get a resolution higher than 1024x768.  In my xorg.conf it even listed 1680x1050 as the resolution for all modes.  The only option listed in screen resolution is 1024x768.  So I called Dell.  Of course they had no solution for me except to pay Canonical.  (Which I find pretty lame that I drop well over $1K on something that doesn't work properly, and now I have to pay someone to find a way to make it work.)  So I do a little reading.

The 915resolution package, after being installed, granted me the higher resolutions I should have.  Then I read a post about how we should use xserver-xorg-video-intel package instead.  Both of these packages independently solved my widescreen problems.

However, when I apply either 915 or the intel driver I lose the CRT/LCD functionality of 'Fn-F8.'  I really need to use my laptop to feed external devices.  I can get a cloned output from the VGA, but I can't feed anything properly because I only can use resolutions with the same h/v pixel ratio as my LCD screen.

Is there a fix for this that grants me the better resolutions without disabling the CRT/LCD functionality of the bios?

Let me also say that every attempt to make the S-Video port work has failed.  I did find one hackish solution by constantly reloading different xorg.confs and restarting x, but this is a new laptop.  There should be a better way.

Anyone have any thoughts?

---

### Post by benanzo on 2007-06-12
Have a look at the package *i810switch*.  It's in the Ubuntu repositories.

After it's installed open a terminal **Applications -> Accessories -> Terminal** and do:
```

i810switch
```
make sure that your external monitor is plugged in or you'll get:
```

PCI id of i810 is not recognized.

```

---

### Post by bunted on 2007-06-12
So the i810switch is compatable with the "i810" driver or the "intel" driver or both?

Right now I'm using the intel driver instead of the i810 and 915resolution patch.

---

### Post by benanzo on 2007-06-12
Hmm.  I am actually not sure about that.  I have been using it with the *i810* driver on my MacBook with the Intel GMA950 chip and it works great.  I have not tried it with the *intel* driver.

---

