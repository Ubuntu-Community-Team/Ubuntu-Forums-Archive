---
title: "Weird Error"
date: 2007-06-29
forum: Desktop Effects &amp; Customization
---

### Post by chrisf79 on 2007-06-29
Greetings:

I installed nvidia-glx-new and it is working.  At least, the NVIDIA logo shows up when I start X.  Then, I went and did:

sudo apt-get install beryl emerald-themes

That installed and the Beryl gem shows up in the top pane.  However, I don't see any effects at all.  When I ran beryl-manager from terminal, this error pops up:

* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : NVIDIA

Checking Display :0.0 ...

Checking for XComposite extension               : failed

No composite extension


How do I fix this?  Any help for a newbie would be greatly appreciated!

---

### Post by hyperair on 2007-06-29
Add this to the bottom of your /etc/X11/xorg.conf file:
```

Section "Extensions"
          Option "Composite" "Enable"
EndSection

```

---

