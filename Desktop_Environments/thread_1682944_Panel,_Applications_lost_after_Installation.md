---
title: "Panel, Applications lost after Installation"
date: 2011-02-06
forum: Desktop Environments
---

### Post by knuthf on 2011-02-06
New Bug...

I have a MacBook, and installed Ubuntu for many reasons. This is a great combination: the quality hardware of Apple with the enormous software pool of Linux - including Wine, allowing Windows emulation.

However: After installing, removing things and adding applications suddenly the menu's were lost. I had set to automatic Log-in, so the recovery was out of reach. What you have is the background screen and an icon of the computer.

Click on the computer, and you will launch Nautilus.
Here, click on "usr" and "bin" - /usr/bin/
Find "gnome-panel" - and start it by double click.

In my case, it was not there, just the tool to configure it.
Find gnome-terminal, and start this.
Type: 
> sudo apt-get gnome-panel
Password: 

Then go to the Nautilus file manager, and you will find "gnome-panel" in /usr/bin. Start this - and the menus come back.

Now, you have to reboot, and this time it will come back.

My debugging of my own setting exposed that a number of variables that you should consider "mandatory" was not set such as the placement of the panel. This was (-1,-1) - or "any place". 

This may relate to MacBook only, the screen is large and may cause a buffer over-run. It may also be caused by not going through any log-in procedure.

Related tags:
Menu missing, Applications lost, Taskbar gone, Everything lost.

Should you encounter the same, please trace what you do / have done that may have caused this. Very few just take another laptop and search, most muck around for a while, and stumble upon the answer. Please amend below what you did. Remember: Mac / PC, and Ubuntu 10.10, and if PC, video card.

---

