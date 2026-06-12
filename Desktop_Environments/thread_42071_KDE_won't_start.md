---
title: "KDE won't start"
date: 2005-06-15
forum: Desktop Environments
---

### Post by vtechstu on 2005-06-15
I can't get kubuntu to load because it says something about the partition not being writeable.  And this locale this is also new.

Creating intial device nodes....  [  OK  ]
locale: cannot set LC_CT'/
locale: cannot set LC_Messages
locale: cannot set LC_All
to default.

And this is what i got once everything loaded and i tried to log in.

The following installation problem was defected while trying to start KDE:

      No write acces to $Home directory(/Home/Chase)

KDE is unable to start.

What does this mean?  This is making me irritated, i thought linux was suppose to be pretty stable compared to windows... i'm havings lots of issues :(.  HELP please.!

Thanks

---

### Post by Xian on 2005-06-15
Appears that somehow the file permissions on your /home directory got shuffled.
Boot into Ubuntu with the Recovery Mode option in Grub.

Then you'll need to input the command below when you get dropped to a command prompt. You should be in an admin environment at this time, but if for some reason you get access errors just run the same command with the sudo prefix.

This is assuming your user name is as written.
Be sure to check the syntax as it is important.

```
$ chown -R Chase:Chase /home/Chase/
```

---

### Post by diebels on 2005-06-15
Could be file corruption. Try running a fsck.
**sudo shutdown -F now**
[CTRL]+[ALT]+F1 and log in to a terminal first

---

### Post by vtechstu on 2005-06-16
What Xian said helped.  Thanks!

---

