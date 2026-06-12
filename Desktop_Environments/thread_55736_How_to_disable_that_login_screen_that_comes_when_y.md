---
title: "How to disable that login screen that comes when you start computer"
date: 2005-08-10
forum: Desktop Environments
---

### Post by kzu on 2005-08-10
I had Red Hat linux in 2000, then I removed it and now installed ubuntu two days ago after 5 year break from linux. And i'm liking it, but! In RH when you started the computer, it didn't start that login screen thing, only the basic console where you could login with the user you want, and then you had to start X manually, how can I set ubuntu to work like that?

---

### Post by lol on 2005-08-10
update-rc.d -f gdm remove

This is going to remove the link to gdm from all /etc/rcX.d folder. Obviously, if you are using kdm, just replace gdm with kdm...

---

### Post by Capilano on 2005-08-12
[QUOTE=lol]update-rc.d -f gdm remove

This is going to remove the link to gdm from all /etc/rcX.d folder. Obviously, if you are using kdm, just replace gdm with kdm...[/QUOTE]
 How can this be reverse ? newbie here

---

### Post by Capilano on 2005-08-13
[QUOTE=Capilano]How can this be reverse ? newbie here[/QUOTE]
I found out BUM; just reactivate GDM

---

