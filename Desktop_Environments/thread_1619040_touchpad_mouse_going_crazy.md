---
title: "touchpad mouse going crazy"
date: 2010-11-11
forum: Desktop Environments
---

### Post by uzlezz on 2010-11-11
[solved]
My touchpad mouse is going crazy. 
Some times I load up its worse than others. The cursor jumps around and often right clicks things. on occasion it wount respond to my clicks when I need it and I have to keep clicking till it works. It is extremely frustrating.

 It is not a hardware problem as the touchpad works fine on the Windows partition.
I have 10.4 at default settings, apart from the mouse sensitivity, which is really low.

Can someone please help me fix this. Advising me to use a USB mouse is not helpful as I am constantly on the move and a separate mouse is inconvenient.

---

### Post by bobcollard on 2010-11-12
> **uzlezz said:**
> My touchpad mouse is going crazy. 
Some times I load up its worse than others. The cursor jumps around and often right clicks things. on occasion it wount respond to my clicks when I need it and I have to keep clicking till it works. It is extremely frustrating.

 It is not a hardware problem as the touchpad works fine on the Windows partition.
I have 10.4 at default settings, apart from the mouse sensitivity, which is really low.

Can someone please help me fix this. Advising me to use a USB mouse is not helpful as I am constantly on the move and a separate mouse is inconvenient.
Try gpointing-device-settings, find it in synaptic package manager.

---

### Post by uzlezz on 2010-11-12
Just tried that, but it didn't work. 
Any other suggestions?

---

### Post by bobcollard on 2010-11-12
> **uzlezz said:**
> Just tried that, but it didn't work. 
Any other suggestions?
Sorry, did you just install it or run it?  You should have unchecked the two boxes under System>Mouse for touchpad and run it either using Alt>F2 or Run Program.  You can also have it startup in Applications startup.  It needs to be reset each time you reboot or log out.

---

### Post by uzlezz on 2010-11-12
Yay that worked. 
I did just install it. Thanks for the help. So I have to start it up every time I log on? Is there any way I can make it to it automatically?

---

### Post by bobcollard on 2010-11-12
> **uzlezz said:**
> Yay that worked. 
I did just install it. Thanks for the help. So I have to start it up every time I log on? Is there any way I can make it to it automatically?
I mentioned using Application Startup.  Use the name of the applet as the command to start it.  Then it will be on your screen ready for your changes when you startup.  I'm not running Gnome so I am not sure where Application Startup is in your menu.

---

### Post by uzlezz on 2010-11-12
Thanks a lot you have been a great help!

---

### Post by bobcollard on 2010-11-12
You are welcome.  Please Edit your first post and in the Title add [Solved] so others may benefit from your experience.

---

### Post by dleik on 2010-11-12
I have a similar issue, except with the trac ball pointer in the middle of the keyboard.  On one of our teachers laptops, Dell Latitude 810, the trac pointer is spazing out.  The pointer will start to wander, and then get stuck in the upper right corner of the screen.  I can try to take it over with the touch pad, but am not always successful.  Is there a way to disable it.  I couldn't find anything in Software Center.  :confused:

---

### Post by bobcollard on 2010-11-12
> **dleik said:**
> I have a similar issue, except with the trac ball pointer in the middle of the keyboard.  On one of our teachers laptops, Dell Latitude 810, the trac pointer is spazing out.  The pointer will start to wander, and then get stuck in the upper right corner of the screen.  I can try to take it over with the touch pad, but am not always successful.  Is there a way to disable it.  I couldn't find anything in Software Center.  :confused:
If you have a mouse you can disable it with gpointing-device-settings.

---

