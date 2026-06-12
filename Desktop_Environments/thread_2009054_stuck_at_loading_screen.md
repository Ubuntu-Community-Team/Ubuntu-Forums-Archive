---
title: "stuck at loading screen"
date: 2012-06-23
forum: Desktop Environments
---

### Post by Apataki on 2012-06-23
I installed Ubuntu on my new Dell laptop and for a few days everything was ok. Once I started my computer I saw "your system is running in low graphics mode" window and then some window with four buttons, which I couldn't choose (it didn't react).  I have no idea why it came up,  I installed a few programs earlier, but nothing strange, all from Ubuntu Software Center...
Anyway, I reinstalled ubuntu-desktop, gdm and fglrx and now when I start Ubuntu it gets stuck at loading screen with five blinking dots. When I press "Ctrl + Alt + F1" I normally get into Terminal and I can log in. After typing "startx" Gnome desktop starts and I can work (although it looks a different than previously, some different icons, Dash taking only a part of screen).
I tried removing fglrx and installing it again and repeating it again... And it didn't magically fix ;) I have no idea what to do, please help

---

### Post by nipunshakya on 2012-06-23
have you tried to install graphics drivers from 'additional drivers' utility ?? install the 'additional drivers' from software center and then it will search for any missing driver from your machine. Install them and restart... see what happens....

Happy Linuxing

---

### Post by Apataki on 2012-06-23
Yes, I tried installing fglrx manually and using "additional drivers" and it was the same. 

But now I installed it from additional drivers again and after typing "startx" I didn't get my desktop... Just something like "Caught signal 11. Server aborting".
So I used ```
sudo apt-get purge fglrx
sudo reboot
``` ...and I didn't get anything, just black screen. But after pressing power button my computer restarted and again got stuck at loading screen.

And now I even don't know if I have fglrx installed or not :|

---

### Post by nipunshakya on 2012-06-23
Have u looked at the following link? that may be helpful..
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

