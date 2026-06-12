---
title: "cdrom won't mount as utf8"
date: 2006-01-19
forum: General Help
---

### Post by Dougal on 2006-01-19
I’ve installed my Ubuntu as UTF-8, yet been having problems reading foreign language (Hebrew) filenames from a cd (created by Wind’oh!). I tried looking up all the ‘options’ for Ubuntu and Nautilus but to no avail.

Eventually I managed to get past the problem manually: 
In an XFCE session (it doesn’t auto-mount like Gnome) I opened a root-terminal (why won’t it let me mount as a non-root user?) and did:
# mount -o utf8 /dev/cdrom /cdrom
Now, looking at /cdrom in the terminal I could see Hebrew characters, albeit in revere order (Hebrew is right-to-left), and when looking at it in Rox all was fine. Same if I now logged out of XFCE and into Gnome and tried Nautilus- Hebrew working properly. (It stays mounted when I log out. In fact, I can never unmount my cdrom- it always gives me a “device is busy” error and the only way to get past it is to reboot. Another bug…)

Anyone know how I can change the “mount” operations of Rox and Nautilus to use “-o utf8”? Are they compiled that way?

---

