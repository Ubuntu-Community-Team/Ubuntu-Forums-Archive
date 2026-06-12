---
title: "notify-send with notify-osd"
date: 2009-11-01
forum: Desktop Environments
---

### Post by arizonagroovejet on 2009-11-01
I've decided to check out Ubuntu after using openSUSE for a while and I can't work out how to interact with this notify-osd thing from a shell script. When notification-daemon is being used one can use notify-send, but notify-send doesn't do anything when notify-osd is running. Is there an equivalent of notify-send that works with notify-osd?

I'm really failing to see how notify-osd is in anyway an improvement over notification-daemon. I'd dump notify-osd and replace it with notification-daemon, except notification-daemon's notifications overlap the panel and their appearance doesn't fit with the theme.

---

### Post by wrightjmf on 2009-11-10
Have a look at the following link.

[http://ubuntuforums.org/showthread.php?t=1251706](http://ubuntuforums.org/showthread.php?t=1251706)

That worked for me, and I didn't have to export the environment variable. It was already taken care of. I did use the command form... 

sudo -E -u target-user <msg_command>

...so I ended up typing

sudo -E -u my-user-name notify-send "Hello World"

I hope that helps.

---

