---
title: "Weird things keep sucking up all my resources"
date: 2006-11-12
forum: Desktop Environments
---

### Post by Karbonik on 2006-11-12
Really, I'm starting to get frustrated - I can't seem to figure out what is causing me so many problems, and I'm not sure even what to specify for help in...

All I know is that something is not configured right, and different apps seem to be draining my resources, but I can't find the consistency.

sometimes it's amaroK.  sometimes it's KPilot.  sometimes it's Gaim. one thing seemed to be a radio toolbar in Firefox (actually got up to a gig and a half of RAM usage with that one) ... sometimes it's I don't know what.

I installed gPS Process list to try and figure it out...

Right now I've got 512 physical RAM (495 listed available) 200 of which is being used and Swap is at 537 out of a possible 4 Gigs (Yeah, I know, a bit overkill, but I'm planning on upgading to 2Gig physical RAM)

The only visble processes running, from looking at the KDE bar show gPS, one instance of Konqueror (Filesystem, not internet) and one instance of Firefox with 8 tabs open.

If I can look at my cron jobs as per this thread here: [http://ubuntuforums.org/showthread.php?t=68615&highlight=resources](http://ubuntuforums.org/showthread.php?t=68615&highlight=resources)
I'm not even quite sure what I need to be running things the way I want or not.

gPS shows the main draw on memory to be Xorg, with a Size of 1073 MB, using 180 MB of physical.  Is that normal?

Please help!

---

### Post by kidders on 2006-11-12
Are you noticing any side-effects of the resource usage?

When reading memory allocation stats, you should bear in mind that having low amounts of available RAM can be quite normal ... even desirable. In fact, Linux's tendancy *not* to be in any hurry to deallocate memory is considered a _feature_ of its default memory management policy.

Additionally, the fact that some of your swap appears allocated doesn't necessarily mean it is actually in active use at that very moment. It often merely indicates that, at some point, it was ... and the kernel simply hasn't had a good reason to free it yet. The fact that *any* swap is being used at all though does suggest that you might need more RAM though -- but you're planning on that anyway :-)

Is that any help?

**Edit:**
I thought you might be interested in some stats from my PC for comparison. I took this snapshot after my computer was at rest for quite some time (as you can see from the load average stats!) Xfce, amarok and firefox are running.

```
top - 21:33:44 up 4 days,  5:55,  4 users,  load average: 0.00, 0.00, 0.00
Tasks: 100 total,   1 running,  98 sleeping,   0 stopped,   1 zombie
Cpu(s):  0.5%us,  0.0%sy,  0.0%ni, 99.5%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   1035080k total,  1017700k used,    17380k free,   359324k buffers
Swap:   522104k total,    12604k used,   509500k free,   359932k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
12629 kidders   15   0  155m  56m  24m S  0.0  5.6   0:47.34 firefox-bin
 8880 kidders   15   0  113m  37m  24m S  0.0  3.7   4:40.74 amarokapp
 4165 root      15   0  188m  36m 9448 S  0.0  3.6   1:46.46 Xorg
 8837 kidders   15   0 53988  18m  12m S  0.0  1.8   0:03.77 xfce4-terminal
14957 kidders   15   0 35360  16m  12m S  0.0  1.6   0:00.76 knotify
 8826 kidders   15   0 43000  15m  12m S  0.0  1.6   0:01.75 xfce4-menu-plug
 8809 kidders   15   0 52480  15m  12m S  0.0  1.5   0:00.71 xfdesktop
 8819 kidders   15   0 41332  14m  11m S  0.0  1.4   0:01.78 xfce4-panel
 8799 kidders   15   0 27084  12m  10m S  0.0  1.3   0:01.60 xfwm4
 8875 kidders   15   0 28244  11m 9064 S  0.0  1.1   0:00.60 kded
 8827 kidders   15   0 22780  10m 9444 S  0.0  1.1   0:00.33 xfce4-mount-plu

...
...

```

As you can see, only 17 megs of an available 1GB RAM are free, and at some point, about 12MB of swap was needed, to supplement my RAM ... probably while doing something complicated with graphics. Between them, firefox, amarok and the xorg parent process appear to be using almost half a gig of RAM, but if I were to give the kernel a reason to re-think those numbers (eg by opening openoffice), that could change.

---

### Post by dahlek on 2006-11-13
I have the same problem. Everything freezes for a few seconds and then comes back. This error sometimes comes up:

Sound server fatal error:
cpu overload, aborting

The window title of that little error box is this: Error - artsmessage

Which is strange, because the first thing I do when I install a KDE distro is turn that piece of crap ARTS off.

The last time I got this error was, believe it or not, while trying to play kolf, that little tiny KDE mini-putt golf game. That error came up just after I made my first putt, in other words, right when a sound should have been generated.

Perhaps the issue is that turning off the KDE sound system in the control center doesn't REALLY turn it off?

I upgraded my setup from 6.06.1 LTS I think it was. I've had Ubuntu just a few days before I upgraded, lol, and I think I should have stuck with the older version.

I also seem to get logged off automatically for some reason. I thought my power went off last night for a moment when I came to the PC to find the login screen instead of the screensaver...Earlier this evening, I went to eat dinner and came back and was logged out as well...

This version sure seems to have a lot of ghosts. I read that the upgrade can be problematic, I'm considering just scrapping the whole thing and starting from scratch...

---

### Post by abbeychase on 2006-11-13
what does 
```

free -m

```
output?

---

### Post by Karbonik on 2006-11-13
Thanks kidders, 

here's what I get right now:


top - 21:08:34 up  5:25,  1 user,  load average: 0.79, 0.66, 0.59
Tasks: 112 total,   1 running, 111 sleeping,   0 stopped,   0 zombie
Cpu(s):  6.6% us,  0.3% sy,  0.0% ni, 92.4% id,  0.0% wa,  0.0% hi,  0.7% si
Mem:    506800k total,   496140k used,    10660k free,     9532k buffers
Swap:  4096532k total,   122448k used,  3974084k free,   175168k cached

6943 root      15   0  677m 129m 5040 S  4.7 26.1  15:26.28 Xorg
 7672 karbonik  15   0  177m  66m  23m S  1.3 13.4   3:46.26 firefox-bin
 7075 karbonik  15   0 33532  16m  12m S  0.3  3.4   0:39.12 kicker
12614 karbonik  15   0 64024  17m  11m S  0.3  3.4   0:03.88 beep-media-play
12789 karbonik  16   0 32384  15m  11m R  0.3  3.2   0:01.13 konsole
    1 root      16   0  1564  472  444 S  0.0  0.1   0:01.59 init


The Xorg still looks pretty huge compared to yours.  I'm not sure if it's something I did.  With this distro I went thru a bit to install beryl, and then realized that it kills me with only 512M RAM, so I took it out, but I think it also removed some other packages which I don't recall at the moment, and since then OpenGL hasn't worked.  

I'm having this nagging feeling that if I get OpenGL working (ie: the correct drivers) then there will be less load because it will be more appropriately allocated.  Am I way off base with that?

---

### Post by Karbonik on 2006-11-14
Ok, so it wasn't the drivers that were preventing me from doing OpenGL - apparently I somehow removed the libraries, duh.  So that's back up and working, and it seemed to make a slight difference.

I also upgraded to 1.5 Gig RAM, and now It's running fairly smoothly at about 483MB used, 0 Swap, with Firefox@8 tabs, Thunderbird, amaroK, Kontact, and a few other incidentals.

I realized that the reason that the xorg was using up twice what kidders's report was is probably because I'm using 2 monitors (duh).  However, I still experience a slight lag with video sometimes, when switching desktops and such.  

This brings up another question, which I posted about a week ago [http://ubuntuforums.org/showthread.php?t=291585](http://ubuntuforums.org/showthread.php?t=291585)

I haven't installed this driver yet, and I'm wondering if that's closer to the root of this particular problem - in that I'm using the i810 driver instead of the Embedded Graphics Driver?

---

### Post by kidders on 2006-11-14
Glad to hear you solved your OpenGL problem. I'm afraid I don't have anything useful to add to your other thread :-( though.

By the way, the other thing that'll make my xorg footprint smaller than yours is that it's using a very lightweight config. But, now that you've upgraded to 1.5G, your X should be happy as a pig in muck!

---

