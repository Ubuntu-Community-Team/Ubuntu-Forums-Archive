---
title: "Can't get compizfusion to work no matter wat..."
date: 2007-07-28
forum: Desktop Effects &amp; Customization
---

### Post by Demon Designs on 2007-07-28
Ok so I hav got my driver I hav compiz fusion all installed but everything i try it don't start up any suggestions... If i can't fix it on fiesty I will prob hav to wait til the next distro upgrade.. can any1 help me coz its really annoying coz my computer is seeming mo0re and more like a pile of c***...

and I really wanna fix this asap

---

### Post by sad_iq on 2007-07-28
Do you have the drivers correctly installed??? Paste the output of this command here to troubleshoot if possible!!! ```
 glxinfo |grep direct && cat /etc/X11/xorg.conf | grep driver && lspci | grep VGA
```

---

### Post by skymera on 2007-07-28
ok i helped him though some bits.

he got

xserver-xorg-video-amd
xserver-xorg-video-ati

and

xorg-driver-fglrx

his xorg conf file, as much as i know is normal.

he changed the driver from "ati" to "fglrx"

---

### Post by sad_iq on 2007-07-28
does he have direct rendering=yes????

---

### Post by skymera on 2007-07-28
o, i dont know.

he has an ATI Raedon 9550.

hes not on MSN at the moment, other side of the world lol.
i cant talk to him for another 12 hours or so.

---

### Post by Demon Designs on 2007-07-28
sidewinder@thomas-desktop:~$ glxinfo |grep direct && cat /etc/X11/xorg.conf | grep driver && lspci | grep VGA
direct rendering: Yes
sidewinder@thomas-desktop:~$ 

^^^ Tis wat I got I hav followed all tuts I hav found none have worked :(

---

### Post by sad_iq on 2007-07-28
That's strange...the command I gave you should have posted more things...I DO believe that your driver is causing so much trouble...anyway what happends when you type in a terminal ```
compiz --replace
```

---

### Post by skymera on 2007-07-28
as far as i know, nothing happened.
which puzzles me there.

all i know is ATI, in fact is a bitch to get drivers for. almost no support.

maybe get an nVidia?

---

### Post by Demon Designs on 2007-07-28
When I type that in it does nothing it just stays the same

---

### Post by andrewsomething on 2007-07-29
> **skymera said:**
> as far as i know, nothing happened.
which puzzles me there.

all i know is ATI, in fact is a bitch to get drivers for. almost no support.

maybe get an nVidia?

I've found that the simplest way to get ATI cards running compiz is to use the restricted driver and create an xgl session. Just search xgl and ati in the forum for a how to...

---

