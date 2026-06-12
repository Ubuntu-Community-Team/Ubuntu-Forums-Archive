---
title: "gDesklets issue:"
date: 2006-11-11
forum: Desktop Environments
---

### Post by cgrenier on 2006-11-11
I'm running Beryl using the Nvidia 1.0-9xxx drivers (so no AIGLX).  It all works well.  gDesklets also looks fine when I run it.

BUT recently the desklets themselves sometimes become "windows"; that is, they appear in the taskbar as "gdesklets-daemon" and aren't constant across all desktops.  When I use the taskbar to get rid of the windows, the desklets disappear.  Unfortunately this all happens very unpredictably - sometimes I boot and all the desklets are as they should be, without taskbar entries, constant across desktops... and sometimes they behave all like normal windows and have taskbar icons and are specific to a certain desktop.  And sometimes some are "windows" and some are proper desklets.  There seems to be no rhyme or reason.  I don't know how to fix this.  Any ideas?  

--CG

---

### Post by murlosad on 2006-11-16
I've been having similar problems. I actually had the same problems with beryl on suse so I think it's got to be something in the way the desklets interact with beryl, probably with the Emerald window manager. Nothing on the beryl forums about it though. I'll post if I'm able to find anything.

---

### Post by pastorjay on 2006-11-24
Any answer to this?

---

### Post by ridetheteapot on 2006-12-20
I am having the same problem with the same setup. I'm not sure if its by chance but, if you turn of the wobbly windows  option Move Window Types: uncheck normal before starting gdesklets.

Its not a fix, but i guess it means the problem is wobbly's fault.

a similar problem is gdesklets and 3d world, because raisng desklets looks dumb, does anyone know if there is a way to exclude windows from 3d world?

---

### Post by VortexICS on 2006-12-26
Me and a couple of other friends are suffering the same issue: we see gdesklets in the task bar. Any resolution on this so far ?

---

### Post by PeTiNgA on 2007-01-07
I'm having the same problem (gdesklets-daemon in the taskbar on boot) using Ubuntu 6.10, nvidia drivers 1.0.8776, beryl 0.1.4 and gDesklets 0.35.4-1. I've already searched for a solution but still no luck. Although, if I close the gdesklets and re-open, they do not appear in the taskbar anymore.

---

### Post by mahiyar on 2007-01-16
Try to open the desklets from the menu i.e file -> run, instead of double clicking it, that solved my problem.

---

### Post by murlosad on 2007-01-16
I'm still having the same problems, although with one of the udates to beryl-svn the 3d world doesn't raise the gdesklets anymore.  I did notice that if I launch gdesklets while using metacity and then switch to emerald they don't show up in the task bar.  Also they only show on one side of the cube.

Still haven't found anything on the beryl forums about this either.

---

### Post by slaytanic on 2007-02-01
i think you can solve this by editing your session and set gdesklets to run first than beryl
it should work

---

### Post by mjpoetic on 2007-02-01
> **slaytanic said:**
> i think you can solve this by editing your session and set gdesklets to run first than beryl
it should work
I was trying to figure out how to do just that...and I don't think it can be done using gnome-session-properties.  So, how does one get this done?

---

### Post by sen~ on 2007-02-04
I had this problem as well and just starting gdesklets before beryl doesn't work for me.
My solution was to make a startup script for beryl:

```
sudo mousepad /usr/bin/beryl-start
```

edit the file like this:
> #!/bin/bash
gdesklets &
AddYourAutostartApps &
sleep 10
beryl-manager

make the script executeable:
```
sudo chmod a+x /usr/bin/beryl-start
```

add the script to your Startup Programms in the gnome-session-properties.

---

