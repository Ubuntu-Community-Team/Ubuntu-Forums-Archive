---
title: "Adding item in menu"
date: 2009-09-10
forum: Desktop Environments
---

### Post by BramWillemsen on 2009-09-10
Hello,

I am trying to add skype in the Applications menu. For webcam support i need to use the following command: "LD_PRELOAD=/usr/lib32/libv4l/v4l2convert.so skype" (without quotation marks) . When i use this command for a menu item it does not work, it only gets the first part, "LD_PRELOAD=/usr/lib32/libv4l/v4l2convert.so". 

It returns the following error because it only picks up the first part:

Could not launch 'Skype'

Failed to execure child process "LD_PRELOAD=/usr/lib32/libv4l/v4l2convert.so" (No such file or directory). The error message shows it does not get the full command. 

When i type "LD_PRELOAD=/usr/lib32/libv4l/v4l2convert.so skype" in the terminal, it does work.

Does anyone know the right way of adding this to a menu item? kind regards, Bram

---

### Post by BramWillemsen on 2009-09-10
okay i figured it out:

put env before the command ->

env LD_PRELOAD=/usr/lib32/libv4l/v4l2convert.so skype

Then the shortcut will work. Hope this will help someone else too.

---

### Post by piotrek75 on 2011-06-22
Thqnks for your tip.
This doesn't worked for me.
The solution for me was to create a script which I launch from my shortcut:
```
#! /bin/sh
export LD_PRELOAD=/usr/lib32/libv4l/v4l2convert.so
skype
```

---

