---
title: "Splash screen"
date: 2010-07-15
forum: Desktop Environments
---

### Post by rdnrvn on 2010-07-15
Hi,

I want to set a different splash screen instead of the one that shows up just before and just after I log in (Ubuntu and the loading bar)

I installed gnome-splashschreen-manager and through that I set the splash screen to another jpg image but this doesnt seem to work. I dint see any difference after rebooting.
Am I doing something wrong in GNOME Splash Screen Preferences? This method seemed really straight forward.

If there is another way to go about it, would love to hear. I hope I can sort this out soon.

Thanks!

---

### Post by ajgreeny on 2010-07-15
Which ubuntu version are you running?  Must be 9.04 or earlier to have the loading bar showing.

---

### Post by blesbok on 2010-07-15
The following is based on LinuxMint and what you have may differ.

What you do is to change the default background as root.  Open a terminal.  Give the terminal this code:

```
gksudo -u gdm dbus-launch gnome-appearance-properties

```

Your password will be requested and the Appearance Preferences dialog will appear. Click on Background. The contents of /usr/share/backgrounds will appear. Edit (or substitute) /usr/share/background/Fresh.jpg with Gimp and save it under the same name. If you mess up Fresh.jpg, you can copy it again from under /usr/share/images/xsplash. A Matthew 23:23 version of Mint’s Fresh.jpg can be viewed [here]("http://glebeconnection.files.wordpress.com/2010/06/Fresh.jpg")

---

### Post by blesbok on 2010-07-16
Note, doing the above will also change your wallpaper.  Be prepared to change it back again :D

Did this help you?  If so, please mark the thread SOLVED.

---

### Post by rdnrvn on 2010-07-22
I found this thread which was pretty much what I needed:
[http://ubuntuforums.org/showthread.php?t=1337381](http://ubuntuforums.org/showthread.php?t=1337381)

I'm marking this as solved. Thanks. :)

---

