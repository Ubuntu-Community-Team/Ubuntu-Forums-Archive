---
title: "GDM Theme tutorials ?"
date: 2011-03-14
forum: Desktop Environments
---

### Post by FrankenCub on 2011-03-14
I've been looking around at a lot of different log in screens and although there are some sweet screens, none of them just trip my trigger lol. Are there any tutorials somewhere where I can build one up from scratch myself ? It may be beyond my realm and my have to pick some other's brains but I'll never learn if I don't try, right ?! Any thoughts ?

---

### Post by Krytarik on 2011-03-14
Unfortunately with the current version of GDM you can't tweak the look of the login screen as much as in the past. Please see the first part of my earlier post:
[http://ubuntuforums.org/showthread.php?p=10468340](http://ubuntuforums.org/showthread.php?p=10468340)

Greetings.

---

### Post by FrankenCub on 2011-03-14
So the log in themes from [HERE]("http://gnome-look.org/index.php?xcontentmode=150"), for example, aren't compatible with Ubuntu 10.10 ? I was think more in the lines of completely building one from scratch, I guess like those were done. I have found how to change the background pics in them, unless that also isn't compatible with 10.10, but I thought a few other changes would be nice like different text in the log in box. Ok, so maybe I might be somewhat :confused:

---

### Post by Krytarik on 2011-03-14
The link target is currently unresponsive, but anything other than *normal* desktop themes can't be applied.

---

### Post by FrankenCub on 2011-03-14
Oh, how bout that. Is was a link to GDM Themes at gnome.look
There's a lot of different log in screens there.

---

### Post by wojox on 2011-03-14
The link is broke, but if you want to use those themes you have to use a distro that doesn't include Plymouth.

---

### Post by FrankenCub on 2011-03-14
Ahh ok, I like Ubuntu 10.10 too much to change now lol, unless it's to upgrade to a newer version. 

So, what is the log in screen built into with this distro ?

---

### Post by wojox on 2011-03-14
> **FrankenCub said:**
> Ahh ok, I like Ubuntu 10.10 too much to change now lol, unless it's to upgrade to a newer version. 

So, what is the log in screen built into with this distro ?

[Plymouth]("http://www.freedesktop.org/wiki/Software/Plymouth")

---

### Post by Krytarik on 2011-03-14
> **wojox said:**
> The link is broke, but if you want to use those themes you have to use a distro that doesn't include Plymouth.
IMO this has nothing to do with Plymouth, but with the version of GDM. Remember, login screen. ;-)

---

### Post by wojox on 2011-03-14
> **Krytarik said:**
> IMO this has nothing to do with Plymouth, but with the version of GDM. Remember, login screen. ;-)

mmmmm, no it's Plymouth

> The first one, plymouthd, does all the heavy lifting. It logs the session and shows the splash screen. The second one, /bin/plymouth, is the control interface to plymouthd.

It supports things like plymouth show-splash, or plymouth ask-for-password, which trigger the associated action in plymouthd.

Plymouth supports various "splash" themes which are analogous to screensavers, but happen at boot time. There are several sample themes shipped with plymouth, but most distributions that use plymouth ship something customized for their distribution.

---

### Post by FrankenCub on 2011-03-14
Any ideas if the next upgrade version will allow these changes ?

---

### Post by false truths on 2011-03-14
You can modify the login screen themes for Ubuntu 10.10 by following the instructions in this post: [http://ubuntuforums.org/showthread.php?t=1602691](http://ubuntuforums.org/showthread.php?t=1602691)

Whenever you've selected your theme, change the icon set to LoginIcons so it won't break the login look.

If you want to modify the icon theme, use the LoginIcons theme as your template.

---

### Post by wojox on 2011-03-14
> **FrankenCub said:**
> Any ideas if the next upgrade version will allow these changes ?

No Plymouth is the future. Like false truths stated you can change the theme, wallpaper, and icons. 

And before you ask, no you can't uninstall Plymouth.

---

### Post by FrankenCub on 2011-03-15
Ok, looks like I'll learn to live with it. I don't log in with a password at the moment so was just hoping to make that my own too. I may as well at least make those changes when I start using a password so it at least stays with my general UFO/ET computer theme. Thanks guys, your all great ;-)

---

### Post by Krytarik on 2011-03-15
@wojox: Ok, it somehow bugs me that you keep stating that Plymouth manages the login screen, and I don't want to leave it that way:

[http://packages.ubuntu.com/maverick-updates/plymouth](http://packages.ubuntu.com/maverick-updates/plymouth)> **Package: plymouth (0.8.2-2ubuntu5.1)**
graphical boot animation and logger - main package

Plymouth is an application that runs very early in the boot process (even before the root filesystem is mounted!) that provides a graphical boot animation while the boot process happens in the background.
[http://packages.ubuntu.com/maverick/gdm](http://packages.ubuntu.com/maverick/gdm)
> **Package: gdm (2.30.5-0ubuntu4)**
GNOME Display Manager

 gdm provides the equivalent of a "login:" prompt for X displays- it pops up a login window and starts an X session. 
 It provides all the functionality of xdm, including XDMCP support for managing remote displays. 
 The greeting window is written using the GNOME libraries and hence looks like a GNOME application- even to the extent of supporting themes! By default, the greeter is run as an unprivileged user for security.
Sorry, but I gave you the chance to back down.

---

### Post by wojox on 2011-03-15
> **Krytarik said:**
> 
Sorry, but I gave you the chance to back down.

Fine. You explain to the OP how to install the GDM Themes he wants to install. 

I'll be the bigger man and bow out.

---

### Post by Krytarik on 2011-03-15
> **wojox said:**
> Fine. You explain to the OP how to install the GDM Themes he wants to install. 

See my very first post in this thread (post #2). ;)

---

### Post by FrankenCub on 2011-03-15
Who know, maybe the next upgrade will turn me on enough I won't want to mess with the log in screen :lolflag:
Now if I can hold out till whenever that may be :-\":popcorn:

---

### Post by wojox on 2011-03-15
> **Krytarik said:**
> See my very first post in this thread (post #2). ;)

Okay I read your post in the link and it did jog my memory that when Plymouth first came out people where mad and rolled back to the previous GDM. My apologies. :D

---

