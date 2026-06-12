---
title: "Can't login anymore - kdsetkeycode: no such device"
date: 2008-02-05
forum: Dell  Ubuntu Support
---

### Post by mpospisil on 2008-02-05
After I did a restart of my system I can't log into Ubuntu.  It brings me to the log in screen where I can enter my user name and password.  

Then an Nvidia splash screen comes up and the Nautilus screen appears, but after that the screen briefly flashes this error: kdsetkeycode: no such device xx and xx, where xx are some numbers.  

After this it takes me back to the login screen and it just repeats the loop.  Can someone please help me fix this problem? 

 I'll probably have to reconfigure xorg or something like that so if someone can tell me how to do that I would greatly appreciate it.  Thanks!

---

### Post by ashokpappu on 2008-02-08
looks like u'r x server is a toast check id you have any files  in /etc/X11/xorg.conf, xorg.conf.bak1 or any other files like this.  if there are there all u need to do is rename the current file to xorg.conf to some thing like xorg.conf.notworking . then copy an older version of xorg.conf.bak to xorg.conf.  reboot and it should work( should work without reboot but just to make sure)

---

