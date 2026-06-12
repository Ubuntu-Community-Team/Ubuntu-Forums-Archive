---
title: "Login error....."
date: 2005-11-20
forum: Desktop Environments
---

### Post by ringding on 2005-11-20
Here is something I've never seen before.......

Recent install of Breezy on a Dell XPS Gen 2 laptop.

Upon initial install everything went GREAT...detected 99% of my system.
Used it for about 3-4 days......rebooted several times.

BUT this time I got and error logging in from the graphical login (below):

*"Your session only lasted less than 10 seconds. if you have not logged out yourself, this could mean that there is an installation problem or that you may be out of disk space. Try logging in with one of the failsafe sessions to see if you can fix the problem."*

I have plenty of disk space...  17 gig partition!
Tried to login via the failsafes but I get same error.

I can login through failsafe terminal though....

I should also mention that this is a dual boot sys with XP.
Partitions for linux are:
/boot 100meg 
/swap 2gig
/    fill space  15 gig or so

ANY THOUGHTS????

---

### Post by taurus on 2005-11-20
What is the output of this command?

df -h

---

### Post by ringding on 2005-11-20
Here ys go:

```
Filesystem          size   Used  Avail  Use%  Mounted on
/dev/sda4          14g    3.2g  9.9g   25%    /
tmpfs                507m     0   507m   0%    /dev/shm
tmpfs                507m  13m  494m   3%    /lib/modules/2.6.12-9-386/volitile
/dev/sta2            89m  12m   73m   14%   /boot
/dev/sda1           41g   14g   27g     34%  /media/sda1
```

This is a fresh install of win xp and Ubuntu.....

Here are the errors from the .xsession-error file:

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/X11/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "rich"
/etc/gdm/Xsession: Beginning session setup...
_IceTransTransNoListen: unable to find transport: tcp
_IceTransmkdir: ERROR: euid != 0,directory /dev/X will not be created.
_IceTransmkdir: ERROR: Cannot create /dev/X
_IceTransPTSOpenServer: mkdir(/dev/X) failed, errno = 13
_IceTransOpen: transport open failed for pts/xander:
_IceTransMakeAllCOTSServerListeners: failed to open listener for pts
_IceTransISCOpenServer: Protocol is not supported by a ISC connection
_IceTransOpen: transport open failed for isc/xander:
_IceTransMakeAllCOTSServerListeners: failed to open listener for isc
_IceTransSCOOpenServer: Protocol is not supported by a SCO connection
_IceTransOpen: transport open failed for sco/xander:
_IceTransMakeAllCOTSServerListeners: failed to open listener for sco

** (gnome-session:8430): WARNING **: Unable to read ICE authority file: /home/rich/.ICEauthority

---

### Post by ringding on 2005-11-20
Found the solution HERE   [http://www.ubuntuforums.org/showthread.php?t=80599&highlight=session+lasted](http://www.ubuntuforums.org/showthread.php?t=80599&highlight=session+lasted)

You need to change the permissions of the .ICEauthority file.......for some reason it seams that k3b might be the culprit....


```
sudo chown (username) .ICEauthority
```

---

### Post by guyomarj on 2005-11-22
[QUOTE=ringding]sudo chown (username) .ICEauthority[/QUOTE]

I'll give it a try. I had the same problem last night, trying to get Gnome Enlightened to work...

Did you have anymore troubles regarding the "you've got 10 seconds and then, Ubuntu will self-destroy" ringding?

---

### Post by ringding on 2005-11-22
[QUOTE=guyomarj]I'll give it a try. I had the same problem last night, trying to get Gnome Enlightened to work...

Did you have anymore troubles regarding the "you've got 10 seconds and then, Ubuntu will self-destroy" ringding?[/QUOTE]

Not yet.   but I have not run k3b since either!!!

---

### Post by guyomarj on 2005-11-22
It did the trick. I've been able to get back to an "Unenlightened Gnome".

I also did a
```
 sudo chown (user) .Xauthority 
```
Because it was "rooted" as the .ICEauthority. Is that ok?

---

### Post by ringding on 2005-11-23
not sure what you mean by "rooted" but if the "(user)" was changed to you then your OK!

---

