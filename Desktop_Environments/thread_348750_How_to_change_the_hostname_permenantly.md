---
title: "How to change the hostname permenantly?"
date: 2007-01-29
forum: Desktop Environments
---

### Post by mesh2005 on 2007-01-29
My machine has the default hostname "ubuntu-desktop". How can I configure it to be renamed to another name automatically?
Thank you

---

### Post by taurus on 2007-01-29
You change it **_both_** in /etc/hostname and /etc/hosts.  Remember, whatever you make a change to /etc/hostname, you need to use the same name in /etc/hosts or you would have a one dead machine; can't use sudo and some network apps won't work.

So, boot into recovery mode and edit those two files.

```
nano /etc/hostname
nano /etc/hosts
```
Hold down <Ctrl> while pressing x to exit.  Answer the questions with Y and Return.

---

### Post by tweedledee on 2007-01-31
For a GUI alternative that does exactly the same thing, go to System -> Administration -> Networking -> General and change the host name.

---

### Post by dfreer on 2007-07-05
> **tweedledee said:**
> For a GUI alternative that does exactly the same thing, go to System -> Administration -> Networking -> General and change the host name.

...But GUI's are no fun :(

---

### Post by benzies on 2007-07-05
sudo hostname (enter host name)

I think that should change it.

---

### Post by clint1010 on 2007-07-05
> **dfreer said:**
> ...But GUI's are no fun :(

:shock:

---

### Post by bliffle on 2007-11-27
I changed the hostname from a terminal session . closed the terminal session and now I can't open a new terminal session.

---

### Post by Ankara23 on 2007-11-27
>  I changed the hostname from a terminal session . closed the terminal session and now I can't open a new terminal session.


You will have to log out, and then log back in again in order to open new applications or get a terminal.

---

### Post by schnuser on 2008-02-01
> **benzies said:**
> sudo hostname (enter host name)

I think that should change it.

If I do this, then after reboot the old hostname is restored and the new hostname is lost. I dont know why.

---

### Post by mojoman on 2008-02-02
You listen to Benzies. The command line is your the safest bet. Have a look at the man page for hostname. I wouldn't go mucking about in system configuration files without knowing what I was doing. If you have a quick read at the man page you know what the command you're about to punch in will do. Reading the man page for hostname takes about five minutes.

My second bet would be the GUI alternative suggested by Tweedledee (if that option is available in your setup).

---

### Post by ravenvii on 2008-06-09
Oh crap, I just changed my hostname, I was expecting that I couldn't open any programs until I log out and log in... but I couldn't open the Quit... dialog either!

How do I log out or restart? I'm completely stuck!

---

