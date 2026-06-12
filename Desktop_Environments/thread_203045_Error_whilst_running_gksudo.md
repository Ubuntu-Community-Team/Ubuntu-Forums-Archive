---
title: "Error whilst running gksudo"
date: 2006-06-24
forum: Desktop Environments
---

### Post by Hop-Frog on 2006-06-24
I opened a terminal and tried to use gksudo to run graphical applications:

```
$ gksudo gedit

(gedit:####): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

$ gksudo gnome-terminal

(gnome-terminal:####): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
```

I have searched Google for this error message, but this returned zero results.  This error does not happen when simply using the sudo command.

---

### Post by bulldog on 2006-06-24
Try sudo gedit instead.
That will give you no errors:D 

Don't know why you want to use gksudo.

---

### Post by bscbrit on 2006-06-24
Are you trying to run this on a local machine, or have you used ssh or something else to log into a remote machine?

If you are local, what do you want to achieve?

---

### Post by aysiu on 2006-06-24
*gksudo* is the proper prefix for graphical applications. When you launch it from the terminal you may see "errors," but nothing is actually wrong.

If you use *sudo* for graphical applications, you will always have to launch it from the terminal (no keyboard shortcut, no launcher icon), and...

1. Sometimes it plain just won't work for certain applications
2. Sometimes it will corrupt the permissions on your configuration files

It's always best to use *gksudo* or *kdesu* for graphical applications and *sudo* for terminal applications. Ignore the "errors"--I've never seen them actually have an adverse side effect, but *sudo* with graphical applications sometimes does have an adverse side effect.

---

### Post by aysiu on 2006-06-24
[QUOTE=bscbrit]Are you trying to run this on a local machine, or have you used ssh or something else to log into a remote machine?

If you are local, what do you want to achieve?[/QUOTE]
```
gksudo gedit
``` allows you to edit graphically a file owned by root.

If you believe *sudo* is great for graphical applications, just keep doing it until your .ICEauthority gets owned by root and then see how happy you are. Read more here:
[http://www.ubuntuforums.org/showthread.php?t=181867](http://www.ubuntuforums.org/showthread.php?t=181867)
[http://archlinux.org/pipermail/arch/2006-February/008674.html](http://archlinux.org/pipermail/arch/2006-February/008674.html)

---

### Post by bscbrit on 2006-06-24
Aysiu

Yes I know - but sudo is already working for him so why try to use gksudo in particular?  You are also correct in describing that gksudo is used for graphical applications but it does give error messages - even if there is nothing actually wrong.  I find that I can use gedit as root if I start it with 'sudo' and my question was intending to discover why hop-frog wanted to use gksudo.  The same solution was suggested by bulldog. (I accept the point made about ICEauthority) but its never been a problem for me - perhaps I've just been lucky).

I was just confirming that this was on the local machine because, as you know, if you use 'ssh <anothermachine>' then you cannot start graphical applications that require X. In such a case one would have to use 'ssh -X <anothermachine>'

---

### Post by aysiu on 2006-06-24
Let's just say I've changed my stance since [this thread](http://www.ubuntuforums.org/showthread.php?t=165957). It's a matter of encouraging good practice through a consistent message. I don't want users to have to keep track of "This is a list of graphical applications that are just fine to use with *sudo* and this is a list of applications that aren't."

Why not just use *gksudo* and *kdesu* for graphical applications **all the time** and know it's not going to screw up your system?

---

### Post by bscbrit on 2006-06-24
Ok, I can live with that.  But wouldn't it be nice if someone could fix the unnecessary error messages as well? :-D

---

### Post by aysiu on 2006-06-24
[QUOTE=bscbrit]Ok, I can live with that.  But wouldn't it be nice if someone could fix the unnecessary error messages as well? :-D[/QUOTE]
Yes. Maybe I'll file a bug report on it.

**Edit**: Never mind. [It's already been filed](https://launchpad.net/distros/ubuntu/+source/gksu/+bug/23917), but the developers consider it low priority.

In the meantime, I'd rather reassure people those "error" messages are innocuous than walk them through trying to *chown* the .ICEauthority file just so they can log in.

---

### Post by bscbrit on 2006-06-24
I'll try to remember to give the same message!

Thanks.

---

