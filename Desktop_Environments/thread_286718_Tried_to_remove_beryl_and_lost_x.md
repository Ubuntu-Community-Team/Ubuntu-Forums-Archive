---
title: "Tried to remove beryl and lost x"
date: 2006-10-28
forum: Desktop Environments
---

### Post by roncrump on 2006-10-28
Hi,

I have been playing with beryl on Ubuntu 6.06.

I only really wanted to see what it could do, and it is quite pretty, but when it broke (flickering windows borders) after the last upgrade, I thought I would remove it.

Anyway, having installed using the instructions on [this thread]("ubuntuforums.org/showthread.php?t=268036"), I thought I'd be alright just to work through them backwards. Dumb move, apparently. 

When I rebooted X didn't start, so I logged in and tried startx and it said there was no driver for my NVidia card. Changed back to nv in xorg.conf, and startx then worked, but X doesn't come up automatically on reboot. And, I get a message that the GNOME_Panel_WirelessApplet (I think that was it, something like that anyway) had a problem, so that isn't starting up.

EDIT: I also seem to have lost totem. Don't know how that has happened.

So, any suggestions welcome. The process I followed to get myself into this mess was:

(1) Went to System –> Preferences –> Sessions –> Startup Programs and removed the following two entries:
```
xmodmap -e "keycode 22 = BackSpace"
beryl-manager
```

(2) sudo gedit /etc/gdm/gdm.conf-custom
and removed the following from below the [servers] section:
```
0=Xgl

[server-Xgl]
name=Xgl server
command=/usr/bin/Xgl :0 -fullscreen -ac -accel glx:pbuffer -accel xv:fbo
flexible=true
```

(3)
```
sudo apt-get remove xserver-xgl libgl1-mesa xserver-xorg libglitz-glx1 beryl emerald emerald-themes
```

(4) sudo gedit /etc/apt/sources.list
and removed:
```
deb [http://www.beerorkid.com/compiz](http://www.beerorkid.com/compiz) dapper main aiglx
deb [http://media.blutkind.org/xgl/](http://media.blutkind.org/xgl/) dapper main aiglx
```

(5) restart.

I'd like to know how to put it right (that is, back to a functioning system without beryl installed), but would also like to know what I have done to make this mess (for future reference).

Thanks for reading this far.

Regards,
Ron Crump

---

### Post by roncrump on 2006-10-28
Things I've tried this evening:

(a) sudo apt-get install libgl1-mesa xserver-xorg libglitz-glx1
Since these didn't have xgl or beryl/emerald in their names, so I
thought maybe there were versions of these I needed.

Which didn't work, so I:

(b) re-installed the nvidia drivers and then followed the xgl and
beryl installation instructions again, to hopefully put it back
to where it was before I started removing stuff.

Again, no joy. This makes me think that I have stuffed up a file
or something along the way.

If I just try to upgrade to Edgy, is this likely to overwrite my
errors with clean files and hence fix my problem?

Ron.

---

### Post by roncrump on 2006-10-28
In addition, I am also getting a problem running gksu (ie if trying to start synaptic). I get a message saying the child process "gksu" cannot be started (No such file or directory), and I cannot find a gksu file (there seem to be other files related to it, eg gksu.conf, but not the program itself).

---

### Post by GoombaDoolies on 2006-11-02
Try here [http://www.ubuntuforums.org/showthread.php?t=268036&page=34]("http://www.ubuntuforums.org/showthread.php?t=268036&page=34")

I had a similar problem (though once i get around to putting on edgy, it should hopefully solve itself.  But this is how I uninstalled and reverted back to the old ATI driver (a must IMHO) on dapper.

Cheers,

---

