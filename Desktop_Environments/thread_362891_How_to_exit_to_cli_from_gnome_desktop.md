---
title: "How to exit to cli from gnome desktop?"
date: 2007-02-16
forum: Desktop Environments
---

### Post by forzagrifo on 2007-02-16
I just installed ubuntu-desktop on ubuntu dapper server.  How do I exit back to cli?  I don't want to switch back to cli (i.e. using Ctrl-Alt-F2).  I want to **exit** gnome outright and go to cli.

And how do I make it so that I can keep using cli instead of showing the gnome login page when I boot up the machine?

And how to start gnome desktop when I'm using cli?

Thanks in advance.

---

### Post by GoingDown on 2007-02-16
To exit to cli:

close gnome session (normal exit button, and then logout)
After that, press ctrl+alt+F1
log in
sudo /etc/init.d/gdm stop (it will stop gdm & X completely)

Warning. It seems that last step might give you blank screen, computer works but you cannot see anything... at least for me. Somebody said that pressing <ctrl><alt>F1 again after stopping gdm might help.

To disable X and start text-only (there is billions of ways, here is one of them) :
start console
sudo update-rc.d -f gdm remove

To get it back:
sudo update-rc.d gdm defaults

If you want to go to X from cli:
startx

---

### Post by forzagrifo on 2007-02-16
> **GoingDown said:**
> 
If you want to go to X from cli:
startx

Thx for quick reply, but this doesn't work for me.  I have xserver-xorg installed and startx will start the xserver desktop instead of gnome.  Any idea?

---

### Post by ashmew2 on 2007-02-16
as far as i know the desktop is X server and the session is gnome. Have u tried going to the normal graphical login page , pointing to the settings (its on the lower left corner on my system) and clicking Session and doing GNOME as Default ?
let me know what happened.

---

### Post by mannheim on 2007-02-16
On a gnome setup, if the gui is not running (i.e. no graphical login manager or X server) and you are the command-line, you can start things up again with

```
sudo /etc/init.d/gdm start
```

or (essentially the same thing, but for some reason preferred, I think):

```
sudo invoke-rc.d gdm start
```

In place of "start" you can also use "restart", which will stop any existing copy of the login manager (as well as all the sessions started from the graphical login), and will start a new one.

---

### Post by GoingDown on 2007-02-16
It seems ubuntu doesn't set up default X11 session to gnome. 

You can do it by creating/modifying your ~/.xinitrc file. See documentation from here: [http://doc.gwos.org/index.php/CustomXSession](http://doc.gwos.org/index.php/CustomXSession)

---

