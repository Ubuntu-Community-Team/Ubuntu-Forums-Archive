---
title: "GDM PostLogin script not working"
date: 2006-10-31
forum: Desktop Environments
---

### Post by vm76 on 2006-10-31
GDM PostLogin script is killing me:
(on edgy, updated)

I want to mount an administrative samba share just before the user starts his session (in order to generate a ~/.user_conf_file)

So.... /etc/gdm/PostLogin/Default
#!/bin/sh
mount -t smbfs //server/share /home/mountpoint -o ro,exec,username=myuser,password=mypass

But... it never works, and better, i can't login !!!
(i need to comment the lines to login)
If i execute this same script from a console, everythings works, the share is mounted and "myscript.sh" is executed.

I've modified the share to be "guest ok" (so without password) and tried to mount anonymous
-> same thing, PostLogin not working but console call does the job

WHYYYY ?????????? (yes i'm a bit nervous....)

---

### Post by andreyka on 2007-12-22
I have this problem with truecrypt mounting too ([http://ubuntuforums.org/showthread.php?p=3996809&posted=1#post3983143](http://ubuntuforums.org/showthread.php?p=3996809&posted=1#post3983143))
Ubuntu 7.10
please advice :)

---

