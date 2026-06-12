---
title: "Is there any &quot;send to USB&quot; script?"
date: 2006-08-07
forum: Desktop Environments
---

### Post by nimes on 2006-08-07
Hi.
i'm looking for "send to usb" script (nautilus). 

any suggest?

---

### Post by Scythe!? on 2006-08-07
Drag and drop to the usb drive?

---

### Post by nimes on 2006-08-07
:) no,
clik with right mouse button to any file and send to usb

very useful in my option

---

### Post by mostwanted on 2006-08-07
It depends on what you mean by USB... =/

---

### Post by nimes on 2006-08-07
usb: kingston, sandisk, data traveler ...etc.(usb storage)

---

### Post by reclusivemonkey on 2006-08-07
> **nimes said:**
> usb: kingston, sandisk, data traveler ...etc.(usb storage)

I can't check this right now as I am at work, but if you look in ~/.gnome2 I believe there is a folder called "nautilus-sendto". I presume if you add a shortcut to a device in there, you can then use the "Send to" context menu.

EDIT: No, sorry this doesn't work. You can however make script with nautilus which will do what you want. I believe there is a program in the repos that will help you with this called nautilus-actions.

---

### Post by mostwanted on 2006-08-08
> **nimes said:**
> usb: kingston, sandisk, data traveler ...etc.(usb storage)

Hm, the problem here would probably be that more USB devices can be plugged in at the same time, but creating a graphical dialog with the different devices on Zenity should be fairly simple. Maybe I'll create one for you, but I can't help but feel it's a bit pointless when you can just drag and drop.

---

### Post by mostwanted on 2006-08-08
Ok, I looked at it and it seems that a USB-key will be mounted to /media/usbdisk/. As long as you don't plug in more than one key at a time, this script should work:

```
#!/bin/bash
# Sends selected files to mounted USB disk

cp -r $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS /media/usbdisk/
```

Save it to a file, make the file executable and put it in ~/.gnome2/nautilus-scripts/. Then reload nautilus (either log out or do a *killall nautilus* in the terminal). Now you should have script available in your right-click menu for sending to your USB-key.

---

