---
title: "X Error: BadDevice"
date: 2006-09-13
forum: Desktop Environments
---

### Post by amsch on 2006-09-13
```

X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kbuildsycoca running...
ScimInputContextPlugin()
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0

```

Can anybody please tell me what this means or what I have to do to fix this?

---

### Post by amsch on 2006-09-15
Can nobody help me?

---

### Post by petrusgomes on 2006-10-25
I've heard about wacom device at xorg.conf (etc/X11/xorg.conf)

try to coment the entries of it...

goo luck ;)

---

### Post by novice_forever on 2007-07-15
Thanks a lot for *that* advice.
I did so, which kept me from receiving further error messages, because the system didn't show up **at all**.
](*,)

---

### Post by quux on 2007-07-15
Have you removed the wacom devices from the "ServerLayout" section (stylus, cursor, eraser)?

---

### Post by novice_forever on 2007-07-15
> **quux said:**
> Have you removed the wacom devices from the "ServerLayout" section (stylus, cursor, eraser)?

I had commented out these sections (since they are the only ones where "wacom" appears).

[INDENT][FONT="Courier New"]Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection[/FONT][/INDENT]

After reboot, I was welcomed by a black screen with a blinking cursor whith no reaction to any commands.
In the meantime, I have returned to the original configuration.

---

### Post by quux on 2007-07-15
There's a Section titled "ServerLayout" in xorg.conf (in Ubuntu's default X11 config it's located somewhere near the end of the file). Try commenting out the lines 
```

InputDevice     "stylus" "SendCoreEvents"
InputDevice     "cursor" "SendCoreEvents"
InputDevice     "eraser" "SendCoreEvents"
```

---

### Post by novice_forever on 2007-07-15
Hey, it **works!**
At least, when launching the application as normal user...
However, when doing so as root, I get this:

```
DCOPClient::attachInternal. Attach failed Could not open network socket
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kdeinit: Can't connect to the X Server.
kdeinit: Might not terminate at end of session.
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kded: cannot connect to X server :0.0
DCOP aborting call from 'anonymous-5398' to 'kded'
kded: ERROR: Communication problem with kded, it probably crashed.
QFile::open: No file name specified
```

Still, the application runs allright.

---

### Post by Nythain on 2007-07-15
are you running it as:
root
sudo
or gksu/kdesu

when running graphical apps from the terminal you should ALWAYS use gksudo or kdesu... and i would advise never actually switching user to root for anything really

---

### Post by novice_forever on 2007-07-15
When I want to edit some config files, I have to be root, of course. Instead of editing with vi, I prefer to do this with kate. However, I cannot save the file then, if launching kate from the K-menu. So I usually run ```
sudo kate [config-file-to-edit]
``` which works perfectly, but produces the above mentioned error messages. I was just wondering what they were about.

---

### Post by Nythain on 2007-07-15
yeah, kate is a graphical program... use kdesu instead of sudo... sudo on graphical apps has the potential to jack your system... try kdesu kate file from now on and you should have no problem

---

### Post by novice_forever on 2007-07-15
> **Nythain said:**
> use kdesu instead of sudo
I will! This *really* works.
Thanks a lot!

---

### Post by ossgrouch on 2007-08-10
I went to Adept Package Manager, search and found that Wacom drivers were installed.
After uninstalling the annoying messages disappeared.

Osscar Grouch

---

