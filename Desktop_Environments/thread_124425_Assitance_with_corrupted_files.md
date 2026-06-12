---
title: "Assitance with corrupted files"
date: 2006-02-01
forum: Desktop Environments
---

### Post by Leviathan05 on 2006-02-01
I am still new to linux, and Ubuntu.  I am having a problem with my current installation.  It was working fine for the last month, but during a mishap (phone fell of the table and landed on my tower, resetting the installation) I can no longer log in to the GUI GNome interface.

I keep getting this error.
**There was an error load the theme Human**
[COLOR="Red"]Couldn't recognize the image file format for file '/usr/share/gdm/themes/Human/background.png'[/COLOR]

It is then followed by

[COLOR="Red"]There was an error loading the theme and the default theme could not be loaded.  Attempting to start the standard greeter.[/COLOR]

The standard greeter starts, and I cannot enter any credentials to login.


I have checked and the file does exist.  However, I have notice that there are a large number of files in the /lost&found folder.  I have checked the hda and hdb for errors and they are OK.

Can someone please assist me with getting the GUI side working again?  It will not let me login again, except from command line or via SSH.

---

### Post by cwaldbieser on 2006-02-01
[QUOTE=Leviathan05]I am still new to linux, and Ubuntu.  I am having a problem with my current installation.  It was working fine for the last month, but during a mishap (phone fell of the table and landed on my tower, resetting the installation) I can no longer log in to the GUI GNome interface.

I keep getting this error.
**There was an error load the theme Human**
[COLOR="Red"]Couldn't recognize the image file format for file '/usr/share/gdm/themes/Human/background.png'[/COLOR]

It is then followed by

[COLOR="Red"]There was an error loading the theme and the default theme could not be loaded.  Attempting to start the standard greeter.[/COLOR]

The standard greeter starts, and I cannot enter any credentials to login.


I have checked and the file does exist.  However, I have notice that there are a large number of files in the /lost&found folder.  I have checked the hda and hdb for errors and they are OK.

Can someone please assist me with getting the GUI side working again?  It will not let me login again, except from command line or via SSH.[/QUOTE]

Does 
```

$ file /usr/share/gdm/themes/Human/background.png

```
recognize it as a PNG?  If so, are what are the permissions like?

---

### Post by Leviathan05 on 2006-02-01
PNG image data, 1600x1200, 8-bit Color RBG, Interlaced.

Permissions are 777.

Really do not want to have to reload.  Is there anyway that I can use apt-get to force a re-install of the gdm?

---

### Post by cwaldbieser on 2006-02-01
[QUOTE=Leviathan05]PNG image data, 1600x1200, 8-bit Color RBG, Interlaced.

Permissions are 777.

Really do not want to have to reload.  Is there anyway that I can use apt-get to force a re-install of the gdm?[/QUOTE]
```

$ sudo dpkg-reconfigure gdm

```
might do the trick.  Or you could try to "apt-get uninstall gdm" and "apt-get install gdm".  Or you could try installing kdm if that doesn't work.

---

