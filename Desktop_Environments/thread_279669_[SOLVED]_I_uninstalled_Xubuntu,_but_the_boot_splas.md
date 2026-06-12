---
title: "[SOLVED] I uninstalled Xubuntu, but the boot splash &amp;amp; login screens still there!"
date: 2006-10-18
forum: Desktop Environments
---

### Post by bswilson on 2006-10-18
I have Ubuntu 6.06LTS installed with the default gnome environment.  Recently, I decided to test Xubuntu's **xfce** environment by installing the desktop packages:

```
$ sudo apt-get update; sudo apt-get install xubuntu-desktop
```

The installation went just fine, no problems.  But I decided to go back to using **gnome**, no problem.  I know very well how to change my default session and all of that, so again, I figured no sweat.  However, I noticed that the boot splash and login screen are _still_ the ones that came with Xubuntu's desktop environment!  I figured that I needed to uninstall Xubuntu to fix this, so I did this:

```
$ sudo apt-get remove xubuntu-desktop
```

However, whenever I log out and log back in (or reboot), the Xubuntu boot splash and login screen are _still_ there, even though when I log in I am starting the **gnome** environment!

Is there any way to delete restore the default Ubuntu/gnome boot splash and login screen, _**without**_ reinstalling ubuntu-desktop?

---

### Post by bswilson on 2006-10-18
OK, sorry everybody; I apparently did not search hard enough in the forums.  The answer to my question is to open the Login Window applet (System --> Administration --> Login Window).

More details were found here: [http://www.ubuntuforums.org/showthread.php?t=269394]("http://www.ubuntuforums.org/showthread.php?t=269394")

---

### Post by merkur2k on 2006-10-18
I dont know the specifics since I use gfxboot, but the bootsplash stuff will be in /boot/grub/menu.lst. It should be a matter of changing the splash image filename, or changing a symbolic link in the grub directory.
The login manager I dont know the specifics of either since ive never used xubuntu, but I am guessing it needs to be changed from xdm back to gdm. The file /etc/X11/default-display-manager looks promising though.

---

### Post by Roobert on 2006-10-27
Hmm. Is there any way to make the login screen match whatever your last *buntu session was? For example, if I was logged into Ubuntu, log out, get the Ubuntu login screen, then login to Xubuntu, logout, and get the Xubuntu login screen?

~ Roobert.

---

### Post by bswilson on 2007-01-12
Just a quick add-on; you can restore your boot usplash with this command:

```
sudo update-alternatives --config usplash-artwork.so
```

You'll be prompted to switch to another one or restore the original.

---

