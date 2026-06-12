---
title: "File Manager Not Responding on quit"
date: 2011-01-10
forum: Desktop Environments
---

### Post by quandry247 on 2011-01-10
Lynx amd64

Honestly don't know what to make of this, any advise is appreciated. Is the error report below the result of one problem or many?

--- cut from terminal 8< ---

me247@my-desktop:~$ nautilus
Xlib:  extension "RANDR" missing on display ":0.1".
Xlib:  extension "RANDR" missing on display ":0.1".

(nautilus:2076): Unique-DBus-WARNING **: Error while sending message: Message did not receive a reply (timeout by message bus)

(nautilus:2076): Unique-DBus-WARNING **: Error while sending message: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

--- >8 end of paste ---


File Manager Not Responding - error shows when shutting down or re-booting

I can't suss out if this is a X server problem or Nautilus.
The system is defiantly slower to boot-up, one of the two VDUs I use is rotated counter clockwise and has been for a long time before I tried installing the Elementary-Theme  ([http://www.elementary-project.com/](http://www.elementary-project.com/))

Since then I've had issues mounting/unmounting NTFS drives, viewing the Wastebasket and other locations in my Places.

I've removed Elementary-Theme, Compiz and re-installed Nautilus to no-avail.

Looking for some sage support before ditching the whole lot and re-installing from scratch.

---

### Post by quandry247 on 2011-01-10
Turns out that the Elementry-Theme has issues with duel screen set-ups. 
Ditched my second VDU in favour of eye-candy, but not before I'd removed Nautilus completely and rebooted. For those of you who don't know, THAT'S BAD.

thankfully -
**apt-get install ubuntu-desktop**
- was my friend when entered from the recovery option and dropping to the root user.

---

