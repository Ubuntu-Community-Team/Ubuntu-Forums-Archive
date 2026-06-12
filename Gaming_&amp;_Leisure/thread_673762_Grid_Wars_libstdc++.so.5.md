---
title: "Grid Wars libstdc++.so.5"
date: 2008-01-21
forum: Gaming &amp; Leisure
---

### Post by kooldino on 2008-01-21
I got Grid Wars 2 from: [http://gridwars.marune.de/bin/gridwars_lin.zip](http://gridwars.marune.de/bin/gridwars_lin.zip)

When I try to run it, I get the following error:

```
libstdc++.so.5: cannot open shared object file: No such file or directory

```

I have the libstdc++6 package installed.

---

### Post by KhaaL on 2008-01-21
libstdc++-so.5 is in the package libstdc++5 - not libstdc++6 :)
So a simple sudo apt-get install libstdc++5 should get you going to enjoy this great game.

---

### Post by kooldino on 2008-01-21
> **KhaaL said:**
> libstdc++-so.5 is in the package libstdc++5 - not libstdc++6 :)
So a simple sudo apt-get install libstdc++5 should get you going to enjoy this great game.

Can they co-exsist?  I just assumed that 6 was a newer version of 5 and that there would be a conflict between the two.

---

### Post by DoktorSeven on 2008-01-21
Yes, they can.  They have different files and can exist side-by-side.

---

### Post by kooldino on 2008-01-21
Awesome, I'll give it a whirl and report back.

---

### Post by kooldino on 2008-01-26
libstdc++5 installed fine...now when I go to run it, I get the following:

X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  134 (XFree86-VidModeExtension)
  Minor opcode of failed request:  10 (XF86VidModeSwitchToMode)
  Value in failed request:  0x137
  Serial number of failed request:  43
  Current serial number in output stream:  46

---

### Post by Perfect Storm on 2008-01-26
Could be that the resolution it using is not supported in your xorg.conf. either add it or change the resolution of the game (most games have a .ini/.conf file hidden in your home folder.

---

### Post by kooldino on 2008-01-26
I'll give that a shot.

---

