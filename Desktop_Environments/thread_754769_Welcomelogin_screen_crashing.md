---
title: "Welcome/login screen crashing"
date: 2008-04-14
forum: Desktop Environments
---

### Post by nife87 on 2008-04-14
Hi

I have tried a couple of Welcome/Login screens, but suddenly I cannot log into Ubuntu (by the graphical interface) any longer, since the chosen screen keeps crashing (I will never try that anymore, I can tell you that much).
It tries to display the login screen 3 times, hereafter it says something along the lines of "It seems like the welcome screen keeps crashing. Trying another". But it seems like it does certainly not try another, since it still keeps crashing. Therefore, I cannot log into Ubuntu.
So, how can this be fixed? Is there a way to reset login settings or something like that from the command line (the tty1-6 still works fine)? Or maybe just change the welcome screen?
I am just looking for a solution lighter than reinstalling Ubuntu :)

---

### Post by nife87 on 2008-04-14
I found the solution by surfing a bit more. I edited /etc/gdm/gdm.conf via one of the consoles and changed the following line:
Greeter=/usr/lib/gdm/gdmgreeter
to
Greeter=/usr/lib/gdm/gdmlogin
to successfully log in and, of course, changed it back afterwards.

---

### Post by warp99 on 2008-04-14
Did you change your graphics drivers recently? If so you may have a problem with the login to your desktop not the login screen. First do the following:

```
sudo apt-get remove --purge gdm
```
this may ask to remove the ubuntu-desktop, but do not be alarmed. This is only a meta-package referring to other packages. If you're unsure about an apt-get operation use the -s parameter for a simulation like this:
```
sudo apt-get -s remove --purge gdm
```
Once that's done reboot the computer, login to the command prompt screen then type 'startx' to run the desktop. If the desktop does not run there is a problem with your graphics drivers, so do the following:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
and choose 'vesa' as you graphics driver, then issue a 'sudo reboot' command. If you can load your desktop with the same 'startx' command after login then do the following
```
sudo apt-get install gdm
```
Then issue a 'sudo reboot' and you'll be back to your login screen

---

