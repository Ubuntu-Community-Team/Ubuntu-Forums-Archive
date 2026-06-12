---
title: "GDM Logout Issue/Error Log Question"
date: 2006-06-29
forum: Desktop Environments
---

### Post by tokyo on 2006-06-29
when logging out from my Gnome session to get to my GDM, it loads a screen that somewhat resembles the GDM, but is devoid of text or form (sans the bg color and the grey where the login box should be)

i thumbed through the search results on the forums, and i got a clue to find the log file.  so i purposely made it error to make a fresh log in the /var/gdm directory, and these are the errors that i found

```
(EE) fglrx(0): Hardware already been locked.
error opening security policy file /etc/X11/xserver/SecurityPolicy

(EE) xf86OpenSerial: Cannot open device /dev/wacom
        No such file or directory.

```

i combed through a few google searches but im coming up dry as to a reason for this error.  if anyone can give me some more information, that would be great.  cheers.

edit: i found some information on wacom, seems to be an open source project to integrate the Wacom brand tablet PCs with linux.  still not sure how that applies to me (im running a laptop, not a tablet)

---

### Post by Maggot on 2006-06-29
I had the same problem, so went into /etc/X11/xorg.conf and commented out all those references to wacom. Its for tablets.

---

### Post by tokyo on 2006-06-29
[QUOTE=Maggot]I had the same problem, so went into /etc/X11/xorg.conf and commented out all those references to wacom. Its for tablets.[/QUOTE]

thank you for the response.  i tried commenting out the whole sections themselves, and also only commenting out the parts where wacom appears, but both made xorg error on boot.  here is the portion of my xorg.conf where wacom appears (this is the version of the file that caused my initial error, not the xorg errors), if you could show me where you editted it, that would be great.

```
Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

```

---

### Post by tokyo on 2006-06-29
thanks for the suggestion Maggot, after a bit of playing around and only commenting out certain things, i finally got it to work.  for future reference if anyone searches this topic, i commented out the following line:

every occurance of this line (in my xorg.conf file there were 2)
```
Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
```

---

### Post by cury on 2006-11-16
Tokyo,
it worked perfectly for me, thanks for the tip!! :mrgreen:

---

