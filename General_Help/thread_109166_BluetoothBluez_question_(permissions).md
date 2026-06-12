---
title: "Bluetooth/Bluez question (permissions)"
date: 2005-12-28
forum: General Help
---

### Post by Nate53085 on 2005-12-28
I was able to get my bluetooth mouse to pair beatifully using this guide:

[http://ubuntuforums.org/showthread.php?t=87919](http://ubuntuforums.org/showthread.php?t=87919)

But hidd requires sudo.  I don't use my mouse all that often (only when my laptop is at my desk) and often times I leave it alone for longer then the sleep time of my mouse.  I have a button in my taskbar that pairs the devise when clicked, but I have to type my password in each time.

What I would like to accomplish is to not have to sudo in order to pair the device.  Right now I have: 

sudo hidd --connect 00:0A:3A:06:59:73; exit

How can I go about removing the sudo?  A simple chmod 777 (its 755 default) did not do anything.  I get a permission denied.  Thanx in advance.

---

### Post by Nate53085 on 2005-12-28
I tried adding:

user ALL= NOPASSWD: /usr/bin/hidd

to /etc/sudoers and had no luck

EDIT

adding: username ALL=(root) /etc/bin/hidd
stops the need from entering a password when executing hidd from username

---

### Post by Nate53085 on 2005-12-28
Nope, I lied it didn't work.  Apparently sudo hadn't timed out yet when I tested it.  Any ideas?

---

