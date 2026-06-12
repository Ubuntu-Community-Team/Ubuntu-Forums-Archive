---
title: "Weird kedit message"
date: 2006-02-23
forum: Desktop Environments
---

### Post by Connollyir on 2006-02-23
Whenever I start kedit I get this message: 

e@Persepolis:~$ sudo kedit .bashrc
Error: "/tmp/kde-e" is owned by uid 1000 instead of uid 0.
Link points to "/tmp/kde-root"
e@Persepolis:~$

How do I fix this? Its a completely new installation and I haven't had this problem with previous installs.

-Ian

---

### Post by Jucato on 2006-02-23
do you have kedit installed? how about trying to use kate?
btw, the .bashrc that you are trying to open is in your /home directory and is owned by you, so no need for sudo.

---

### Post by lowey23 on 2006-02-23
You may have to use kdesu instead of sudo. Had the same thing and it worked for me.
Cheers
Lowey

---

