---
title: "How to run KDE Partition Manager as a root?"
date: 2009-05-05
forum: General Help
---

### Post by yildiz.a on 2009-05-05
Hi,

I recently installed KDE partition manager on Ubuntu 9.04. But when I run 

it as a normal user, it says you can not use unless you become root. How 

can I fix this? Or what is the command to run this program, I couldn't find 

it? Thanks...

---

### Post by BslBryan on 2009-05-05
You should run "sudo (whatever the application name is)"

So, for example:
```
sudo audacity
```

Su stands for Super User, which is basically the computer's administrator.  Sudo means Super user, Do *this command.*  I hope I've helped. :)

---

### Post by yildiz.a on 2009-05-06
Thank you, but I know how to run an application as root/superuser. I asked for what the binary file name of KDE partition manager is.

---

### Post by dabl on 2009-05-06
> **yildiz.a said:**
> Thank you, but I know how to run an application as root/superuser. I asked for what the binary file name of KDE partition manager is.

Looks like you are asking about this:

[http://www.volker-lanz.de/en/software/partitionmanager/](http://www.volker-lanz.de/en/software/partitionmanager/)

which is found here:

[http://sourceforge.net/projects/partitionman/](http://sourceforge.net/projects/partitionman/)

It is for KDE 4 (not Gnome), and it appears to be only a Beta version at this time.  I would think it installed the executable in /usr/bin -- can you not find it there?  It probably requires qt libraries to work, and since it is Beta, it may not have its dependencies fully documented.  Bottom line -- you might have to install kubuntu-desktop and run it under KDM to even make it run.

---

### Post by VolkerLanz on 2009-05-11
> I recently installed KDE partition manager on Ubuntu 9.04. But when I run it as a normal user, it says you can not use unless you become root. How can I fix this?

It does ask for your password via kdesudo when using a KDE desktop. If you're trying to run this from a GNOME application menu, that might not work, because GNOME probably doesn't honor the setting to ask for authentication.

In this case, run the program from the command line with sudo:

```
$ sudo partitionmanager
```

> I would think it installed the executable in /usr/bin -- can you not find it there?


Yes, it does. For a little bit of advanced knowledge here:

```
$ dpkg -L partitionmanager | grep /bin/
/usr/bin/partitionmanager
```

This tells us what the executable is called for the package "partitionmanager".


> It probably requires qt libraries to work, and since it is Beta, it may not have its dependencies fully documented. Bottom line -- you might have to install kubuntu-desktop and run it under KDM to even make it run.


I have neither created the package that comes with Ubuntu 9.04 nor checked to see if it pulls the correct dependencies when no KDE is installed at all, but from the control file it looks ok.

In general, you never ever need kubuntu-desktop or KDM to run any KDE app. Also, KDM is the login manager, which has nothing to do with the desktop you're using in the end.

---

