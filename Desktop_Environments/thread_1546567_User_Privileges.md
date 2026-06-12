---
title: "User Privileges"
date: 2010-08-05
forum: Desktop Environments
---

### Post by magus841 on 2010-08-05
Hello! 

I've been using Ubuntu for a couple months now and I just got a an old computer from work that I'd like to put Ubuntu on for my mother. I'm afraid she'll do something silly and brick the system. So I want to make an account for her to use that has basic desktop user privileges. But I still want her to be able to update the system with the Update Manager and from what I can tell, you need to have admin privileges to use it with sudo. I'm going to be away and can't do it for her. Is this possible? If so, how? I just want to keep it as easy as possible for her. I appreciate any help with this. Thank you.

---

### Post by sydbat on 2010-08-05
> **magus841 said:**
> Hello! 

I've been using Ubuntu for a couple months now and I just got a an old computer from work that I'd like to put Ubuntu on for my mother. I'm afraid she'll do something silly and brick the system. So I want to make an account for her to use that has basic desktop user privileges. But I still want her to be able to update the system with the Update Manager and from what I can tell, you need to have admin privileges to use it with sudo. I'm going to be away and can't do it for her. Is this possible? If so, how? I just want to keep it as easy as possible for her. I appreciate any help with this. Thank you.I doubt she'll bork the system. I have set up many-a-buntu box with the default user. Because you HAVE to input your password each time you install something, chances are really slim she would 'click' on the wrong thing and brick it.

Just talk with her about what she is able to do, and what not to do, in as non-a-technical way as possible. Also, tell her that if she is not sure about what to do, to leave it until you get back.

Easy Peasy!

---

### Post by magus841 on 2010-08-05
That's good and fine. I can talk to her, which I would have done anyway :P

But just so I know for personal knowledge, is there a way to give users without root privileges access to specific programs?

---

### Post by sisco311 on 2010-08-05
> **magus841 said:**
> That's good and fine. I can talk to her, which I would have done anyway :P

But just so I know for personal knowledge, is there a way to give users without root privileges access to specific programs?


sudo, by default, is configured to allow users from the admin group to run any commands as any other user, but you can configure it to allow specific users to run specific commands as root or another user:

[uhelp]community/Sudoers[/uhelp]
[thread=1321821]HowTO: Sudoers Configuration[/thread]

Most modern GUI applications (Software Center, Users and Groups, Network Manager...) use policykit instead of sudo.

Check out:
[http://hal.freedesktop.org/docs/polkit/pklocalauthority.8.html](http://hal.freedesktop.org/docs/polkit/pklocalauthority.8.html)

i.e. to allow a user to install software via Ubuntu Software Center you could create a .pkla file in /var/lib/polkit-1/localauthority/50-local.d/ withe the following content:
```
[Installing software]
Identity=unix-user:**username**
Action=org.debian.apt.install-packages;org.debian.apt.update-cache
ResultActive=auth_self_keep

```

For a list of actions and their descriptions, run:
```
pkaction --verbose
```

---

