---
title: "xession and screensaver"
date: 2008-01-29
forum: Desktop Environments
---

### Post by bloodniece on 2008-01-29
well, im trying to sneak Linux into my workplace and one way I can is to use legacy workstations as thin clients for our terminal server.

I created an xsession that starts X and tsclient. GDM is set to autologin too. This works fine.  I need a screensaver of some sort.  Any suggestions?

---

### Post by deeann on 2008-01-29
Are they former Windows machines or are you using existing thin client NC workstations like HDS/NetOS?

(edit- if they are former Win PCs, I'd go with something standard looking like the pipes screensaver. Or you could use GLtext and make it say Windows (some version):tongue: )

---

### Post by bloodniece on 2008-01-30
They are beige box Windoze machines.  I like the fake Windows screensaver idea.:)
So, i could add xscreensaver as another startup app in the xsession file?

Here is what I have so far

```

# turn on screen blanking
/usr/bin/X11/xset s on
/usr/bin/X11/xset -dpms

# allow local user access to windows
/usr/bin/X11/xhost +local:

# make blue bars black
/usr/bin/xvattr -a XV_COLORKEY -v 0

# showtime
/usr/bin/X11/xsetroot -solid "#000000" &
/usr/bin/unclutter -idle 1 &
#xterm -font 9x15
/usr/bin/tsclient

```

---

### Post by deeann on 2008-01-31
Just remembered something- some of them were resource hogs network-wise.  

If you're setting them up as thin client workstations here's a good reference place so you can set up locking and timeout (if needed) and that it exits clean:

[http://www.jwz.org/xscreensaver/man1.htm](http://www.jwz.org/xscreensaver/man1.htm)

I would try it locally on one machine, find the screensaver you like than back it up and install that as the global config.

---

