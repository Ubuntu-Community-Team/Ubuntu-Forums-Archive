---
title: "Multiple sessions, how???"
date: 2010-01-31
forum: Desktop Environments
---

### Post by Barriehie on 2010-01-31
Hey All,
So sometimes I screw up while 'optimizing' and would like to have access to another session.  I've read the post [here](http://ubuntuforums.org/showthread.php?t=271674) and actually on one occasion was presented with the login screen on another virtual terminal.  I can't remember how I did it though and can't read my notes!
I've tried going to another terminal and from my text login:
```

sudo /usr/bin/startx /etc/init.d/gdm start -- :x

```
I've tried various numbers for x and have tried with and without a trailing &.

Any help on doing this, i.e. step 1, 2, 3, etc. will be greatly appreciated!

TIA,
Barrie

---

### Post by Barriehie on 2010-01-31
Just tried: (from tty1, logged in as root) 
```

sudo /usr/bin/startx /usr/bin/gnome-session -- :1 &
```
and it logged me in as root with a GUI session.  How do I get the login screen to choose sessions???

Anyone?

TIA

---

### Post by falconindy on 2010-02-01
Stop that, no biscuit. Don't start X as root.
```
xinit /usr/bin/gnome-session -- :1
```
This creates a new pts. You can switch back to the other one with ctrl-alt-f7 and back to the new one with ctrl-alt-f8.

---

### Post by Barriehie on 2010-02-01
> **falconindy said:**
> Stop that, no biscuit. Don't start X as root.
```
xinit /usr/bin/gnome-session -- :1
```
This creates a new pts. You can switch back to the other one with ctrl-alt-f7 and back to the new one with ctrl-alt-f8.

Thank you! :)  Worked as advertised!!!

Barrie

---

### Post by r_avital on 2011-11-17
Sorry to re-open, but:

I'm sure this was once possible, but when I try it now, this is the output:

```
snoopy@snoopy:~$ sudo xinit /usr/bin/gnome-session --:1

Fatal server error:
Server is already active for display 0
        If this server is no longer running, remove /tmp/.X0-lock
        and start again.


Please consult the The X.Org Foundation support 
         at http://wiki.x.org
 for help. 

 ddxSigGiveUp: Closing log
snoopy@snoopy:~$
```What am I missing?  Need to stop X before this?  If so, my original session (on Ctrl+Alt+F7) will be gone, right?

Also, where can I find this log so I can trim it?

BTW, when I run this without sudo, I get a permissions error (not authorized).

Thanks in advance

---

