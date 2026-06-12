---
title: "Can't change my resolution"
date: 2006-01-19
forum: General Help
---

### Post by liquanius on 2006-01-19
Whenver i boot up the live cd it sets the default resolution for my monitor to 600x400, and it won't give me any other options to change it to.  I've used the same live cd on numerous pc's and it gives additional resolutions to change to. Any help?

---

### Post by mettallicat on 2006-01-19
Check if you have modes in xorg.conf

like :

```

Section "Screen"
        Identifier      "Screen"
        Device          "ATI Radeon"
        Monitor         "Monitor"
        DefaultDepth    24

        Subsection "Display"
                Depth           24
                Modes           "1024x768" "800x600" "640x480"

                # uncomment this for MergedFB
#               Virtual         1024 1536
        EndSubsection
EndSection

```

and add more if needed

---

### Post by mioip on 2006-01-19
I have the modes, but I can't change my resolution either.

I know there's a config utility that fixed this problem last time I installed Ubuntu, but I don't remember what it was. How do I unstick this is my xorg.conf looks ok?

---

### Post by Wagawaga on 2006-01-20
try ---  dpkg-reconfigure xserver-xorg

---

