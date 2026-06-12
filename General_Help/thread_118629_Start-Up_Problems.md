---
title: "Start-Up Problems"
date: 2006-01-17
forum: General Help
---

### Post by steve_linux on 2006-01-17
Hello,
    I am quite experienced with computers, but a complete beginner with regards to Linux.
    I have ditched Windows completely and have installed Ubuntu 5.10. I have been progressing well and generally I am very happy with Linux.
    Now the problem!!!!! When I start the computer it boots O.K. (User, Password, Splash Screen etc.), but when it reaches the splash screen with "window manager" and the icon of two windows(?) it hangs. Nothing happens at all. If I key "Ctrl, Alt, Delete" the computer continues to boot as normal and everything else appears to be fine. This problem does not seem to have coinsided with the installation of any software.

   Thanks in advance for your help.
   Regards Steve

---

### Post by lamego on 2006-01-17
Did it ever booted without that problem ?
You may have a problematic program running on your gnome session.
On a terminal shell just add a new user with the command:

sudo useradd test
Give it a password:
sudo passwd test

Then logoff and login with the new user.

---

