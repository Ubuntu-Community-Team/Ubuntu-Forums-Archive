---
title: "How do I edit xorg.conf?"
date: 2009-06-22
forum: General Help
---

### Post by PsychedelicWonders on 2009-06-22
I need to add some code to my xorg.conf so I can have both of my video cards show up so I can run 4 monitors.

I need to add this to it...

```
Section "Device"
     Identifier     "Videocard0"
     Driver         "nvidia"
     VendorName     "NVIDIA Corporation"
     BoardName      "Unknown"
     BusID          "PCI:1:0:0" 
EndSection

Section "Device"
    Identifier     "Videocard1"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 9600 GT"
    BusID          "PCI:4:0:0"
    Driver          "nvidia"
    Option          "NoLogo"    "True"
EndSection
```

---

### Post by michy99 on 2009-06-22
```
gksudo gedit /etc/X11/xorg.conf
```Make changes and save.

---

### Post by Lucky. on 2009-06-22
I don't know how to do it purely from the GUI.  However a terminal with the sudo command will allow you to gain write permissions to the file.

Open up a terminal, and type the following:

```
sudo gedit /etc/x11/xorg.conf
```

Good luck!  4 monitors, phew!  I hope it works for you.  I have a hard enough time getting one to work at times.

---

### Post by Cheesemill on 2009-06-22
> **Lucky. said:**
> I don't know how to do it purely from the GUI.  However a terminal with the sudo command will allow you to gain write permissions to the file.

Open up a terminal, and type the following:

```
sudo gedit /etc/x11/xorg.conf
```Good luck!  4 monitors, phew!  I hope it works for you.  I have a hard enough time getting one to work at times.

You really shouldn't do this, use
```
gksudo gedit /etc/X11/xorg.conf
```instead.
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

You can also hit ALT + F2 and type this instead of opening a terminal.

---

### Post by PsychedelicWonders on 2009-06-23
> **Cheesemill said:**
> You really shouldn't do this, use
```
gksudo gedit /etc/X11/xorg.conf
```instead.
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)
 
You can also hit ALT + F2 and type this instead of opening a terminal.
 
Very interesting tip! thanks man.

---

