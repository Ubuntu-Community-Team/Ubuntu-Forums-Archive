---
title: "No toolbar"
date: 2009-03-04
forum: Desktop Environments
---

### Post by bkem on 2009-03-04
we have just installed Ubuntu 8.10 and we are using the Gnome desktop.

however no toolbar appears on the desktop screen.

does anyone know how we can get it or what we are missing?

complete beginners here.

---

### Post by Therion on 2009-03-04
Well, language preferences aside, this is what the [default desktop](http://bd-things.net/wp-content/uploads/2008/10/ubuntu-810-default-desktop.jpg) for a fresh install of Intrepid Ibex should look like.

There are two panels on the default Gnome desktop as you will see in the pic; there's the top panel and the bottom panel.  The top panel displays, among other things, the time in the far-right corner and the bottom panel displays, among other things, the trash-can/recycle bin in the far-right corner.

Are you saying you are NOT seeing either of these panels when you boot up your Ubuntu install?

---

### Post by UbuntuNerd on 2009-03-04
try this command in a terminal to reset your panels to default like they were before:
```
gconftool-2 --shutdown
rm -rf ~/.gconf/apps/panel
pkill gnome-panel
```
if that doesn't work you might have to reinstall your desdtop

---

### Post by UbuntuNerd on 2009-03-04
since you said you were a beginer you might not know this, hit (Ctrl Alt f1) to get to the terminal. log in and enter your password and you might have to copy the code to a piece of paper. then enter the first line follow by enter then the second line follow by enter then the third. hit (alt f7) to get back to your desktop.
hope that helps

---

### Post by C-- on 2009-03-04
> **UbuntuNerd said:**
> try this command in a terminal to reset your panels to default like they were before:
```
gconftool-2 --shutdown
rm -rf ~/.gconf/apps/panel
pkill gnome-panel
```
if that doesn't work you might have to reinstall your desdtop

There is a graphical front-end for gconf that can be used to edit gnome profile settings called Sabayon. You can use it to make the toolbar un-delete-able too.

[http://www.linux.com/feature/114319](http://www.linux.com/feature/114319)

You can probably get it with ```
sudo apt-get sabayon
``` in the terminal.

It should help if you have issues like this in the future, so you can better understand what the commands are doing.

---

