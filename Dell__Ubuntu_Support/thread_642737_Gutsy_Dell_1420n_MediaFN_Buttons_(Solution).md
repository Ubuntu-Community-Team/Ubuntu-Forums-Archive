---
title: "Gutsy Dell 1420n Media/FN Buttons (Solution)"
date: 2007-12-17
forum: Dell  Ubuntu Support
---

### Post by kuja on 2007-12-17
I don't know about the rest of you, but I've had issues with getting the media & fn buttons to work on my 1420n since upgrading to Gutsy. Fortunately, I've come up with a solution.

I suppose this ****could**** scale to other computers with some minor modifications, but I do not expect it would work without.

[size=4]Dependencies:[/size]

```
sudo apt-get install xmodmap xbindkeys
```

[size=4]Files:[/size]

Create a file, 
~/.xmodmaprc
```

keycode 162 = XF86AudioPause
keycode 174 = XF86AudioLowerVolume
keycode 176 = XF86AudioRaiseVolume
keycode 160 = XF86AudioMute
keycode 144 = XF86AudioPrev
keycode 164 = XF86AudioStop
keycode 153 = XF86AudioNext
keycode 101 = SunVideoLowerBrightness
keycode 212 = SunVideoRaiseBrightness
keycode 237 = XF86AudioMedia
keycode 165 = XF86Sleep

```

Create a file, 
~/.xbindkeysrc
```

"sudo raisebrightness.py" 
SunVideoRaiseBrightness

"sudo lowerbrightness.py" 
SunVideoLowerBrightness

```

Create a file:
/usr/bin/raisebrightness.py
```

#!/usr/bin/python

import os
import sys

if os.path.isfile("/tmp/brightness.lock"):
	sys.exit(1)

os.system("touch /tmp/brightness.lock")

currentBrightness = open("/proc/acpi/video/VID/LCD/brightness").readlines()[1].strip()
currentBrightness = int(currentBrightness[9:len(currentBrightness)])

newBrightness = 0

if currentBrightness < 96:
	newBrightness = currentBrightness + 12

if newBrightness == 96:
	newBrightness = 100

os.system("echo -n %d > /proc/acpi/video/VID/LCD/brightness" % newBrightness)
os.system("sleep .1s && rm -f /tmp/brightness.lock")

```

Create a file:
/usr/bin/lowerbrightness.py
```

#!/usr/bin/python

import os
import sys


if os.path.isfile("/tmp/brightness.lock"):
	sys.exit(1)

os.system("touch /tmp/brightness.lock")

currentBrightness = open("/proc/acpi/video/VID/LCD/brightness").readlines()[1].strip()
currentBrightness = int(currentBrightness[9:len(currentBrightness)])

newBrightness = 0

if currentBrightness == 100:
	currentBrightness = 96	

if currentBrightness > 12:
	newBrightness = currentBrightness - 12

os.system("echo -n %d > /proc/acpi/video/VID/LCD/brightness" % newBrightness)
os.system("sleep .1s && rm -f /tmp/brightness.lock")

```

[size=4]Sudoers[/size]

You need to add two lines to your sudoers file
You'll need to know:

a) your hostname, find it out via the hostname command in a shell
b) your username .... ..... .....

Now, open up a shell and type "sudo visudo"

The lines you'll add will look like this:
```

username hostname = NOPASSWD:/usr/bin/raisebrightness.py
username hostname = NOPASSWD:/usr/bin/lowerbrightness.py

```
[size=4]Execute a couple commands[/size]
```
sudo chown root:root /usr/bin/lowerbrightness.py /usr/bin/raisebrightness.py
sudo chmod 644 /usr/bin/lowerbrightness.py /usr/bin/raisebrightness.py
```

[size=4]Finishing up[/size]
Create a startup script

In KDE this involves going to ~/.kde/Autostart in Konqueror, creating a launcher - call it whatever you like, just have it execute this command, "xmodmap ~/.xmodmaprc && xbindkeys" ... have it run in a terminal, should be in the advanced options

As per GNOME, XFCE, Fluxbox, and etc, I have no idea.

After this, just log out, log back in, and you should be good to go. Good luck.

---

### Post by timseal on 2007-12-17
Thanks for the detailed guide.  I don't actually need it yet, but Gutsy has been a bit icky on my 1420N so far, so I'll be bookmarking this anyway.

Have you seen any other issues since your upgrade?

---

### Post by natehall on 2007-12-17
Any problems installing Konqueror?

---

### Post by kuja on 2007-12-17
> **timseal said:**
> Thanks for the detailed guide.  I don't actually need it yet, but Gutsy has been a bit icky on my 1420N so far, so I'll be bookmarking this anyway.

Have you seen any other issues since your upgrade?

Well, I have run into some issues with the wireless drive, so I switched to the iwl3945 driver. Apart from that, I've also been experiencing more crashes, mostly the infamous segmentation fault/core dumped, which I've been gettinng randomly from random applications.

---

### Post by timseal on 2007-12-19
> **kuja said:**
>  mostly the infamous segmentation fault/core dumped, which I've been gettinng randomly from random applications.

Ouch, if it's really random then that could mean bad memory.  Or the app might be confused about the upgraded libraries.  Next time, try reinstalling the offending app and all its dependencies.

---

### Post by kuja on 2007-12-19
Don't think it's bad memory, but just in case I'm letting memtest run over night .... so far after a few hours no errors, but I'm going to be paranoid and let it go all night. I'll let you know how things go in the morning. I've never had any trouble with crashyness pre-gutsy .... blah. I've tried reinstalling the apps, but hand picking the dependencies would be a bit troublesome ... I( suppose the only practical way to do that would be to sudo apt-get install --reinstall $(dpkg -l | grep -e ^ii.* | cut -d ' ' -f 3 | tr  '\n' ' ') .... but that seems a bit extreme to me.

---

### Post by timseal on 2007-12-20
Yeah, if it's only just started after the upgrade then it's probably not memory.
Try building something you use a lot, that will give gcc a good workout and you shouldn't see the segfaults on the thing you build.

---

