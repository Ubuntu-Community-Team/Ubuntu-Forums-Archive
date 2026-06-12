---
title: "X window fails to start"
date: 2006-08-07
forum: Desktop Environments
---

### Post by satimis on 2006-08-07
Hi folks,

Ubuntu-6.06-amd64

After running "sudo apt-get upgrade" X windows/Gnome desktop fails to start.  On login screen typing User_name and password it prompts a black screen, hanging there for prolonged time.

$ sudo nano $HOME/.xsession-errors```

......
......
x-window-manager:4843:Gdk-Warning ** Locale not supported by Xlib
x-window-manager:4843:Gdk-Warning ** cannot set locale modifier
```

Ran;

$ sudo dpkg-reconfigure locales```

....
.....
.....
universal time is now Mon Augu 7  01:31:45 UTC
Run 'tzconfig' if you wish to change it
```

$ sudo rm /tmp/.X0-lock
$ sudo startx

A bright screen started with mouse pointer on it which can be moved around.
(I suppose it was KDE desktop but I haven't installed it)


Ctrl+Alt+F4
$ sudo shutdown -r now

Rebooted PC.

PC started as normal but X-window still could not be started with a black screen hanging.

$ sudo cat $HOME/.xsession-error```

......
......
x-window-manager:4843:Gdk-Warning ** Locale not supported by Xlib
x-window-manager:4843:Gdk-Warning ** cannot set locale modifier
```

Still the same warning.

Pls advise how to fix this problem.  TIA

B.R.
satimis

---

### Post by mlind on 2006-08-07
You should restart X instead of manually removing the lock file and creating another Xserver session (this probably confuses X pretty much).

Does /var/log/messages contain any other information why Xserver is failing?
What gfx card do you have and what drivers do you use for it?

(what language-packs do you have installed?)

---

### Post by satimis on 2006-08-07
Hi mlind,

Problem fixed by re-ran;

$ sudo apt-get upgrade```

....
....
Setting up Gnome panel
Setting up Gnome applets
Setting up Gnome terminal
Setting up nautilus
```

Rebooted PC.  This time Gnome desktop started.

$ cat $HOME/.xsession-error
The warnings were still there.

Is it strange???

Anyway tks for your advice.

B.R.
satimis

---

### Post by mlind on 2006-08-07
I think your last upgrade process was somehow interrupted and those packages were left partially installed/unconfigured. Good you got it sorted out.

---

### Post by satimis on 2006-08-07
Hi mlind,

> I think your last upgrade process was somehow interrupted and those packages were left partially installed/unconfiguredNo.  Neither interruption nor complaint were found.  At its finish, just said 'upgrade complete' something like that.

B.R.
satimis

---

