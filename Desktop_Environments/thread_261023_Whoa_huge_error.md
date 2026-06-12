---
title: "Whoa huge error:"
date: 2006-09-19
forum: Desktop Environments
---

### Post by Poeffie on 2006-09-19
I'm working with Ubuntu 6.06 and I seem to have messed up something:

This error only shows with gnome2 applications (I think), everywhere at startup, I'm not able to use any gnome panel, application launcher etc.. (I've made an application on the desktop to start firefox now)
Firefox works normally

Adding client to server's list failed, CORBA error:
An error occurred while loading or saving configuration information for gnome-desktop-item-edit. Some of your configuration settings may not work properly.
Details:
IDL:omg.org/CORBA/COMM_FAILURE:1.0
Adding client to server's list failed, CORBA error: IDL:omg.org/CORBA/COMM_FAILURE:1.0
[repeated...]

This error doesnt show on my other account, everything there is 100% normal.
Also all non-gnome programs (gdesklets, Gaim, Firefox,..) are able to work normally

I've lost my theme, background,.. but I still see desktop icons

First time I've seen this is in my last session, then it started. Suddenly I started nautilus with a very simple view whenever I wanted to look at my files and it showed these errors.
I tried to fix it by logging out and logging back in, but then my gnome was completely gone.

Does anybody know a fix for this?? Please ASAP becouse I only have 14 hours and I'm moving this pc to another location.

---

### Post by Poeffie on 2006-09-19
Ok, I seem to have solved it by removing /tmp/orbit-$USER and rebooting

Now I dont get what this had to do with my gnome-enviroment

---

