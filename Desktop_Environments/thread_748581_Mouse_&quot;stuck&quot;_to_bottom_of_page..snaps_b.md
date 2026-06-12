---
title: "Mouse &quot;stuck&quot; to bottom of page..snaps back there with any movement."
date: 2008-04-07
forum: Desktop Environments
---

### Post by Brotato on 2008-04-07
Okay, this is a very frustrating problem and makes the OS unusuable to me.

My mouse is a Logitech G5 connected via USB

Ubuntu 7.04 my mouse works fine
7.10 the mouse isn't working right, and 8.04 has the same problem.

What happens, and this happens when the OS is installed or if I'm just using the Live CD, is that upon start up whenever I move the mouse it immediately darts to the bottom of the screen. 

I try to move somewhere else and the mouse immediately darts back again. Disconnecting and reconnecting the mouse doesn't fix it.

I don't have a PS/2 mouse to use to check that. My USB keyboard works fine.

So....any ideas? I really would like to use this, but I find it impossible.

It should be noted that I have the same problem in Linux Mint with their newest version. The older one works fine.

---

### Post by metalf8801 on 2008-04-07
Are you using a laptop or does you keyboard have touch pad on it? If so try cleaning it off.

---

### Post by Brotato on 2008-04-07
> **metalf8801 said:**
> Are you using a laptop or does you keyboard have touch pad on it? If so try cleaning it off.

No.

This is a desktop and I'm using a regular keyboard.

Like I said...7.04 the mouse works perfect..7.10 and above it has this issue.

But in 7.04 it doesn't detect my monitor's native resolution.

I am very frustrated.

---

### Post by Brotato on 2008-04-07
I should also mention that the mouse works fine in Vista.

---

### Post by benerivo on 2008-04-07
You could try changing the mouse driver in the /etc/X11/xorg.conf file. There are two driver options I have seen. One is called mouse and the other (and i think the more recent one) is called vmmouse. Try ```
gksudo gedit /etc/X11/xorg.conf
``` and changing the driver, then reboot.

---

### Post by Brotato on 2008-04-07
> **benerivo said:**
> You could try changing the mouse driver in the /etc/X11/xorg.conf file. There are two driver options I have seen. One is called mouse and the other (and i think the more recent one) is called vmmouse. Try ```
gksudo gedit /etc/X11/xorg.conf
``` and changing the driver, then reboot.

Is there any way to do that by just using the Live CD?

The OS isn't currently installed.

---

### Post by benerivo on 2008-04-07
Yes, i think you can dot it as above, but instead of rebooting, you can log out, then press Ctrl+Alt+Backspace (to restart the xserver), then login. You'd have to guess the username and password (i think the username is ubuntu). If you can't do this then try  Ctrl+Alt+Backspace straight from the desktop to see if that works.

---

### Post by Brotato on 2008-04-07
> **benerivo said:**
> Yes, i think you can dot it as above, but instead of rebooting, you can log out, then press Ctrl+Alt+Backspace (to restart the xserver), then login. You'd have to guess the username and password (i think the username is ubuntu). If you can't do this then try  Ctrl+Alt+Backspace straight from the desktop to see if that works.

Okay..I tried it with both drivers and it didn't work. :(

---

### Post by jsmiith on 2008-04-07
you might want to check and see if gutsy uses the same mouse driver in your xorg.conf as feisty. If it autodetected your mouse wrong you might be using the wrong driver.

---

### Post by benerivo on 2008-04-07
This probably won't help, but here are some options that you can add to your xorg file. Add the lines below the 'Driver' line.
```
Option "SendCoreEvents" "true"
Option "CorePointer" "true"
```

---

### Post by Brotato on 2008-04-07
> **jsmiith said:**
> you might want to check and see if gutsy uses the same mouse driver in your xorg.conf as feisty. If it autodetected your mouse wrong you might be using the wrong driver.

Gutsy says vmmouse.

When I tried to change it to just mouse as up above, I ctrl+alt+backspace and the problem persisted. :(

I guess I could load up Feisty and see what the xorg says.

---

### Post by Brotato on 2008-04-07
Hah..well at least I did something.

I changed xorg to:

```
Section "InputDevice"
        Identifier      "Logitech G5"
        Driver          "evdev"
        Option          "Name"          "Logitech USB Gaming Mouse"
        Option          "HWHEELRelativeAxisButtons" "7 6"
EndSection
```

And also:

```
Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
	Inputdevice	"Generic Keyboard"
#	Inputdevice	"Configured Mouse"
        InputDevice     "Logitech G5" "CorePointer"
EndSection
```

And my mouse stopped working completely.

At least it was something differnt.:)

---

### Post by Brotato on 2008-04-07
Bump as I really would like to get this fixed.

---

### Post by Brotato on 2008-04-08
bump

---

### Post by Brotato on 2008-04-08
Bump from page 2.

---

### Post by Brotato on 2008-04-08
Weird..seems as though I fixed my own problem.

I unplugged my wacom tablet and voila..the mouse works as intended....weird.

---

