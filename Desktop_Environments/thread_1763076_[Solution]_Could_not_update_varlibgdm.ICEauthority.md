---
title: "[Solution] Could not update /var/lib/gdm/.ICEauthority"
date: 2011-05-20
forum: Desktop Environments
---

### Post by OlanK on 2011-05-20
I use Ubuntu 9.10, but I'm sure this solution carries over to other releases.

You will likely receive an error about gconf-sanity-check along with the .ICEauthority error.

Reboot: Press ESC after your BIOS has booted to reach the grub recovery menu. Choose root from the list.

```
chown gdm:gdm -R /var/lib/gdm
chmod 600 /var/lib/gdm/.ICEauthority
mv /home/*username*/.ICEauthority /home/*username*/.ICEauthority.old
chmod 1777 /tmp
```

Change the "*username*" to your username.

This should fix the problem, or at least, it did for me.

---

