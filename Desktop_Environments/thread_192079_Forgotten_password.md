---
title: "Forgotten password"
date: 2006-06-08
forum: Desktop Environments
---

### Post by zeusdo on 2006-06-08
I'm a Windows person but I did install ubuntu on my machine a few months ago and I have seem to have forgotten my username and password to boot it up. Is there a way to reset it or retrieve it?

---

### Post by taurus on 2006-06-08
I assume you use GRUB to boot Ubuntu.  At the GRUB screen, choose the recovery mode (or single user mode) and boot from it.  It will drop you into a shell as root so you can look at /etc/passwd to see exactly what is the username (probably somewhere at the bottom of that file).  Then, assign it a new password as
```

passwd john
(assuming that john is the username login name...)

```

p.s.  You can view the content of /etc/passwd with
```

more /etc/passwd
(then hit the space bar for the next 24 lines...)

```

---

### Post by persistent_phenomenon on 2006-06-14
OK, as embassed as I am to admit it I've done something so stupid that even the above post doesn't help me. As this is a learning thing for me I'm quite prepared to re-install and I probably deserve to but I thought I would ask here first.

I installed dapper drake a few days ago, it was late and so as soon as the actual install finished I went to bed.  I booted up tonight and can't remember username or password.  The thing is I don't remember creating an account as part of the install at all.

I've logged in in recovery mode and checked etc/passwd and I can't see any account listed.  So I tried creating one using useradd, setting the password and then trying to login to the GUI but it told me that I didn't have a home directory, it let me login using the root directory but then I reached a blank desktop and my session timed out after 10 seconds (or something similar) 

Any suggestions would be greatly appreciated! 

:?:

---

### Post by lamego on 2006-06-14
Delete the user and create it again, but now use the useradd -m option to create the home directory.
Loging with the root directoy will not work because gnome will need to write some files on your home dir and it has no permissions to do it on / .

---

### Post by zeusdo on 2006-06-15
Thanks, I'll give it a try.

---

### Post by persistent_phenomenon on 2006-06-24
lamego, taurus, Thanks a lot for your help.

---

