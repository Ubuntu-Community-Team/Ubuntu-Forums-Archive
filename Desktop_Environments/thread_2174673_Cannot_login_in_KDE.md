---
title: "Cannot login in KDE"
date: 2013-09-15
forum: Desktop Environments
---

### Post by jenny3 on 2013-09-15
Hello all,
I'd just finished configuring a new system when this happened: I get the login screen but entering the username/passwd results in a brief black screen and then back to the login screen.

The previous day I'd added large (10Tb) directories to the nepomuk config and it crashed during the night while indexing them. The problem started after the reboot.

I've tried removing all the .directories: .kde, .cache, .config, .local but there's no change.

I can log into another account, but I want to use that one !

It appears that X11 dumps core.

Here are a bunch of log files:
[core]("http://www.gdargaud.net/BugFest/Prob/core")
[auth.log]("http://www.gdargaud.net/BugFest/Prob/auth.log")
[kern.log]("http://www.gdargaud.net/BugFest/Prob/kern.log")
[lightdm.log]("http://www.gdargaud.net/BugFest/Prob/lightdm.log")
[syslog]("http://www.gdargaud.net/BugFest/Prob/sys.log")
[x-0-greeter.log]("http://www.gdargaud.net/BugFest/Prob/x-0-greeter.log")
[x-0.log]("http://www.gdargaud.net/BugFest/Prob/x-0.log")
[Xorg.0.log]("http://www.gdargaud.net/BugFest/Prob/Xorg.0.log")

There's no .xsession* or .Xauthority in my home

---

### Post by maestrobwh1 on 2013-09-15
If you are not terribly attached to your kde settings, you might be able to do something like 
```
mv ~/.kde ~/.kde.old 
```
in the directory of the profile you want to keep (from the working profile) then log in.

That generally resolved most of my kde issues... granted, all your customizations to kde apps will be reset, but you can go into your .kde.old directory and copy back some of your config files for appls like dolphin and such.

---

### Post by jenny3 on 2013-09-16
Thanks for the answer. I did and... no change. Still can't login.

---

### Post by carl4926 on 2013-09-16
As soon as you enter password 
Press Alt+SHIFT+F12

---

### Post by jenny3 on 2013-09-16
I will try that when I get back home, but I did try putting a file in /usr/share/X11/xorg.conf.d/ to disable compositing. I think it was:
> Section "Extensions"
    Option "Composite" "disable"
EndSection

---

### Post by SeijiSensei on 2013-09-16
Any permission problems in your home directory?  UID/GID's match up between the file system and /etc/passwd?

Another thing to try is to boot in to recovery mode, then run
```

# mount -o remount,rw /
# su username
$ cd
$ startx

```
and see if X throws any errors.

---

### Post by jenny3 on 2013-09-16
> Any permission problems in your home directory?  UID/GID's match up between the file system and /etc/passwd?
Nope. I ran find ! -uid 1000 and there was nothing. /etc/passwd and group look fine.

> 
Another thing to try is to boot in to recovery mode, then run
```

# mount -o remount,rw /
# su username
$ cd
$ startx

```
and see if X throws any errors.

I received ```
X: user not authorized to run the X server, aborting
xinit: giving up
```
So I did dpkg-reconfigure x11-common and changed from console to anybody, then startx went further and complained about some missing gnome (which I don't have). I reinstated my various .directories and after that I managed to login fine. Only kmail failed on first try and seems to be doing a lot of activities on the 2nd try. Probably because I removed the nepomuk folder.

Anyway thanks, I consider the case 99% closed.

---

