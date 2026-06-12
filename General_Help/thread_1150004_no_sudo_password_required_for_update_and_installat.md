---
title: "no sudo password required for update and installation (jaunty)"
date: 2009-05-05
forum: General Help
---

### Post by pigbird on 2009-05-05
I just installed jaunty on my laptop today, it works quite well so far, just have a question. Now if i install something or update with update manager, it does automatically without asking my sudo password. It wasn't like that after installation of jaunty. Can anybody explain why and help me to make it like back to "normal". I just find it not so secured this way, not being asked sudo password.

---

### Post by Brandon Williams on 2009-05-05
The system will not ask you for your password every time you run sudo. It asks once, and then will just run sudo commands without it for 15 minutes before asking for the password again.

You can change the length of time by setting the timestamp_timeout in sudoers. See 'man sudoers' for more details about how to adjust the config.

---

### Post by hg21 on 2009-05-07
I am finding the same thing with updates.

It does not ask for a password even when I haven't done a 'sudo' for ages. The default for /etc/sudoers is said to be 15mins and there is nothing in my /etc/sudoers to change this.

I use kubuntu

---

### Post by xouns on 2009-05-08
With Ibex and Hardy, when I closed the Update-window and reopened it, it asked me again for my password, somehow Jaunty doesn't. Could someone please explain why? And how can I change it back to the old way (I like to enter my password, it gives me a slight feeling of control).

---

