---
title: "1280x800 resulotion not available?"
date: 2007-04-30
forum: Desktop Environments
---

### Post by Mustek on 2007-04-30
Hey,
My screen resolution should be 1280x800, but it isn't in the list,
how do I add it? (I have like, 2 screens above eachother and a line on the left...)

---

### Post by ArtificialSynapse on 2007-04-30
You've got to edit your xorg.conf file to allow that resolution. 

```

        SubSection "Display"
                Viewport  0 0
                Depth     24
                Modes     "1280x800"
        EndSubSection
EndSection

```


Add this where all the other subsection listings are in your xorg file.

---

### Post by ayoli on 2007-04-30
> **Mustek said:**
> Hey,
My screen resolution should be 1280x800, but it isn't in the list,
how do I add it? (I have like, 2 screens above eachother and a line on the left...)
What is your hardware ?
I experienced same problem with an intel i945 chipset on my new HP laptop, i solved this with 915resolution (which you can install via apt-get from universe or multiverse repos)
then i've edited /etc/default/915resolution to have these lines in it:
```
MODE=3c
XRESO=1280
YRESO=800
BIT=24
```
now it works just like a charm :)

---

### Post by ntt on 2007-04-30
Confirmed, you probably need to install the package "915resolution".

That is, IF your video board is based on an Intel chipset (like i915/i945).

These days most low-cost laptop PC's are equipped with Intel graphic chips, and for some reason most of the provided Intel video BIOS still have this bug, which is preventing X.org from properly recognising 1200x800 or 1280x800 resolutions.

In my case, I never needed to fiddle with the 915resolution configuration file: just installed the package and rebooted the laptop, and it was OK.

Tested on HP and DELL laptops.

hope this helps.

---

