---
title: "How to set up different gdm session for each user"
date: 2009-08-14
forum: Desktop Environments
---

### Post by victor.cighir on 2009-08-14
Hello Ubuntu Forum users and gurus!

[INDENT]I have the following problem: on an Ubuntu 9.04 installation I have installed the following desktop environments and managers : Gnome, KDE , XFCE and Fluxbox.[/INDENT]

Also, I use gdm as my session manager.

[INDENT]*My question is , how can I configure gdm to use different desktop environments for each of my users ?* [/INDENT]

For example ,
[INDENT]USER 1     uses     gnome
USER 2      ->      Fluxbox
USER 3      ->      KDE[/INDENT]

Each time USER1 logs in, gnome should load  without him having to explicitly select Gnome from the sessions menu. The same for the other users.


Thanks,
Victor

---

### Post by Brandon Williams on 2009-08-15
That should happen automatically. For each user, there is a file called ~/.dmrc that stores the name of the session that the user most recently logged in with. Each of your users should have different content in their own ~/.dmrc file.

---

### Post by victor.cighir on 2009-08-15
> **Brandon Williams said:**
> That should happen automatically. For each user, there is a file called ~/.dmrc that stores the name of the session that the user most recently logged in with. Each of your users should have different content in their own ~/.dmrc file.

Thank you Brandon. I now realize how obvious it was... Sorry for posting this silly question. 

My hope is that this post will be cached in google and somebody will find it useful in the future. I searched google and the Ubuntu forums and nothing popped out.

Thank you again!

---

### Post by stimpyaw on 2010-08-07
I'm having a similar issue, I'm using Ubuntu 10.04 and would like to set one of the users of a laptop to login using "netbook-launcher-efl" that is part of the 10.04 package. I haven't found a way to set a user to "netbook-launcher-efl" when the click on there name when login into the laptop.

Any help on this would be great.

UPDATE: figured it out, found the user folders with the '.drmc' file under '/var/cache/gdm/[user short name]'.

---

