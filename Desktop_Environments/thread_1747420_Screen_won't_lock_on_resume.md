---
title: "Screen won't lock on resume"
date: 2011-05-02
forum: Desktop Environments
---

### Post by x-shaney-x on 2011-05-02
Installed KDE/Kubuntu Natty today and I have noticed the screen will not lock when resuming from suspend.

The option to lock the screen IS checked in power management settings and when it does resume, there is a notification that says it is locking the screen (but doesn't).

Also, clicking the button on the lock/logout applet doesn't lock the screen either.]
Surely this is a fairly serious security issue?

Kubuntu Natty 64-bit.
I should point out this is working normally on a fully up-to-date 32-bit beta 2 install.

---

### Post by x-shaney-x on 2011-05-03
Just to add, I tried it on a secondary user account and the screen DID lock on resume and the lock button DOES work in the other account.

I have removed ~/.kde and anything in my home folder related to power management but it still won't work on my main account.

---

### Post by aleko74 on 2011-05-13
Any luck with this? I'm having the same problem on Kubuntu Lucid.

---

### Post by x-shaney-x on 2011-05-13
I removed everything in my ~/home directory and copied essentials over and the problem went away.
A few hours later the problem came back again for no apparent reason.

So I did the same again and it has been ok since.

Cannot find any cause but it's behaving now so I'm happy enough.

---

### Post by ario on 2011-08-08
Yeah! I will tell you what happens in new Kubuntu!
I guess some necessary application to lock screen is not working on Kubuntu by default, so that locking the screen won't work. I'm telling you this, becuase whenever I run switch user, it takes some time, and my HDD LED blinks for a while just like loading some application. After that the transparent switch user dialog comes up and although I will close it, I will be able to lock my screen after that!
I wish I knew what is the path of that magic application which runs by switch user command, but till then, **the only work around is to first run switch user from somewhere, and then you will be able to lock your screen!** Pretty patatic! :(

---

