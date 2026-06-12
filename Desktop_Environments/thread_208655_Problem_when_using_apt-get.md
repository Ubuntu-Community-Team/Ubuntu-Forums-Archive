---
title: "Problem when using apt-get"
date: 2006-07-03
forum: Desktop Environments
---

### Post by bonefry on 2006-07-03
I get a strange error that is referring to a QT object, although all I do is execute apt-get in the console ...

[INDENT]DESTROY created new reference to dead object ' Qt::VBoxLayout', <> line 1 during global destruction.[/INDENT]

I haven't noticed anything wrong, as apt-get finishes the job, but it bothers me.

---

### Post by encompass on 2006-07-04
interesting.... I don't think apt-get or synaptic use qt.... it has something to do with your KDE install.  KDE is big into QT so I figure it is nothing big if your system is working fine. IMO

---

### Post by WirelessMike on 2006-07-07
I think this may be a result of configurations changed by "easy Ubuntu" or Automatix.  My friend and I were able to duplicate the problem on 3 different machines running kubuntu64, kubuntu and xubuntu after installing easy ubuntu.

What happened is that debconf was reconfigured to use the gui of choice (in this case kde).

The solution is to reconfigure debconf.  To confirm the problem, use command-line to remove an app (say gimp) and then reinstall it.  You should get some strange errors including the one you mention in the first post.

Now enter the following line command:
> sudo dpkg-reconfigure debconf

In the gui that appears, change the interface to "dialog"
I set the priority to medium, but set it wherever you like, the interface was the problem.

Now remove the same app as before and reinstall it again.  You should not get those errors.

By the way--  If the gui does not come up with the above command, su to root and run the same command (without the sudo, of course).  It will come up in dialog, but the interface will not show dialog as your preference.  You can change it here and it will change it for all users just as sudo would have.

Hope that helps.

---

