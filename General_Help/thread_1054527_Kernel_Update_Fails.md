---
title: "Kernel Update Fails"
date: 2009-01-29
forum: General Help
---

### Post by ItsJweed on 2009-01-29
I've gone and done something really moronic and I can't seem to track down a solution. Here is what happened:

1) I'm running Ubuntu with dm-crypt and my /boot partition is on a usb flash drive.
2) I had edited /etc/rc.local to unmount /boot so that after the system was running I could remove my flash drive.
3) I ran aptitude safe-upgrade forgetting that /boot was inaccessible.
4) The error generated is attached.

5) I've tried re-running aptitude safe-upgrade with /boot mounted to no avail - same error message. (I've attached it as well.)

6) I tried ```
sudo dpkg --configure -a
``` and ```
sudo apt-get -f install
``` to no avail.
7) ???
8 ) Profit

What do I do? Feel free to criticize me for doing something so dumb in the first place.

---

### Post by dcstar on 2009-01-29
> **ItsJweed said:**
> I've gone and done something really moronic and I can't seem to track down a solution. Here is what happened:

1) I'm running Ubuntu with dm-crypt and my /boot partition is on a usb flash drive.
2) I had edited /etc/rc.local to unmount /boot so that after the system was running I could remove my flash drive.
3) I ran aptitude safe-upgrade forgetting that /boot was unaccessible.
.......

Remove then reinstall the package that did not install.

---

