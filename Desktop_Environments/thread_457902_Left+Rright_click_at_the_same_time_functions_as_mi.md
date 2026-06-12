---
title: "Left+Rright click at the same time functions as middle click, how do I change?"
date: 2007-05-29
forum: Desktop Environments
---

### Post by dspari1 on 2007-05-29
When I press the left and right click at the same time, it functions as the middle click button. How do I remove this feature so that it does nothing?

I need to change this because when I play games, I accidentally press my middle click button by pressing both left and right click at the same time, so help is greatly appreciated.

;)

---

### Post by Blender on 2007-05-29
Not really sure if there's a GUI-way to set it.

But you can do it from your **/etc/X11/xorg.conf** file.

[LIST=1]
[*] Open a terminal: Applications->Accessories->Terminal
[*] Create a backup of the file:
```

$ sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf-backup
Password: <here you enter your password>
```
[*] Open the file:
```

$ sudo nano /etc/X11/xorg.conf

```
[*] Find the section for your mouse, something like
```

Section "InputDevice"
    Identifier  "Mouse0"
    Driver      "mouse"
    ...

```

[*] See if there's an option
```

    Option      "Emulate3Buttons"   "true"

```

[LIST=2]
[*]If yes, then change the true to false.
[*]If no, then add the following:
```

Option      "Emulate3Buttons"   "true"

```
[/LIST]

[/LIST]

To summarize, your mouse section would look something like:
```

Section "InputDevice"
    Identifier  "Mouse0"
    Driver      "mouse"
    Option      "CorePointer"
    Option      "Device"            "/dev/input/mice"
    Option      "Protocol"          "ImPS/2"
    Option      "ZAxisMapping"      "4 5"
    Option      "Emulate3Buttons"   "false"
EndSection

```
Note the **Emulate3Buttons** line, ignore the other things. Don't change anything else in the file.

Hope this helps.

---

### Post by dspari1 on 2007-05-29
Awsome, works perfect.

I think they should add a GUI way to do it because it was a real problem when playing games on Cedega. I'm happy now. :)

---

### Post by mozetti on 2007-05-29
There is a "semi-GUI" way of doing it -- in the terminal if you run ```
sudo dpkg-reconfigure xserver-xorg
```.

It's an automated way to set up your xorg.conf file, and it has the "emulate 3-button mouse" question in there.

---

