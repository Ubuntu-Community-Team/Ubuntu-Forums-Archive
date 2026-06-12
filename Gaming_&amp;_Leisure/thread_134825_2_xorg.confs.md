---
title: "2 xorg.confs"
date: 2006-02-22
forum: Gaming &amp; Leisure
---

### Post by Haegin on 2006-02-22
Hi, is it possible to have two seperate xorg.confs and specify which to load when you turn the pc on? I want to have one with the nv driver which works fine and the other with the nvidia driver which is needed for games but my gfx card is a bit duff so it wont let me shutdown, logout, restart x or change to a terminal (ctrl alt f1 etc) so I am planning to use the nv driver except when I need games. Is this possible?

Thanks in advance

---

### Post by bernardfrancois on 2006-02-22
I don't think that's possible, unless you install X two times. If you do that you can switch (for example if you let the first X start on one teriminal, the other X on another terminal).

If you want to know more about the xorg.conf file, try **man 5 xorg.conf**.

---

### Post by Harleen on 2006-02-22
You can write a script, that switches the configuration files on boot before starting X. But I'm not quite sure yet how to tell that script, which configuration to take.
A dialog would be too annoying. I'd try to make a new Grub entry, but I don't know how you could possibly pass some arguments from grub to the Linux system...

---

### Post by bernardfrancois on 2006-02-23
Or - easier to do - you could write a script that switches those scripts, shuts down and restarts x.

Let's say your two xorg.conf files are /etc/xorg1.conf and /etc/xorg2.conf, then you can execute the following script to switch (run it as root):

```

#!/bin/sh
if [ $(md5sum /etc/X11/xorg.conf | cut -d ' ' -f 1) = $(md5sum /etc/X11/xorg1.conf | cut -d ' ' -f 1) ] ; then
  cp /etc/X11/xorg2.conf /etc/X11/xorg.conf
else
  cp /etc/X11/xorg1.conf /etc/X11/xorg.conf
fi

```

Checking the md5sum is not the fastest way to see if files are the same, probably you can use another method. But since it's not executed periodically and at a high frequency, this si not a problem.

---

### Post by Harleen on 2006-02-23
Instead of using md5sum you could use diff. If diff returns 0, both files are the same.

But I just realised a much simpler solution. Make two configuration files and two shortcuts on your desktop, that copy them over the /etc/X11/xorg.conf.

You can than switch the configuration by klicking on the shortcut so set the correct xorg.conf and then restart X by pressing <CTRL>+<ALT>+<BACKSPACE>.
That's probably not the nicest solution, but an easy and working one.

---

### Post by bernardfrancois on 2006-02-23
Or the script mentioned above could be placed on the desktop... Then there's only one icon to click on on the desktop (or in the gnome menus, which would be nicer I guess).

---

### Post by Haegin on 2006-02-23
schweet - then i guess I can just tell the script to stop gdm at the beginning and start it again at the end. Thanks :D

---

### Post by bernardfrancois on 2006-02-23
Yep. with **/etc/init.d/gdm start** or **stop** (or **kdm** if you're using kde). Don't forget that this will end all programs you are running under X. Maybe you could add a dialog box that asks confirmation and warns about that (using **zenity**, which you can install using synaptic, if it isn't already installed).

---

### Post by Haegin on 2006-02-23
Well because of my cheapskate gfx card the pc will crash if I am using the official drivers (hence why I want to use nv when possible) so that will need a full restart (and I have a warning box telling you it will crash) but a confirmation box for the close all programs would be good...

Thanks for all the help

---

### Post by Harleen on 2006-02-23
Restarting X should be enough. No need to restart the whole computer.
But you shouldn't call "gdm stop" and than "gdm start" from your script, because when you close gdm it will kill X before "gdm start" gets executed leaving you on a text console. The command "gdm restart" should do the trick.

You can get a confirmation for free using the gksudo arguments. Instead of calling "gksudo <script>" you can use
```
gksudo --message "<b>Attention:</b> This is going to restart your X-Server. <script>"
```

---

### Post by bernardfrancois on 2006-02-23
Oh, nice. I didn't know that was possible. Note that the name of the script should be outside the quotes (as a 3rd parameter to gksudo).

---

