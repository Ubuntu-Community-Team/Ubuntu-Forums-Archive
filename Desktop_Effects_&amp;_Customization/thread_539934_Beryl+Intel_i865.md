---
title: "Beryl+Intel i865"
date: 2007-08-31
forum: Desktop Effects &amp; Customization
---

### Post by coricaman on 2007-08-31
I need to know how to update xorg and run configuration for my drivers
intel: i810
then the beryl commands thereafter....
I know 
sudo apt-get install beryl
then?

---

### Post by Milk &amp; Toast &amp; Honey on 2007-09-01
Hi, have you tried to see this [post]("http://ubuntuforums.org/showpost.php?p=1552759&postcount=207") ?

Basically, you need to add the lines in that post up there to the xorg.conf file, located in /etc/X11/xorg.conf.

I'll provide the steps:
1. Application -> Accessories -> Terminal
2. Type
```

sudo gedit /etc/X11/xorg.conf

```
3. Find the line written " Section "Module" ", and add this line:
```

    Load "dri"

```
4. Find the line written " Section "Device" ", and add this line:
```

    Option "XAANoOffscreenPixmaps" "true"

```
5. Then, go to the end of line, and add this lines:
```

Section "Extensions"
    Option "Composite" "true"
EndSection 
Section "DRI"
    Mode "0666"
EndSection

```
6. Save the file, logout, and restart X (Ctrl-Alt-Backspace), or you can just restart the computer.
7. Login, then to load beryl type this at the terminal:
```

beryl

```
or
```

beryl-manager

```
to customize the beryl's settings.

---

