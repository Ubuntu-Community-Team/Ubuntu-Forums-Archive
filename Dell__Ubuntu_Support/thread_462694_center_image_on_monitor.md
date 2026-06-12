---
title: "center image on monitor"
date: 2007-06-03
forum: Dell  Ubuntu Support
---

### Post by dondad on 2007-06-03
I have a Dell 1701fp monitor on my system. I finally got the 1280X1024 resolution working thanks to help from the forums, but have a bit of a problem with the centering. The screen image is about an eighth of an inch to the right, which is just enough to hide the scrollbars and the close box when a window is maximized.

I guess that the buttons on the monitor must have been using some software to adjust the size/position because they no longer function in ubuntu. Is there a way that I can adjust the screen position in ubuntu?

Got it fixed per below reply. thanks to everyone for the answers.

---

### Post by pappapump on 2007-06-03
The buttons on the monitor will function no matter what OS you are using.
Your primary menu button on any dell will almost always be the large one to the left or extreme right.
If pushing it does nothing then keep pushing till you feel a slight click, it may just be dirty.
You should see 2 buttons in the middle with opposing arrows which set centering after menu mode is entered.

---

### Post by yabbadabbadont on 2007-06-03
Run xvidtune from a terminal window.  Adjust your screen.  Click the "Show" button when done, then quit.  It should have spit out a line in the terminal window when you clicked Show.

Example from my monitor: ```
"1024x768"     78.75   1024 1040 1136 1312    768  769  772  800 +hsync +vsync
```
You now need to select that line and copy it.  Now edit your /etc/X11/xorg.conf file.  You will need to use either sudo or gksudo when you start your editor.  (sudo for a command line editor like vi and gksudo for a graphical editor like gedit)  Now you need to add that line to your "Monitor" section, but you also need to add the keyword, "ModeLine", to the front of the text you copied.

Example from my monitor: ```
Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       30-69
        VertRefresh     50-80
        DisplaySize     306 230
        Gamma           0.75 0.75 0.75
        ModeLine        "1024x768"     78.75   1024 1040 1136 1312    768  769  772  800 +hsync +vsync
EndSection

```
Save your changes and exit the editor.  Now you need to restart X windows.  Either logout and reboot or logout and hit Control-Alt-Backspace at the login screen.

---

### Post by bapoumba on 2007-06-03
Thread moved to "Ubuntu Dell Support" sub forum.

---

### Post by dondad on 2007-06-04
> **yabbadabbadont said:**
> Run xvidtune from a terminal window.  Adjust your screen.  Click the "Show" button when done, then quit.  It should have spit out a line in the terminal window when you clicked Show.

Example from my monitor: ```
"1024x768"     78.75   1024 1040 1136 1312    768  769  772  800 +hsync +vsync
```
You now need to select that line and copy it.  Now edit your /etc/X11/xorg.conf file.  You will need to use either sudo or gksudo when you start your editor.  (sudo for a command line editor like vi and gksudo for a graphical editor like gedit)  Now you need to add that line to your "Monitor" section, but you also need to add the keyword, "ModeLine", to the front of the text you copied.

Example from my monitor: ```
Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       30-69
        VertRefresh     50-80
        DisplaySize     306 230
        Gamma           0.75 0.75 0.75
        ModeLine        "1024x768"     78.75   1024 1040 1136 1312    768  769  772  800 +hsync +vsync
EndSection

```
Save your changes and exit the editor.  Now you need to restart X windows.  Either logout and reboot or logout and hit Control-Alt-Backspace at the login screen.

Thanks, that did it.

---

### Post by dondad on 2007-06-04
> **pappapump said:**
> The buttons on the monitor will function no matter what OS you are using.
Your primary menu button on any dell will almost always be the large one to the left or extreme right.
If pushing it does nothing then keep pushing till you feel a slight click, it may just be dirty.
You should see 2 buttons in the middle with opposing arrows which set centering after menu mode is entered.

I have tried everything on this one, and none of the buttons do anything.

---

### Post by Sunflower1970 on 2007-06-04
> **pappapump said:**
> The buttons on the monitor will function no matter what OS you are using.
Your primary menu button on any dell will almost always be the large one to the left or extreme right.
If pushing it does nothing then keep pushing till you feel a slight click, it may just be dirty.
You should see 2 buttons in the middle with opposing arrows which set centering after menu mode is entered.

[QUOTE=dondad]I have tried everything on this one, and none of the buttons do anything.[/QUOTE]

The above should work. I have the same model Dell  flat panel as you and by playing around with the buttons on the monitor worked just fine... (I also have the 1702fp and the buttons work as well)

---

