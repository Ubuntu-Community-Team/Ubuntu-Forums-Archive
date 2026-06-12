---
title: "Remote control Ubuntu Server"
date: 2009-03-11
forum: General Help
---

### Post by artheus on 2009-03-11
Hi!

I would like to know if there is any way of remotely controlling my Ubuntu (no GUI) server?
I am using it as a server, and don't have any monitor for it. So I'd really like to control it from my Desktop PC. Where I've got Windows installed.
If it's possible to control it with the command prompt in Windows that's be great!
I mean control it like logging in, and writing any Linux commands.

Like VNC, but without the GUI.

Cheers,
Artheus

---

### Post by Peter09 on 2009-03-11
Yes,
install openssh-server on your server and you will need a program such as putty on the windows machine. This will enable you to open a terminal on the remote 'server'.

---

### Post by hyper_ch on 2009-03-11
openssh-server + putty will enable what you want to do :)

alternatively you could install cygwin on the windows machine. That will give you a linux-like shell (also with rsync ;)

---

