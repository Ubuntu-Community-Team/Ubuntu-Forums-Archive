---
title: "Xorg iz empty!"
date: 2009-01-19
forum: General Help
---

### Post by GrimmReaperVI on 2009-01-19
I'm an ubuntu noob still getting the hang of everything. From my little knowlage, Xorg is a thingamajig that sets things up...or something like that...yeah :confused:

So I after the Intepid Ibex, i've had no mouse control. Or keyboard control. So I look in my xorg.conf file. Feel free to correct me but there should be something like:

```
Section "InputDevice"
Identifier "Configured mouse"
Driver "mouse"
Option "CorePointer
EndSection

Section "InputDevice"
Identifier "Generic Keyboard"
Driver "kbd"
Option "XkbRules" "xorg"
Option "XkbModel" "pc105"
Option "XkbLayout" "us"
EndSection"

Section "ServerLayout"
Identifier "Default Layout"
screen "Default Screen"
Inputdevice "Generic Keyboard"
Inputdevice "Configured Mouse"
EndSection
```

Well, that's what I found by googling. Anyway, my xorg.conf only has info about my screen and the monitor but none of these sections. I've tried reconfiguring but still no change. Help? Should I manually add them? Is there a specific position I have to add them?

---

### Post by Npl on 2009-01-19
Theres work underway to make the xorg.conf file redundant, and Intrepedid should be able to work without one. I remember having trouble with Keyboard/Mouse but I cant remember what I did to fix it. Unfortunatly most Ubuntus had some very weird bugs at release... which get worked out soon afterwards usually.

Do you have a fully uptodate System, might be that this bug is fixed already. If you dint update yet, do so and delete the xorg.conf file - you dont need it unless you use restricted drivers.

---

### Post by GrimmReaperVI on 2009-01-19
My system Is up to date. What should I delete? The whole X11 Folder?

---

### Post by Npl on 2009-01-19
> **GrimmReaperVI said:**
> My system Is up to date. What should I delete? The whole X11 Folder?God no, only the /etc/X11/xorg.conf file. But as your system is uptodate it likely wont help.

Do you have any Gamepads/wheels/joysticks attached? Might try without them if thats the case.

---

### Post by GrimmReaperVI on 2009-01-19
It's worth a try. How about all the other xorg.confs?
(backup, lots of numbers ect.)

---

### Post by Npl on 2009-01-19
xorg.blahblah are all backup-files, can delete them aswell but it wont make a difference (other than removing useless files).

In case running without xorg.conf aint working, you can automatically create a new file using "Xorg -configure". I think it creates the file in the current directory so will still have to copy it over to /etc/X11.. and to fix your problem you will have to edit it, but it should be a better starting point than a random file from the internet.

---

### Post by GrimmReaperVI on 2009-01-19
K, one thing left to ask. What's the command you delete files again? >.<

---

### Post by adamlau on 2009-01-19
```
man rm
```

But before you do, you may want to take a look at:

```

man cp
man mv

```

---

### Post by Npl on 2009-01-19
```
sudo rm /etc/X11/xorg.*
```

(Other OSes would use something intuitive like "delete" or "remove", but hey this is the l337 haxx0r OS)

---

### Post by GrimmReaperVI on 2009-01-19
> **Npl said:**
> (Other OSes would use something intuitive like "delete" or "remove", but hey this is the l337 haxx0r OS)

:lolflag: yeah quite true. No change when I deleted xorg.conf and now I can't search for updates for some reason!! (you never know, I might have missed a brand new one)

---

### Post by adamlau on 2009-01-19
I assume you restarted X after removing xorg.conf. If so, run:

```
dpkg-reconfigure xserver-xorg
```

---

### Post by GrimmReaperVI on 2009-01-19
restarted...?

---

### Post by adamlau on 2009-01-19
In order to initialize new settings, Ctrl+Alt+Backspace ought to do it...

---

### Post by GrimmReaperVI on 2009-01-19
Yes, but it still doesn't show anything about my mouse and keyboard. there's only "Device" "Monitor" and "Screen"

---

