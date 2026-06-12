---
title: "gksu stopped working"
date: 2006-07-02
forum: Desktop Environments
---

### Post by bobby on 2006-07-02
hi,
this happened suddenly : i can't start any app as root (like synaptic for example) anymore.
I've tried dpkg-reconfigure sudo and gksu but it didn't help
```
$ gksu synaptic
(asks for password)

Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified
Gtk-WARNING **: cannot open display:

```

so I followed [this]("http://forum.ubuntu-fr.org/viewtopic.php?id=43120") (in french) :
```
$ sudo visudo
Defaults  !lecture,tty_tickets,!fqdn,env_reset,env_keep+="DISPLAY HOME XAUTHORIZATION LANG LANGUAGE LC_* USER"
$ sudo ln -fs /home/USERNAME/.Xauthority /root/.Xauthority
$ sudo chown USERNAME.root /home/USERNAME/.Xauthority
```
And now, 
$ gksu synaptic
asks for password, and after that, nothing happens, no error messages, neither in the console nor in the logs

I also noticed that if I
$ gksu **-k** synaptic,
everyhing works fine

So I made an alias gksu='gksu -k', wich does the trick in the console, but not in the applications menu.

Thanks for any help or idea

---

### Post by ajgreeny on 2006-07-02
Shouldn't it be *gksudo synaptic*, rather than *gksu synaptic*?  That's the usual command in ubuntu using gnome.  In kde it's *kdesu synaptic*.

---

### Post by bobby on 2006-07-02
On my machine, /usr/bin/gksudo is a symbolic link to /usr/bin/gksu
And if you edit the menu entry that lauches synaptic, the command that is lauched is : "gksu /usr/sbin/synaptic"

---

