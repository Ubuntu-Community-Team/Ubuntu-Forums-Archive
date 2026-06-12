---
title: "USB Ports do not Resume Properly (Dell 1420n/Hardy)"
date: 2008-05-04
forum: Dell Ubuntu Support (CLOSED)
---

### Post by aidave on 2008-05-04
When coming back from resume, the USB ports are not waking up right.  They are giving power to the mouse, but does not appear to be acknowledging its presence.  This happens with different USB mice.  

The only solution for now seems to be unplugging the mouse and plugging it into a different USB port.  If I plug it back into the same port, it still does not work.

This isnt a major problem but it is a problem.. does anyone else experience this?

---

### Post by aidave on 2008-05-05
bump

---

### Post by AaronMT on 2008-05-05
What if you type ```
lsusb
``` in a terminal right after you return from suspend? Do they work then?

---

### Post by aidave on 2008-05-05
Wow, that works!  Thanks!

How do I get it to do that automatically?

---

### Post by aidave on 2008-05-06
bump

---

### Post by publicskill on 2008-05-06
I had similar problem with suspending system. After resuming my USB just didn't work. Try clues from this thread

**_[http://ubuntuforums.org/showthread.php?p=4895237#post4895237](http://ubuntuforums.org/showthread.php?p=4895237#post4895237)_**

Maybe this will help you...

---

### Post by aidave on 2008-05-10
Thanks for the link.  I experimented until it worked. 
Here is the solution that worked for me:

cd /usr/lib/pm-utils/sleep.d
sudo touch 98usb
sudo chmod +x 98usb
gksudo gedit 98usb

```

#!/bin/sh

case "$1" in
   resume|thaw)
      lsusb
      ;;
   *)
      ;;
esac

```

---

### Post by aidave on 2008-07-04
Still have this issue even with 8.04.1, but the fix above works.

---

