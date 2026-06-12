---
title: "Ubuntu ubroken... cant login"
date: 2006-01-17
forum: General Help
---

### Post by huey90 on 2006-01-17
Hi all,

This is my first post and I am very new to linux.  I have been using Ubuntu for a few months now and it is the only distro I have spent much time with.  I am currently experiencing a problem that is a bit over my head.

When I start my computer, I am taken to the login screen, but when I try to login and load gnome I get the following error:

```

~/.xsession-errors files

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/X11/sessreg &#8211;a &#8211;w /var/log/wtmp &#8211;u /var/run/utmp &#8211;x &#8220;/var/lib/gdm/:0.Xservers&#8221; &#8211;h &#8220;&#8221; &#8211;l &#8220;:0&#8221; &#8220;ma&#8221;
/etc/gdm/Xsession: Beginning session setup&#8230;
_IceTransTransNoListen: unable to find transport: tcp
_IceTransmkdir: ERROR: euid != 0,directory /dev/X will not be created.
_IceTransmkdir: ERROR: Cannot create /dev/X
_IceTransPTSOpenServer: mkdir (/dev/X) failed, errno =13
_IceTransOpen: transport open failed for pts/m500:
&#8230;(a few more lines similar to these)...

** (gnome-session:8604): WARNING **: Unable to read ICE authority file: /home/ma/.ICEauthority

```

I believe I had done three main things prior to the failed boot that may be the cause of the errors

1.	Installed Opera and followed this guide:

[http://ubuntuforums.org/showthread.php?t=78468&highlight=opera](http://ubuntuforums.org/showthread.php?t=78468&highlight=opera)
        I eventually got plugins to work, but in the process may have damaged libXm.so.2 or libXm.so.3.  Would this result in the errors I am getting?

2.	I configured my touchpad in xorg.conf, but have since restored to an older copy of xorg.conf that I know worked, so this must not be the problem.

3.	Under startup services (I think that&#8217;s what it is called) I tried to add a shell script to mount my windows partition.  I entered it as &#8220; ./winmount &#8220; fully expecting it to not work, but I was interested to see what would happen.  Can this lead to gnome not loading at all.  If so how do I get there without using the gui to remove this?

---

### Post by lamego on 2006-01-17
Add a new user from the terminal window and try to login with it, just to make sure its a system related issue.

Installing opera shouldn't hurt your X unless you did something REALLY bad :)

Creating a startup script to mount your windows partitions is a bad option, you are ignoring the functions of /etc/fstab, anyway it shouldn't mess with the gnome login.

---

### Post by cbudden on 2006-01-17
When you have logged in as a different user, open up a root nautilus so you can access your original home folder, then rename your old .ICEauthority file to something else, like .ICEauthority.bak, log out and try to log into your original account again.

---

### Post by huey90 on 2006-01-17
[QUOTE=lamego]Add a new user from the terminal window and try to login with it, just to make sure its a system related issue.
[/QUOTE]

How do I add a new user from the terminal?

---

### Post by ferebee on 2006-01-17
Hi Huey,

I had this same problem today, and the info in this thread solved the problem for me.
[http://www.ubuntuforums.org/showthread.php?t=116900&highlight=ICEauthority]("http://www.ubuntuforums.org/showthread.php?t=116900&highlight=ICEauthority")

Good Luck!

---

### Post by huey90 on 2006-01-17
^ Hey that was too easy.  I really appreciate the help guys, the ubuntu community rocks.

edit:  why does this happen anyway?

---

