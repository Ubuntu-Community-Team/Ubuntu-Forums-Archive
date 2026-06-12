---
title: "Can not add neww users, guest session not working."
date: 2011-03-19
forum: Desktop Environments
---

### Post by luciferactual on 2011-03-19
Ubuntu 10.10 x64

It's been a little over a week since I *rebuilt my system after a gdm or gnome issue and now I'm having an issue with the guest session not working and I'm unable to add a new user. It says "incorrect data" or something like that. This is more than annoying. Why is my system decaying so rapidly? I'm not adding anything to the system that isn't approved by Ubuntu. it's virtually a stock build, minus some changes to the look and feel category. Is this possibly a security issue? My routers up and running and I turned on UFW.

.1) Can't add new users
.2) Guest session will not start.
.3) Should I be concerned about my security? 

Thanks in advance, sorry for the rant.



**Slicked it and reinstalled it.

---

### Post by Thund3rstruck on 2011-03-19
I just ran into a similar problem adding new users using the users-admin tool. 

What happens when you run:
```

sudo useradd -m -s /bin/bash newUserName
sudo passwd newUserName

```

That should create a new user successfully. As for the other stuff; I migrated to Linux Mint (which is a more stable version of Ubuntu) that doesn't break stuff on every software update. You might want to give it a try (I personally got tired of re-installing VMWare and wireless drivers every week --when a new kernel version is released).

---

### Post by luciferactual on 2011-03-20
Thanks Thun3rstruck.

I'll give it a go and see what happens, but Ideally I would like to find out why this happened and how to prevent it from happening again.  -Cheers

---

