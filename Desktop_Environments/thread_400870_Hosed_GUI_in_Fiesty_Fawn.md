---
title: "Hosed GUI in Fiesty Fawn"
date: 2007-04-04
forum: Desktop Environments
---

### Post by gkrugerradar1 on 2007-04-04
After 3 days of sweating, and fighting wireless issues, finally got Fiesty Fawn up and running. I love it. Tried the new desktop effects(they warn you that it doesn't work on all machines, BETA, my desktop went blank, or rather all white, and thats where I am stuck. It totally locks up. I can start in recovery mode and get to command prompt. Tried to delete, reinstall Gnome, Nautilus GUI to no avail. Also read ton's of forums. Help. 

Compaq 2410 XP dual boot, AMD64, ATI Xpress 200, 512 Ram, Broadcom 4316,(still doesn't work, using Buffalo wli-cb-g45-hp.
 
PS, I think Fiesty Fawn is finally the release to win a lot of folks over to Linux. Good-bye Bill G. and Steve J.

---

### Post by RaZer0r on 2007-04-04
tried to do dpkg-reconfigure xserver-xorg?
or remove beryl and try again, i'm not sure what's causing the problem atm but it seems that bery messed up your gdm... if you have put it to an startup session, try and remove it, although i'm not sure where to find it using console... i'll look it up in a minute

---

### Post by gkrugerradar1 on 2007-04-04
Thanks for the prompt response. I'm a newbie. What is Beryl? Even if I could uninstall Gnome and reinstall KDE, that would be fine. But the steps I tried didn't work. After all that work, it would be a pity if I had to reinstall Fiesty Fawn. The wife is getting pi**ed at me.

---

### Post by WernerBrandt on 2007-04-04
Its not beryl, its compiz...

---

### Post by GS2 on 2007-04-10
Just had this experience myself on the Ubuntu Feisty Beta

Could not log in to an account that had enabled the 'desktop effects'.

Solution was to log in to the 'failsafe terminal' in GNOME as that user.

log in as root (not sudo) - I used the command 'sudo bash'

The type the following in the terminal:
```
dpkg --get-selections | egrep '[[:space:]]install$' | cut -f 1 | xargs apt-get install --reinstall
```

This will rebuild your system, and get rid of the white screen - a bit excessive but works a treat.

I had already tried deleting the Gnome files in /home/username/ without success.

---

