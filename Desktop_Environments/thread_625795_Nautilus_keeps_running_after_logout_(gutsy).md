---
title: "Nautilus keeps running after logout (gutsy)"
date: 2007-11-28
forum: Desktop Environments
---

### Post by goldix on 2007-11-28
Hi,

if a user logs out from our gutsy system it sometimes happens that there are still some running processes doing heavy io on our NFS server. Here is an example: User "x" logs out and then there are still processes left of x:

```
x   24145  0.1  3.4 131360 15756 ?        S    14:13   0:13 nautilus --no-default-window --sm-client-id default2
x   24149  0.0  0.1   8644   788 ?        S    14:13   0:00 /usr/lib/gamin/gam_server
x   24150  0.0  0.2  45296  1264 ?        Ssl  14:13   0:00 /usr/lib/bonobo-activation/bonobo-activation-server --ac-activate --ior-output-fd=18
x   24175  0.0  0.0   8180   404 ?        S    14:13   0:00 /usr/lib/nautilus-cd-burner/mapping-daemon
x   24497  0.0  0.7  35656  3536 ?        S    14:17   0:00 /usr/bin/artsd -F 10 -S 4096 -s 60 -m artsmessage -l 3 -f
x   25430  0.0  0.9  10464  4284 ?        S    17:19   0:00 /usr/lib/libgconf2-4/gconfd-2 13

```
The "nautilus" process causes a very high load on our NFS server (homes are exported via nfs).

Why doesn't nautilus quit if a user does a logout? btw: I just do a kill, NOT a kill -9 and nautilus stops immediately.

Did anyone experience that? Is there a tool to stop processes from not loged in users?

Thanks!

---

### Post by drdrewusaf on 2007-12-09
In the same boat...I guess no one has an answer to this?



Drew

---

### Post by ja4509 on 2007-12-12
Me too this is something that continues from earlier releases btw!

In the past on my laptop it wasn't an issue but I replaced my Red Hat server with Ubuntu and this is not going to cut it. I hope that someone has a work around on this. If not I will drag out my X books. I think there is a script that is run on logout that can be used to kill nautilus. But what I think is happening is nautilus is being nohup'ed. Let me look around a bit and see if I can come up with something that is not so in-elegant as a kill -9 in a logout script.

---

### Post by ja4509 on 2007-12-13
As promised here is a crappy work around.

I searched high and low for a clean fix for this but it seems nobody has a clue and the problem/bug has been around for quite a few releases. Because most everybody seems to login and stay that way others don't experience this much.

The work around I suggest is simple at least but effective.

There is a PostSession directory with a path of:  "/etc/gdm/PostSession" and in this directory is a file named "Default". 

Do this:

    sudo nano /etc/gdm/PostSession/Default

Then near the bottom of the file right BEFORE the line "exit 0" put this line in the file.

    /usr/bin/killall -u $USER nautilus

Save the file and that should clean up after a session logout. It works for me.

---

### Post by bistros on 2007-12-13
I'd also take a look at cron tasks.  There are a lot of new things installed by default or installable - indexers, search tools etc. that may run under a user's UID even of they are logged out.

sudo /etc/init.d/gdm stop 

will stop gnome (and X) cold.  Nautilus is a lot more than a basic file manager - it handles a whole bunch of stuff like Finder in a Mac.  I expect the post-logout stuff may be search indexers or the like.

Just for interest's sake, if you are exporting people's homes and running like a 1980-90's server/workstation environment, did you think about using LTSP and just export the whole environment to an XDCMP/ RPL boot network session?  That way there is less client and more control.  It's got the benefits of local hardware (graphics/ usb peripherals etc.) and controlled server based desktops.

---

### Post by drdrewusaf on 2007-12-23
ja4509,

Thanks so much....works like a charm!



Drew

---

