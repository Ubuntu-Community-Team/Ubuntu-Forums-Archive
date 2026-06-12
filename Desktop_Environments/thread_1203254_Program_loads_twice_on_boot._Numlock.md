---
title: "Program loads twice on boot. Numlock?"
date: 2009-07-03
forum: Desktop Environments
---

### Post by siabost on 2009-07-03
Hi,

I have Kubuntu (KDE4) currently on one of my desktops.

I use aMSN (loaded from the repo) as my Internet Messenger which contains two accounts. We only use one account at a time depending on who's at the computer.

On booting the system into KDE4 it always loads up two instances of aMSN. In Gnome it only loads the one i.e. what I'm after.

How do I change this behaviour in KDE4?

Also: how do I get NumberLock to come on at boot in KDE4?
And: as the comp is only used by me & my partner, is it possible to get it to auto-connect to my wireless network without having to enter a password to allow access to the Wallet?

These are just niggling issues but any help would be appreciated.

Thanks.

---

### Post by Gamall on 2009-07-04
> Also: how do I get NumberLock to come on at boot in KDE4?

System Settings > Keyboard & Mouse > Keyboard > Numlock on KDE startup :)

---

### Post by txcrackers on 2009-07-04
If you've added it to the Autostart **and** you're running the application when you log out, on next startup/login the KDE manager will start the program twice (once for Auto and once for the saved session).

---

### Post by siabost on 2009-07-05
txcrackers - I will have a look at that re the double loading at start up. Thanks.

Gamall - The only options under Mouse & Keyboard in KDE4 are "Mouse", "Joystick", "Standard Keyboard Shortcuts" & "Global Keyboard Shortcuts", none of which make any mention of Number Lock that I can see! :(

---

### Post by Gamall on 2009-07-08
> **siabost said:**
> Gamall - The only options under Mouse & Keyboard in KDE4 are "Mouse", "Joystick", "Standard Keyboard Shortcuts" & "Global Keyboard Shortcuts", none of which make any mention of Number Lock that I can see! :(

Which version of KDE4 are you using? I have 4.2.2 and Jaunty --- according to your profile, so do you ---, and beside "Mouse", "Joystick" etc, I also have a "Keyboard" category; see attachment.

---

### Post by siabost on 2009-07-08
H Gamall,

Picture of my keyboard & mouse settings panel - no keyboard section!

I'm on the same version as you - KDE 4.2.2.

Puzzling. Any ideas?

Thanks

---

### Post by Gamall on 2009-07-08
Apparently this is a known bug:

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=524506](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=524506)

Presumably this has been fixed, and if you update your system you will get the module back :? (sudo apt-get upgrade)

**edit**: if all else fails, try the command *kcmshell4 keyboard*, which should show keyboard settings directly.

---

### Post by siabost on 2009-07-09
Hi,

Thanks for the bug link.

It seems that it's a bug that only occurs when you have Gnome & KDE desktops on the same machine. Both keyboard control panels have the same name in the software and the conflict prevents it loading.

This is resolved in KDE4.2.3 but that's not in the Ubuntu repos yet so upgrading via that method doesn't change anything.

I noticed on the Kubuntu website that KDE4.3 RC is available for Jaunty but I'm not sure what "Release Candidate" means in terms of stability? Is it one step up from "beta"?

Possibly better to wait for it to appear in the repos?

In the meantime I've resolved the number lock issue by installing Numlockx via Synaptic.

Thanks

---

### Post by Gamall on 2009-07-09
> I noticed on the Kubuntu website that KDE4.3 RC is available for Jaunty but I'm not sure what "Release Candidate" means in terms of stability? Is it one step up from "beta"?

"Release Candidate" designates a version which *might* become the final version if no serious bugs are found in it. It is intended for somewhat wider testing than Betas are, but is still definitely not recommended for the casual user.

I don't think installing an RC in order to fix a bug would be a sane course of action ;)

---

### Post by siabost on 2009-07-10
Advice taken.

Thanks. :guitar:

---

