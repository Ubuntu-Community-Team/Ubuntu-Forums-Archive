---
title: "BadLength Error after enabling XEVIE"
date: 2009-02-18
forum: Desktop Environments
---

### Post by veaudaux on 2009-02-18
I'm running Intrepid.

I added:
[INDENT]Section "Extensions"
    Option         "XEVIE" "Enable"
EndSection[/INDENT]
to the bottom of my /etc/X11/xorg.conf file, in order to enable XEVIE to capture keystrokes for Mumble (it's one of those gaming VoIP apps, it needs to capture keystrokes for it's Push-To-Talk button).

I restarted X and ran Mumble, and my keyboard and mouse stopped working. I restarted X again and ran Mumble from terminal so I could see what was happening - on every keypress or mouseclick I'm getting an X Error in the terminal window. I can't copy and paste the error exactly, because my input devices don't work - what I scribbled down on paper though was:
[INDENT]X Error: BadLength (poly request too large or internal Xlib length error) 16
  Extension:    160 (Uknown extension)
  Minor opcode: 3 (Unknown request)
  Resource id:  0x17[/INDENT]
As long as I don't run Mumble, the keyboard and mouse work fine - but even after a full restart I'm still getting this error any time the program runs.

Any ideas? I really appreciate the help.

---

### Post by veaudaux on 2009-02-19
I (sort of) worked out my problem - I post this here for the sake of posterity.

The XEVIE errors are caused by the fact that XEVIE is no longer fully supported in X.

Mumble can still capture keypresses through hardware polling however - so if you've added anything to your xorg.conf to enable XEVIE, take them back out again - you don't need it, and it'll just break things.

The problem I was originally having that made me turn on XEVIE in the first place (Mumble not detecting my extra mouse buttons) was related to Intrepid not fully supporting the Logitech G5 mouse right out of the box.

To get Intrepid to play nice with my Logitech G5, I added the following to the top of my xorg.conf, right below the comments:

[INDENT]Section "InputDevice"
Identifier "Configured Mouse"
Driver "evdev"
Option "CorePointer"
Option "Name" "Logitech USB Gaming Mouse"
Option "Device" "/dev/input/event1
Option "ZAxisMapping" "4 5 6 7"
Option "Emulate3Buttons" "false"
EndSection[/INDENT]

Then in Section "ServerLayout" I added
[INDENT]InputDevice "Configured Mouse"[/INDENT]

AND in Section "ServerFlags" I added
[INDENT]Option "AutoAddDevices" "false"[/INDENT]

I created a file in my /home/ directory called .Xmodmap, and in it I put
[INDENT]pointer = 1 6 3 4 5 8 9 2 7[/INDENT]

Then ran the following command in Terminal
[INDENT]xmodmap ~/.Xmodmap[/INDENT]

Then restarted X with a Ctrl+Alt+Backspace. When X restarted it confirmed that I wanted to load the custom Xmodmap, and after that, Mumble was at least able to detect ONE of my Logitech G5's side buttons (it also made the tilt wheel work for History back and forward in Firefox again).

If anybody's got any further input, I welcome it.

---

