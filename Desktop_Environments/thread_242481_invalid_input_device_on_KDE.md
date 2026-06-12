---
title: "invalid input device on KDE"
date: 2006-08-23
forum: Desktop Environments
---

### Post by loserboy on 2006-08-23
i just installed kubuntu for the 1st time last night. (been using gnome for a lil while now).
anyway at certain times in terminal after running commands it will say

```
 X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

```

it doesnt seem to effect anything negatively, isnt it a keyboard error?
it'd be nice if someone could tell me what to do, thanks

also if it matters i have a usb keyboard (in case it actually is a keyboard error)

---

### Post by Jucato on 2006-08-23
Try if this solution works for you:

[http://kubuntuforums.net/forums/index.php?topic=7964.0](http://kubuntuforums.net/forums/index.php?topic=7964.0)

---

### Post by loserboy on 2006-08-24
is it telling me to comment out that entire input device section?

---

### Post by Jucato on 2006-08-24
Yep. At least the lines that are supposed to be for Wacom's, which I guess you don't have, hence the errors.

---

### Post by loserboy on 2006-08-24
hmm, no workie    now i cant boot  to kubuntu.... what text editor does kde use at command line?

---

### Post by Jucato on 2006-08-24
you can use nano.

```
sudo nano /etc/X11/xorg.conf
```

Once you get things working again, could you post your xorg.conf?

---

### Post by loserboy on 2006-08-24
will do,  i'm at work right now though so it'll be tonight

thanks for the help so far.

---

### Post by Jucato on 2006-08-24
Btw, if these error message don't seem  to be doing anything wrong, it would be best to probably leave them alone, following the saying, "if it ain't broke, don't fix it".

You are not the only one having these error messages, but they seem to be generally harmless.

---

### Post by loserboy on 2006-08-24
it must be something obsessive compulsive in me, but if i see that error a few more times i think i'll explode.

---

