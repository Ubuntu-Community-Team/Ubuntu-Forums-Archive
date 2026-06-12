---
title: "Screen Saver Changes Mouse and Internet Connection"
date: 2005-02-20
forum: Desktop Environments
---

### Post by El Guapo on 2005-02-20
Every time after the screen saver has been on the the mouse icon turns black and the internet connection basically turns off.  Using ifconfig shows the connection to still be active but i cannot access any web pages.  It takes a reboot of the computer to get it working again, simply re-starting GNOME (ctrl-alt-backspace).

Any ideas?

---

### Post by kassetra on 2005-02-20
Do you have a Rage 128 video card by any chance?

---

### Post by El Guapo on 2005-02-21
I do, Rage Fury 128 Pro. This doesn't sound promising.   :-? 

Do you know of a fix for this?

---

### Post by kassetra on 2005-02-21
[QUOTE=El Guapo]I do, Rage Fury 128 Pro. This doesn't sound promising.   :-? 

Do you know of a fix for this?[/QUOTE]

Possibly:
You'll need to edit your X server config file.
Are you using Hoary or Warty?

---

### Post by El Guapo on 2005-02-22
I'm using warty.  I was going to wait until Hoary was officially released.

---

### Post by kassetra on 2005-02-22
[QUOTE=El Guapo]I'm using warty.  I was going to wait until Hoary was officially released.[/QUOTE]

Ok, then here is what you need to do:  ( I needed to know which version so I didn't give you the wrong directions)

1. Make a backup copy of your current XF86Config-4 file:
 ```
sudo cp /etc/X11/XF86Config-4 /etc/X11/XF86Config-4.0
``` 

2. Open your XF86Config-4 file for editing:
 ```
sudo gedit /etc/X11/XF86Config-4
``` 

3. Find the line that says Section "Device"
4. Add this into that section:
 ```
Option "SWCursor"
``` 
5. Save & Close the file.
6. Reboot your computer.

That *should* fix the problem, it's a bug in the ATI driver for your card...

---

