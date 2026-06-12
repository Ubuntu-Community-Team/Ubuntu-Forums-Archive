---
title: "Where does Ubuntu Mount CIFS though GUI?"
date: 2009-06-02
forum: General Help
---

### Post by alime on 2009-06-02
I used Places > Connect to Server to connect to a samba share using CIFS. 

Now i want to use the terminal to copy some files. Where does the GUI mount the shared Drive. 

I looked in /mnt and /media but was unable to find the mounted share other than the link on the desktop though the GUI.

Thanks,
Aaron

---

### Post by KeyserSoze93 on 2009-06-02
It is a while since I've used the GUI to mount shares, but AFAIK all GNOME Virtual File Systems (CIFS, SSHFS etc.) are in ~/.gvfs (it's a hidden dir)

Hope it helps...

---

### Post by alime on 2009-06-04
That was it. Thanks.

---

### Post by mperrin on 2009-08-12
At least gnome mounts them, although the location isn't obvious. That is not the case with KDE as far as I can tell, and XFCE does not have a network browser. Personally, I prefer to have cifs shares mounted automatically to rationally named directories where I can access them easily from the command line. Attached is my cifs management system.

These scripts provide a convenient way to automatically mount
samba/Windows shares when the user logs in, with the option for each
share to be disconnected or remain mounted when the user logs out.
This capability is useful for:
- Making shares available in console sessions and remote logins, or
  desktops such as XFCE that don't provide share browsing through the
  file manager.
- Making shares available to command line operations and scripts
  on desktops like KDE that let you browse and manipulate shares
  graphically, but don't actually mount them.
- Making shares more obvious and accessible to the command line and
  scripts on desktops like gnome that browse and mount them, but in
  obscure places like ~/.gvfs/My\ Share\ on\ SomeServer.
- Keeping shares mounted for background processes and cron jobs when
  you log out of the graphical environment.

They have been tested on Ubuntu 8.04 and 9.04, Xubuntu 9.04,
Fedora 10 and 11, openSUSE 11.1, PCLinuxOS 2009.2, and Slackware 12.2.

I hope you find them useful.

---

