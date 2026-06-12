---
title: "how to switch sessions from KDE to Gnome"
date: 2011-03-06
forum: Desktop Environments
---

### Post by edroid on 2011-03-06
I installed Ubuntu 10.10 64bit as a VirtualBox guest with openSUSE 11.3 as host OS.  Immediately after installing all the latest updates, I issued: "sudo apt-get install kubuntu-desktop" and - when asked - I chose gdm as the window manager.

KDE installed without error, but I was never offered the 'session' option when either restarting or logging out - it would only restart the Gnome desktop.

So I nosed around the System menus - found a login configuration utility and changed it to boot KDE by default.  Now I have the opposite problem:  I can't find a way to start a Gnome session.

---

### Post by ankspo71 on 2011-03-06
Hi,
After you log out, click on your username first, then some menus will appear at the bottom of the login screen, then choose KDE or Gnome (or Kubuntu or Ubuntu) from the session menu at the bottom of the screen, then enter your password to continue logging in to your chosen desktop.
Hope this helps

---

### Post by edroid on 2011-03-06
Thanks for the information, ankspo71, but I cannot get the menus to appear by clicking on my username after log out - maybe because this ia a virtual guest?  I have learned that by changing the
"System->Login Screen Settings->Select Default Session" I can change from Kubuntu to Ubuntu and vice-versa.  Guess that will have to do.

---

