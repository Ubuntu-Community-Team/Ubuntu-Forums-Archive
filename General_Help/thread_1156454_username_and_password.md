---
title: "username and password"
date: 2009-05-11
forum: General Help
---

### Post by drynear on 2009-05-11
I installed Ubuntu 8.10 and had all kinds of trouble but it finally installed completely.
Now it tells me I am trying to log in with an incorrect username or password.
I am positive I am using the username and password I had entered at installation but of course I could have made an error.
I hate to have a username and password on my personal home computer but found no way to install without them.
Any way I can now do a workaround or am I destined to uninstall and reinstall?

---

### Post by SuperSonic4 on 2009-05-11
You can drop to the root shell via the recovery mode (press esc during grub to access it)

Once there pick the root shell and type ```
passwd <user>
``` where <user> is your user.

You may also manage to do the above command as user via a terminal

---

### Post by hobo14 on 2009-05-11
And once you're in, go to System > Administration > LoginWindow, and set automatic login in the security tab, so you don't have to login again.

---

### Post by drynear on 2009-05-11
Thanks for the fast reply.
It looks like it is the username which is incorrect.
I followed the instructions with no problem and it finds no user by that name.

---

### Post by hansdown on 2009-05-11
Hi drynear.

This tutorial should help you straighten things.

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by drynear on 2009-05-11
Thanks loads for all the fast responses and help.
I'm all set. So far I am impressed.
Thanks again.

---

