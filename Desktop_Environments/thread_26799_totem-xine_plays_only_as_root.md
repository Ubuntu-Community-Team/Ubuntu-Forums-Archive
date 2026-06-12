---
title: "totem-xine plays only as root"
date: 2005-04-13
forum: Desktop Environments
---

### Post by vegetto on 2005-04-13
I have this stupid problem, totem-xine plays media files only as root. as a normal user it gives "there is no plugin to handle this movie". but as root everything works fine. the w32codecs are present as symlinks in .gnome2/totem-addons, but there is a lock icon on them, so i deleted all of them and copied all of them from /usr/lib/win32 and the lock icon is gone. still no joy!

---

### Post by wondering_jew on 2005-04-14
Hmmm I have 2 suggestions either of which might fix this problem.
1) Make sure that you and not root owns the codecs individually (if not use "chown (user name) (name or path of file)"
or
2) change the permisions of the codecs so that anybody can use them

Im not confident enough in my own command of the command line to give you exact steps but i do know that you can just type "sudo nautilus" from a terminal and then right click on the files and change the permissions in properties without bothering with chmod or whatever.  Hope something that I said was somewhat usefull ;)

---

### Post by vegetto on 2005-04-14
> 1) Make sure that you and not root owns the codecs individually (if not use "chown (user name) (name or path of file)"
or
2) change the permisions of the codecs so that anybody can use them
Already done that. i also noticed that everything works fine with xine-ui only totem has problems.

---

