---
title: "Beryl, get back title bar for nvidia?"
date: 2007-03-20
forum: Desktop Effects &amp; Customization
---

### Post by zanyspydude on 2007-03-20
I don't know if this will help anyone else, but when i installed beryl and used it as the window manager, the titlebar disappeared on me and the console became nothing but a white screen.   I looked at my xorg.conf file and it's backup and noticed that something changed...

I added 
```
    Option "AddARGBGLXVisuals" "True"
```

```
Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 6600 GT"
    Option "AddARGBGLXVisuals" "True"
EndSection
```

to the device section.  Hope this helps someone else out!

btw, i'm a total n00b so have some mercy :(.

-David

---

### Post by zixxer on 2007-03-22
i have this same problem...gnome term is completely white and all other windows are missing everything around them....only xterm works and it still doesnt have buttons....i will give this a shot..

ive had this working with the last nvidia drivers and the previous version of beryl...im thinking its the new nvidia driver. any ideas?

---

### Post by flowb on 2007-04-20
hello,

i've been having the same issue. i'm currently using the nvidia-glx driver from the repos. does using the driver from the nvidia site fix this?

i've got the extra cruft in my xorg.conf. compiz seems to generally work ok but, i haven't gotten beryl to load properly once.

---

### Post by bribri124 on 2007-04-20
I completed my upgrade last night, and I had the same problem.  The nvidia-glx driver will work, but the option that zanyspydude posted must be added to your xorg.conf.  Here is a post from Beryl:

[http://forum.beryl-project.org/viewtopic.php?f=35&t=1631](http://forum.beryl-project.org/viewtopic.php?f=35&t=1631)

After inserting this option, I found it would not function until I did a restart.  Additionally, I tried to use the same format as posted by zanyspydude.  That disabled X11 for me, so I had to remove those lines.

I hope this helps.

---

