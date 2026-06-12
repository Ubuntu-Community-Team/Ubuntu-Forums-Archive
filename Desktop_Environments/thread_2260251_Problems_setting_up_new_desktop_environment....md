---
title: "Problems setting up new desktop environment..."
date: 2015-01-10
forum: Desktop Environments
---

### Post by nicholas18 on 2015-01-10
Hi, this is my first post here- I just switched from windows to Ubuntu 14.04 in October.  This is the first real problem I have had since then....

I tried switching from Unity to Xfce for my desktop environment.  I installed xfce and tried to delete unity, but it only deleted 2 of 97 files I believe.  Now when I try to login it just keeps going back to the login screen and I have to use ctrl+alt+F3, login, then enter sudo startx /usr/bin/startxfce4 and then I end up logged in as root (I can't get the command to work w/o sudo) with no way to choose which wifi to connect to (if it connects by default to my wifi it works, if not I can't seem to change it).  I then reinstalled unity, but that did not fix it so it would log in to unity.  I would rather not completely reformat due to programs which would have to have licenses moved over, etc.  I have searched google for an answer but I've can't find what I know to be the correct answer.  I would ideally like to still get rid of unity and have xfce as my default desktop.

Right now I am stuck using a live usb as my OS.

Thank you in advance for your help

EDIT: I am able to log into a new sudo account I created, and when I log into xfce4 through the command line of the account it goes to root but still has the desktop from the user account (the items on it etc).

---

### Post by buzzingrobot on 2015-01-11
Removing the components of Unity is very difficult/not worth it. It's easy allow the removal of core components and end up with a broken.  

It's also not really necessary. If another desktop environment, like XFCE, is selected at log in, then the Unity bits do not execute.  

When another desktop environment is installed, you need to select it when you log in. (So, if you have opted for automatic login, you need to log out and log back in.)  A right-click on the small icon to the right on the login widget should expose the available interfaces.  Select the one you want.  The system will remember it on subsequent logins.

If you like XFCE, the best approach is to install Xubuntu, which is the Ubuntu spin that uses XFCE instead of Unity. Much less hassle that way.

---

### Post by Frogs Hair on 2015-01-11
Having used XFCE and other desktops along with Unity, I noticed many duplicate applications including different file managers This is a good way to experiment with different desktop environments but not the best solution for a daily user machine.

---

