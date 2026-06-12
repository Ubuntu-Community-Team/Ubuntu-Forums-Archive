---
title: "My Keyboard Layout changed to Arabic =&gt; Can't login..."
date: 2009-03-27
forum: General Help
---

### Post by seppl82 on 2009-03-27
Hi all,

unfortunatly however it went, my keyboard language changed to arabic (even in the console).
How can i change it back to German or to US?

Boot from CD and then which file ?

Kind Regards
Seppl

---

### Post by seppl82 on 2009-03-28
bump

---

### Post by albandy on 2009-03-28
when logged with rescue mode or rescue cd
sudo dpkg-reconfigure console-setup

---

### Post by Berserker v7 on 2009-03-28
> **seppl82 said:**
> Hi all,

unfortunatly however it went, my keyboard language changed to arabic (even in the console).
How can i change it back to German or to US?

Boot from CD and then which file ?

Kind Regards
Seppl

Log in using your Ubuntu live cd(for the same version as installed), mount the root partition of your ubuntu install from the live cd and execute the following command in a terminal. Here I am assuming that you mounted this partition onto /media/disk
```
for i in `locate keyboard|grep -v ^/media/disk`;cp $i /media/disk
```
After this, boot into your ubuntu install and your settings should be back to default...

---

### Post by Zimmer on 2009-03-28
What file?...
My guess would be /etc/X11/xorg.conf
and the following section looks like it provides the custom keyboard layout (for me "gb"....for a United Kingdom keyboard.


Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
EndSection

---

### Post by albandy on 2009-03-28
> **Berserker v7 said:**
> Log in using your Ubuntu live cd(for the same version as installed), mount the root partition of your ubuntu install from the live cd and execute the following command in a terminal. Here I am assuming that you mounted this partition onto /media/disk
```
for i in `locate keyboard|grep -v ^/media/disk`;cp $i /media/disk
```
After this, boot into your ubuntu install and your settings should be back to default...

this will copy all files in cd locate database with keyboard pattern. Don't do this!!!! cd it's not as updated as your system and could broke something.

Use the system commands to repair it as said before.

---

### Post by seppl82 on 2009-03-28
Okay,

in /etc/X11/xorg.conf there is no localization listed.

I've found the corresponding entry in 

/etc/default/console-setup

# The following variables describe your keyboard and can have the same
# values as the XkbModel, XkbLayout, XkbVariant and XkbOptions options
# in /etc/X11/xorg.conf.
XKBMODEL="pc105"
XKBLAYOUT="de"
XKBVARIANT=""
XKBOPTIONS=""

---

### Post by albandy on 2009-03-28
if you type sudo dpkg-reconfigure console-setup a text menu will appear alowing you to change your keyboard configuration.

then if you do sudo dpkg-reconfigure xserver-xorg it will ask you the X11 options where you can configure your keyboard.

Simply do this with your filesystem mounted from the rescue cd

---

### Post by alab0 on 2011-03-13
> **seppl82 said:**
> bump
Awsome ;),great work..

---

