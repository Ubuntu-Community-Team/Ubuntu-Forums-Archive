---
title: "Please help me to recover crashed Ubuntu.."
date: 2006-01-03
forum: Desktop Environments
---

### Post by guliver on 2006-01-03
System was ON several days. All I did is used **ethtool** to enable 100mbps and followed this topic in order to fix floppy drive issue [http://www.ubuntuforums.org/showthread.php?p=603640](http://www.ubuntuforums.org/showthread.php?p=603640)

After that I **can not** login no more to my PC as main user. 
I** can** login with other user accounts and everything working fine.

If I try to login with main user i got this ERROR message:

```
your session only lasted less than 10 seconds. If you have not logged out yourself, this could mean that there is some installation problem or that you may be out of disk space. Try looging in with one of failsafe sessions to see if you can fix the problem.

View details(~/xsession-errors file)

/Default: Registering your session with wtmp and utmp
/Default: running: /user/bin/X11/sessreg -a -w var/log/wtmp /u /var/log/utmp -x "/var/lib/gdm/ :0.Xservers" h "" -l ":0" "myusername"
/etc/gdm/xsession: Beginning session setup...
_IceTransTransNoListen: unable to find transport: tcp
_IceTransmkdir: ERROR euid != 0,directory /dev/x will not be created
_IceTransmkdir: ERROR can not create /dev/x
_IceTransPTSOpenServer: mkdir(/dev/X) failed, errno = 13
_IceTransOpen: transport open failed for pts/makinja:
_IceTransMakeALLCOTSServerListeners: failed to open listeners for pts
_IceTransPTSOpenServer: Protocol is not supported by ISC connection
_IceTransOpen: Transport open failed to isc/makinja:
_IceTransMakeALLCOTSServerListeners: failed to open listeners for isc
_IceTransSCOOpenServer: Protocol is not suported by SCO connection
_IceTransOpen: transport open failed for SCO/makinja:
_IceTransMakeALLCOTSServerListeners: failed to open listeners for sco

**(gnome-session:6692): WARNING **: Unable to read ICE authority file: /home/myusername/ .ICEauthority



```


Can anybody help me fix this problem?
(Im not sure if im hacked by somebody or...)

Disktool report that im using just 10% of disk space.

---

### Post by syklitengutt on 2006-01-03
try to start in failsafe gnome.
Had a similar problem and that worked for me.
Start in failsafe and log in!

---

### Post by angkor on 2006-01-03
```
**(gnome-session:6692): WARNING **: Unable to read ICE authority file: /home/myusername/ .ICEauthority
```

Go to console mode with Ctrl+Alt+F1 and log in.

Try moving the .ICEauthority file to another place:

```
mv .ICEauthority ICEauthority_backup
```

type Ctrl+Alt+F7 and try to log in.

Alternatively check the ownership on that file with 

```
ls -al .ICEauthority
```

In my case this reads:

```
 ls -al .ICEauthority
-rw-------  1 angkor angkor 16066 2006-01-03 11:45 .ICEauthority
```

It has to be set to your username. If it is not, you can change the ownership with:

```
chown yourusername.yourusername .ICEauthority
```

You should now be able to log in again.

---

### Post by steve.horsley on 2006-01-03
Correction. That should be a colon between user and group name:
> chown yourusername:yourusername .ICEauthority

I find it easier to just to delete the damn thing.

---

### Post by guliver on 2006-01-03
Hi,

I fixed with this:

```
Go to console mode with Ctrl+Alt+F1 and log in.

Try moving the .ICEauthority file to another place:


Code:

mv .ICEauthority ICEauthority_backup

type Ctrl+Alt+F7 and try to log in.
```

Now can you explane me what is that file for and why i got this problem? I want to know for future :)

---

### Post by ATAQ on 2006-01-03
When this happened me I logged in by

sudo chmod a+wr /home/user/.ICEauthority

but then I set the user by what angkor said.

---

