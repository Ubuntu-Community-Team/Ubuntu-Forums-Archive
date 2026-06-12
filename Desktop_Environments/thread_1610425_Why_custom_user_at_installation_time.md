---
title: "Why custom user at installation time?"
date: 2010-10-31
forum: Desktop Environments
---

### Post by acag on 2010-10-31
I am a newbie who has just installed Ubuntu 10.4 LTS yesterday. I am sure the answer is probably a simple one, but I don't understand why the user created at installation time is a Custom User instead of an Administrator. Please explain.

Regards,
acag

---

### Post by Dave_L on 2010-10-31
There's an explanation here:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

For additional info:
[http://ubuntuforums.org/showthread.php?t=1486138](http://ubuntuforums.org/showthread.php?t=1486138)

---

### Post by acag on 2010-10-31
Thanks for the response!!! Hmmmm, a little deep for me but I think I get the gist of it. So is the best practice to create a desktop user (for everyday use) and an Administrator user (for installs, upgrades, etc.). If so, then what becomes of the custom user ID I created at installation? Is it no linger needed, if so, can it be deleted?

Rgds,
acag

---

### Post by 3Miro on 2010-10-31
There are two ways to do things properly. One way is to create an administrator user and a regular user. Administrators installs programs and messes with global system settings, while the regular user does everything else on the system (browse internet, watch videos and so on). This what is recommended on windows and this is what most of the other Linux distributions do.

The second way, which is what Ubuntu does, is to create a custom users that is in a way both an administrator and a regular user. When you are logged in as your regular user, you can do all administrative tasks, but every time you do something like that, you are explicitly asked for your password. In that way, you still cannot accidentally mess up your system (it is very hard to accidentally type in your password) and you don't have to remember two separate passwords and two separate users.

---

### Post by acag on 2010-11-01
Ahhh! What a great idea. Thanks so much for the explanation, 3Miro. It makes sense to me!

---

