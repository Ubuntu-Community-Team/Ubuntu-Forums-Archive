---
title: "cursor changes to hand and won't function"
date: 2012-07-14
forum: Desktop Environments
---

### Post by sofasurfer on 2012-07-14
10.04
Eventially my cursor always changes to a hand (the "move" tool) and will not function, although I can still move it around. The keyboard functions properly but the mouse is kaput until I do a reboot.

Also, sometimes when I place my cursor on a tab the tab reacts by jumping to a new window. This may be related as both situations are insane. Do you know what my problem is?

---

### Post by sofasurfer on 2012-07-14
I also notice that if I have multiple windows open when I shut down, when I restart and click on the firefox icon ALL of the windows reopen, not just one.

---

### Post by Rexilion on 2012-07-14
Most likely a problem in the window manager which handles the focus. Which one are you using?

---

### Post by sofasurfer on 2012-07-15
Thanks.
I ran sudo apt-get install --reinstall gnome-shell
and it seems to be fixed.

---

### Post by sofasurfer on 2012-07-15
Before I did the above fix, I changed my default window manager to KDE to see if that worked properly. What I did was to install "menu" and the when I saw that KDE was not an option I installed KDE. During setup I was asked if I wanted it to be the default manager. I chose "yes". Now I do not like KDE and I want Gnome back as default.When I reboot the menu comes up and I choose Gnome but I do not want to have to choose it every time. I want Gnome as default. How do I do that?

---

### Post by sofasurfer on 2012-07-15
This sucks. I thought I had it. I removed "menu". I removed "kubuntu" I still get the kubuntu login screen when I boot up. I login and then gnome desktop comes up.
How do I get rid of the login?

---

### Post by Rexilion on 2012-08-25
You are going to be more specific. Removing the 'login' is possible, i.e. you boot your computer and your desktop pops up without any login at all.

But I'm confused, do you want to get rid of the KDE program that is handling your login (KDM)? Or do you want to get rid of the default KDE option in the login manager? Or (maybe, but not likely) want to get rid of the KDE theming in your login manager?

---

### Post by SantaFe on 2012-08-25
If it's the Login Screen you want to change, maybe this will help? [http://linuxandfriends.com/2008/09/06/change-default-display-manager-ubuntu-linux/](http://linuxandfriends.com/2008/09/06/change-default-display-manager-ubuntu-linux/)

Method 2 might be easier.

> Method 2 : Changing the display manager using a tool

This method applies to all Debian based Linux distributions. Fire up a terminal and type the following :

$ **sudo dpkg-reconfigure gdm**

Substitute your current display manager in place of gdm above. And you will be walked through the necessary steps.  Try it using kdm & you should be able to pick the original one from the list shown.

---

