---
title: "path changes to /etc/profile are ignored"
date: 2006-04-02
forum: Desktop Environments
---

### Post by GATTACA on 2006-04-02
Hello.

I'm not exactly a linux newbie but I'm a ubuntu newbie so bare with me if this is a dumb question.

I've done a fresh install of Ubuntu 5.10 and now I want to modify the system path.
Normally under Slackware I would just add a line to /etc/profile. However for some reason when I do this in Ubuntu it doesn't have any effect.

I've read through the other postings and tried placing the path change in /etc/environment but to no avail.

Any ideas what is going on?

](*,)

---

### Post by vruum on 2006-04-03
Maybe take a look at ~/.bashrc, see if anything is setting the path from there? or try setting it from there yourself

---

### Post by GATTACA on 2006-04-03
[QUOTE=vruum]Maybe take a look at ~/.bashrc, see if anything is setting the path from there? or try setting it from there yourself[/QUOTE]

Thanks for the quick reply.

Unfortunately this won't work. I can get it to work by setting the path in ~/.bashrc but I want the change to be _global_, for all users on the system. 

This is why I initially set it in /etc/profile.

---

### Post by jrib on 2006-04-03
PATH when you login to gnome gets set in /etc/login.defs .  /etc/profile gets sourced only for login shells.  The easiest way to modify your PATH is to use ~/.gnomerc (create it if it doesn't exist).  ~/.gnomerc will get sourced every time you log into gnome as well.  Hope that helps

---

### Post by GATTACA on 2006-04-03
[QUOTE=_jason]PATH when you login to gnome gets set in /etc/login.defs .  /etc/profile gets sourced only for login shells.  The easiest way to modify your PATH is to use ~/.gnomerc (create it if it doesn't exist).  ~/.gnomerc will get sourced every time you log into gnome as well.  Hope that helps[/QUOTE]

I'll give that a try thanks. I did set the gnome terminal to be a login shell but this made no difference, /etc/profile was still not sourced.

I take it editing /etc/login.defs acts system wide right?

Thanks

---

### Post by jrib on 2006-04-03
/etc/login.defs is system-wide

If you just need to change your PATH in your gnome-terminal, you can just use ~/.bashrc or whatever the corresponding system-wide bashrc is in /etc (check man bash).  Doing this is the easiest way, but I think the cleanest is using ~/.gnomerc

---

