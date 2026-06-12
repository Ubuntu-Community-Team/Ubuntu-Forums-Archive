---
title: "Runlevel change won't &quot;stick&quot;"
date: 2007-11-18
forum: Debian
---

### Post by arijarot on 2007-11-18
I tried to change from the default runlevel 2 to 3 using ```
telinit 3
```. I check to see if it works using ```
runlevel
``` and it does. But, on rebooting, I enter runlevel 2 again.

Why won't /etc/rc3.d save the changes?

---

### Post by Iandefor on 2007-11-18
telinit changes the current runlevel. It doesn't change what the default runlevel is.

I'm pretty sure the default runlevel on Debian is set in the configuration file /etc/inittab. There is a [manpage]("http://www.netadmintools.com/html/5inittab.man.html") describing the format if the contents of the file aren't descriptive enough.

---

### Post by arijarot on 2007-11-19
> **Iandefor said:**
> telinit changes the current runlevel. It doesn't change what the default runlevel is.

I'm pretty sure the default runlevel on Debian is set in the configuration file /etc/inittab. There is a [manpage]("http://www.netadmintools.com/html/5inittab.man.html") describing the format if the contents of the file aren't descriptive enough.

Thanks a lot :)

---

### Post by Iandefor on 2007-11-20
> **arijarot said:**
> Thanks a lot :)Not a problem.

FYI, /etc/inittab is no longer used on Ubuntu systems because Ubuntu is transitioning from a System V-style init system to Upstart.

---

### Post by arijarot on 2007-11-20
Hmmm... I'm using debian. It boots into runlevel three, but it's not what it's supposed to be. I read that runlevel 3 is cli, networked, multi-user, but it just boots into the gui as usual. Which runlevel boots into the tty, is networked...?

---

### Post by Pobega on 2007-11-23
> **arijarot said:**
> Hmmm... I'm using debian. It boots into runlevel three, but it's not what it's supposed to be. I read that runlevel 3 is cli, networked, multi-user, but it just boots into the gui as usual. Which runlevel boots into the tty, is networked...?

You may be interested in the program sysv-rc-conf for changing what starts/stops at which runlevels.

**Edit:** Or perhaps you'd be interested in file-rc, which I find easier than sysv-rc-conf. file-rc changes the whole sysv system to a faster, easier to configure (/etc/runlevel.conf) version of sysv.

---

### Post by sillyVM on 2008-08-05
To make it stick do:

sudo vi /etc/event.d/rc-default

Change the 

telinit 2

To desired runlevel.

Or if you read the script, you can actually created a a /etc/inittab file to make the run level change. but it's up to you.

---

