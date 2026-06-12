---
title: "edit default vncserver xstartup file"
date: 2009-02-18
forum: General Help
---

### Post by pytheas22 on 2009-02-18
I have vncserver installed on a multi-user Ubuntu machine.  To launch a VNC session, users first connect via ssh, then run 'vncserver' to start a new server session, which they can then connect to using a VNC client.

The problem is that the default VNC xstartup file that gets created the first time vncserver is run for a particular user looks like this:

```
#!/bin/sh

# Uncomment the following two lines for normal desktop:
# unset SESSION_MANAGER
# exec /etc/X11/xinit/xinitrc

[ -x /etc/vnc/xstartup ] && exec /etc/vnc/xstartup
[ -r $HOME/.Xresources ] && xrdb $HOME/.Xresources
xsetroot -solid grey
vncconfig -iconic &
xterm -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
**twm &**

```

As the last line of the script indicates, it calls twm instead of gnome-session, but my users need to use Gnome, not twm.

The problem is easily fixed by changing the xstartup file to this:
```

#!/bin/sh

vncconfig -iconic &
eval `dbus-launch --sh-syntax --exit-with-session`
gnome-session &

```

But because there are multiple users on the system--and because more may be added in the future when I'm not there to iron this out--it's not practical to go into each user's /home/*/.vnc directory and modify the xstartup file there.  I know I could probably write a cronjob to take care of this, but I want a cleaner solution.

So what I want to do is figure out where the default template for the xstartup file is, and edit that.  I've searched everywhere I could think, but can't figure out where the system gets the default xstartup script from.  Does anyone have a clue?

---

### Post by adriano72 on 2009-02-18
> So what I want to do is figure out where the default template for the xstartup file is, and edit that. I've searched everywhere I could think, but can't figure out where the system gets the default xstartup script from. Does anyone have a clue?

assuming you're using vnc4server, the file you want to edit is:

/usr/bin/vncserver

despite in the bin folder, it's actually a perl script. Look for the variable called $defaultXstartup

- Adriano

---

### Post by pytheas22 on 2009-02-18
You got it, thanks so much.

---

