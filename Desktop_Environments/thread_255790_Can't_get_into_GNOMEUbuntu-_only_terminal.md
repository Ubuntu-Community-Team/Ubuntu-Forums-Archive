---
title: "Can't get into GNOME/Ubuntu- only terminal"
date: 2006-09-12
forum: Desktop Environments
---

### Post by kendals on 2006-09-12
Hey guys. I have a huge problem...

I tried (stupidly) to follow the guide here ([http://ubuntuforums.org/showthread.php?t=253856](http://ubuntuforums.org/showthread.php?t=253856)) to install compiz+aiglx, and now it's destroyed my Ubuntu :(

Basically, I've tried the "sudo dpkg-reconfigure xserver-xorg" command to make a new xorg.conf but then I'd restart after doing that, and it'd still give that blue screen with the prompt about "X Server failed to load, etc". And it'd give me a prompt screen with my login...

I then tried "startx" to get in that way, but it gave an error halfway through, saying it didn't like the PCI config (0:2:1) even though I've told it to use 0:2:0 which is the default, and is the location of the video card.

I'm lost- is there any way to restore it from the CD? Someone please help! I want to cry! :frown:

---

### Post by someguyouknow on 2006-09-12
you cant restore the backup xorg file?

---

### Post by kendals on 2006-09-12
NO :( It seems to be shot as well...can I grab it off the CD or something?

---

### Post by kendals on 2006-09-12
Some more info- even after editing via VI the xorg.conf, and then trying to 'startx' it STILL says:

```
(WW) I810: No matching Device section for instance (BusID PCI:0:2:1) found
(EE) I810(0): No matching device found
```

And won't run. I tried changing the PCI from 0:2:0 to 0:2:1 and that doesn't help- it just replaces the error with one about 0:2:0 found, etc... :(

---

### Post by kendals on 2006-09-12
Problem was solve by tseliot over here: [http://ubuntuforums.org/showpost.php?p=1489817&postcount=854](http://ubuntuforums.org/showpost.php?p=1489817&postcount=854)


:D:D:D

---

