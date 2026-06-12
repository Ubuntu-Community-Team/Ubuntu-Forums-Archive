---
title: "gnome-settings-daemon error"
date: 2006-10-18
forum: Desktop Environments
---

### Post by tsheller on 2006-10-18
> Unable to start the settings manager 'gnome-settings-daemon'.
Without the GNOME settings manager running, some preferences may not take effect. This could indicate a problem with Bonobo, or a non-GNOME (e.g. KDE) settings manager may already be active and conflicting with the GNOME settings manager.

Anyone experience this before? Im pretty clueless on what to do, but I dont even see gnome-settings-daemon running, and im not sure what the others could be. 

if I do 
gnome-settings-daemon start/resart, it tells me I can only run one xsettings manager at a time, so, how do I figure out which one it is!

thanks

---

### Post by tsheller on 2006-10-18
yeah.. I sorta fixed it. Killing the old one made it restart itself, and the error message went away.

---

### Post by gosh on 2006-11-14
make sure you have 

auto lo

in your /etc/network/interfaces

---

### Post by blh1983 on 2008-04-10
I'm super new to Linux and Ubuntu.  If I don't have auto lo, how do I get it?  and or how do I "Kill" the old one????  Please explain step by step.  I'm still getting used to everything not microsoft.

---

### Post by kpkeerthi on 2008-04-11
**To Kill**:
```
killall gnome-settings-daemon
```

If it complains permission denied,
```
sudo killall gnome-settings-daemon
```

Post the output of the below command
```
cat /etc/network/interfaces
```

* All these commands should be run from a terminal. Applications -> Accessories -> Terminal

---

### Post by Cammy on 2008-04-11
Lovely.  I just got this same error as well, out of the blue.

I'm running Feisty with compiz-fusion.  The thing is, I haven't changed a thing in weeks, so I have no idea why this would suddenly appear.

And I do have "auto lo" in /etc/network/interfaces

If I do "killall gnome-settings-daemon" the desktop appearance changes completely, so it seems it *was* running.

---

### Post by gali98 on 2008-04-11
Its strange...It actually happens to me all the time, but I have a really slow computer. Maybe its because you login before the daemon has time to start up... I'm clueless. I know that when ever I use an rt-kernel (i.e. Ubuntu studio) that it always happens to me. Usually whenever it happens it means everything defaults to gnome (no tango).
I just hit ALT+F2 (opens the run command dialog)
and do 
sudo gnome-settings-daemon

Whenever I do that evrything comes back in a few seconds. But that doesn't sound like the same problem.

Kory


EDIT:

also just curious, but what does your network interfaces have to do with it?

---

