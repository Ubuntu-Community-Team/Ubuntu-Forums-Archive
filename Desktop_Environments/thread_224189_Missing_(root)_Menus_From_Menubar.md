---
title: "Missing (root?) Menus From Menubar"
date: 2006-07-27
forum: Desktop Environments
---

### Post by aur0ra on 2006-07-27
I've been working with Ubuntu for the past few days, during which I've updated a number of packages (but not the kernel). I'm a Fedora/RHEL user and have decided to try Ubuntu, so I'm definitely not a Linux n00b.

For some reason I lost some of my menus in Applications & System->Administration. It is almost as if I lost all of the "root" menus that are given to appropriate users. For example, I no longer have the Add/Remove Packages and I no longer have System->Administration->Users and Groups.

I checked the aliases file and it looks correct:
root: myuser

Anyone have any idea why I lost these items? 

Just to add to the information... At the same time this happened I also lost access to the sound card (which I fixed by adding my username in /etc/groups audio section) and my sudo priv got hosed too (which I fixed by doing visudo as root).

Any thoughts and/or pointers would be much appreciated.

---

### Post by aur0ra on 2006-07-27
Ok, I just found this thread:
[http://www.ubuntuforums.org/showthread.php?t=159475](http://www.ubuntuforums.org/showthread.php?t=159475)

But what the heck is user-admin? I've never heard of that? I'm certain this will answer my problem as well.

Thanks.

---

### Post by aur0ra on 2006-07-27
Ok, so the command is 'users-admin' that's what the problem was. 

I simply added root and my username to the admin group and now everything is good to go. Hopefully this tread will help someone else in the future.

---

### Post by Sonicgoo on 2007-06-24
That was helpful, thanks

---

