---
title: "gksudo not working"
date: 2006-02-08
forum: Desktop Environments
---

### Post by ashrack on 2006-02-08
This is my problem in an example:
```
$ gksudo nautilus

(nautilus:13530): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

```

```
gksudo gedit

(gedit:13574): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

```

And then I have to wait for about 2minutes for those 2 application to start.

---

### Post by CompShrink on 2006-02-08
I get the same error message, but it doesn't delay the program execution.

Try using plain sudo. It is warned not to use sudo on graphical apps, but the only issue I have noticed is that launching a second (third, forth...) app with sudo before closing the first will ask you for your password again, instead of remembering it. Otherwise, doesn't seem to be any issues.

someone should look into why that is happening though.

---

### Post by ashrack on 2006-02-08
but would still like to solve the error with 'gksudo'?

---

### Post by Zeroangel on 2006-02-08
Have you tried```
sudo gksudo nautilus
```
in xterm?

That's the cheap hack I would try if I were in your situation.

---

### Post by CompShrink on 2006-02-08
Haha, that got rid of my error with gksudo, but that's another workaround not "fixing the problem."

And is that even any better than just straight calling sudo to it? Wouldn't it still have whatever issues straight calling the app with sudo does? From my tests, it still has the not-remembering-password issue as does a straight call with sudo, so it's the same as my solution, isn't it?


Also, very slightly, that delays the launch of the program for me if I use sudo to call gksudo.

---

### Post by aysiu on 2006-02-08
Don't launch ```
gksudo nautilus
``` from the terminal. Create a launcher/keyboard shortcut for the command or press Alt-F2 first.

---

