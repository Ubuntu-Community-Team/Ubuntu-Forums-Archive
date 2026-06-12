---
title: "Continuously asked to log in"
date: 2011-01-16
forum: Desktop Environments
---

### Post by Grujah on 2011-01-16
I booted to Windows, and when I booted back to Ubuntu log-in splash screen came up - which was weird cause normally its disabled and logs in automatically. When I enter username and password it just goes back to log-in screen.
I can log in via command line.
When I log in in recovery mode, and do "startx" it get black screen with my cursor only.

Could anyone please help?

---

### Post by grahammechanical on 2011-01-16
Speaking from my own experience I would say that your graphic card could be overheating. It happened to me. The card would not pass the monitor configuration settings to the xserver. In the end I could not even run a live CD.

Regards.

---

### Post by Grujah on 2011-01-17
Yeah, I couldn't start liveCD either. Also, while I was in Windows I got the Blue Screen of Death.

---

### Post by Grujah on 2011-01-17
I just got back home. My computer was turned off for the night and I still have the same problem. If the Graphic Card was overheating, shouldn't I be able to turn on Ubuntu now considering that it certainly did cool down by now? Also, I'm running Windows and it doesn't work any worse than usual.

---

### Post by Grujah on 2011-01-17
I've installed a fresh install on unused partition that I had laying around so now I can boot into Linux sucesfully. Though I'd still like to restore my old install, so if anyone has any ideas how, share.;)

---

### Post by Krytarik on 2011-01-17
It may be

a) a video driver issue: to test it, rename the file "/etc/X11/xorg.conf" from the console.
```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf-backup-17.01.2011
```b) an issue with the user profile: to test those, create a new user, reboot and try to login with those, alternatively you could login at the console and then startx.
```
sudo useradd NEW_USER
sudo passwd NEW_USER
```

---

### Post by Grujah on 2011-01-19
I tried making a new user, its even worse. When I tried to log in with old one, it would show a black screen with little text cursor in top and than return. With new user, the login menu disapears, but I am left with default background and mouse pointer.

As for xorg.conf - when i tried to move it, it wasn't even there, there was only xorg.conf-failsafe.

---

### Post by Krytarik on 2011-01-19
Have you tried to boot into failsafe graphics mode? If not, choose "recovery mode" at the boot menu, then the aforementioned.

---

### Post by Krytarik on 2011-01-19
double post due to forum error

---

### Post by Grujah on 2011-01-19
Tried. No dice.

---

### Post by Grujah on 2011-01-19
Tried. No dice.

---

### Post by Grujah on 2011-01-19
Tried. No dice. Get only mouse cursor on black screen.

---

### Post by Grujah on 2011-01-19
/

---

### Post by Grujah on 2011-01-19
Tried. No dice. Get only mouse cursor on black screen.

---

### Post by Krytarik on 2011-01-19
A short web search didn't turn up any obvious solution, so my suggestion is to try to fix broken packages, if any, by
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get --fix-broken install
sudo apt-get --fix-missing install

```
And we should have a look at "/var/log/Xorg.0.log" for valuable error messages.

There is also an option at the login screen to login to "failsafe Gnome", try those.

---

### Post by larka06 on 2011-01-30
I to had this problem awhile back. I finally found out it was evolution asking to the continues login because I had set it to sync but had not told it to remember the login and password. This may mot apply to you but, it appears all else has been tried.

---

