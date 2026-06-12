---
title: "[SOLVED] FVWM-Crystal Menus"
date: 2008-06-01
forum: Desktop Environments
---

### Post by Phonan on 2008-06-01
I wasn't sure where to post this, as I'm running on a PowerPC iMac, but this question has to do with FVWM-Crystal, so here goes. I started with a CLI install of Ubuntu, and then I installed FVWM-Crystal. I've now installed some more programs, like rox-filer for my desktop, Firefox, Pidgin, and VLC. My problem is that none of these but rox show up in the auto-generated FVWM-Crystal menus. I've tried googling this to no avail. My menu still shows: the FVWM-Crystal prefs menu, "Flock" (which I have not installed,) and my "System" menu with Xterm, XFCE4 Terminal, Midnight Commander, Rox-filer and Aptitude. No Firefox, VLC, etc. Can someone give me some advice as to how I can get these to show up in the menus? If not, that's okay, as I put shell scripts to launch them on my desktop. However, I'd really like to get this to work. Thanks.

---

### Post by angry_johnnie on 2008-06-01
Maybe this:

```
sudo apt-get install menu && sudo update-menus
```

It will then look for anything that is menu-sensitive and include it.

---

### Post by Phonan on 2008-06-02
Thanks very much, I'll give that a shot. And by the way, LOL at your sig.

EDIT:Man, I feel like an idiot for not trying that before. Thanks much angry_johnnie! My menus are working perfectly now.

---

### Post by linuxvacuum on 2008-09-20
Great information! I have been looking for that for a while, so thanks!

---

