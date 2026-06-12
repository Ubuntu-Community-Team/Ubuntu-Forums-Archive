---
title: "How to prevent users to change desktop, gnome-panel and others variables"
date: 2010-06-15
forum: Desktop Environments
---

### Post by *Igor* on 2010-06-15
Hi all,

this is my first thread, sorry for my english: i'm italian and i know it's not so good...

I'm looking for a manner to prevent users from changing the desktop background/wallpaper and _all other gnome configuration_ with booth Ubuntu and Kubuntu,

First of all, naturallly, i use search, but i don't find any good solution for this issue.

This too (Abraxis, some years ago, have same my problem) 
[http://ubuntuforums.org/showthread.php?t=437578&highlight=prevent+users+changing+desktop](http://ubuntuforums.org/showthread.php?t=437578&highlight=prevent+users+changing+desktop)
do not solve the problem, for example if i change whit chown(*) own and group of this file to root  /.gconf/desktop/gnome/background/%gconf.xml, at the next reboot file return in the previous state.
(I don't like Pessulus)

Thanks and all the best

Igor


(*)
chown root:root %gconf.xml
chmod 644 %gconf.xml

at the reboot file change automatically owner to "student", i don't know why :S

---

### Post by nerdzero on 2010-06-15
Igor,

This is quite a hack but you can try editing the /etc/rc.local script to run your ownership commands.  This way, your command will get executed on every reboot.  There are probably better ways to do this but this is the easiest way off the top of my head.

---

