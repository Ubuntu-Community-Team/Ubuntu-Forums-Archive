---
title: "Command Line Boot"
date: 2006-09-20
forum: Desktop Environments
---

### Post by 00coday on 2006-09-20
I need to accomplish two things:
1. boot Xubuntu into command line mode for login and then auto start the Xfce interface.
2. return the system to command line mode when a user logs out

For those of you that are asking why I would bother...  Our facility requires that a legal message be presented to a user before they login to the system.  I have found no way to do this via the gui login, but I can do this from the command line.

Any help would be appreciated

---

### Post by lagagnon on 2006-09-20
I'll bet there is a way to present a GUI boot message. Ubuntu uses GDM as its login manager. Why don't you put the message on your own login screen? Read this:
[http://hawknotes.blogspot.com/2006/07/something-other-than-brown.html](http://hawknotes.blogspot.com/2006/07/something-other-than-brown.html)

---

### Post by skymt on 2006-09-20
Write a shell script using zenity or xmessage (see the man pages) to present the message. Make it return 1 if the user rejects the agreement, 0 otherwise. Then put it in "/etc/gdm/PostLogin".

After GDM checks the username and password, it runs everything in /etc/gdm/PostLogin. If any of the scripts here return 1, GDM will refuse login. This is designed for exactly your situation.

For more information, see the [documentation](http://www.gnome.org/projects/gdm/docs/2.14/configuration.html).

---

### Post by 00coday on 2006-09-22
Thank!  The xmessage script worked.

Thanks again

---

