---
title: "vnc4server"
date: 2006-07-17
forum: Desktop Environments
---

### Post by jrleighton on 2006-07-17
I have followed about 3 vnc4server forum posts for getting vnc up and running on ubuntu (I don't really mind which vnc server, I just want one that works).

I have vnc4server working at the moment, in the sense that I can connect to it. But all I can see is a grey cross-hatched screen with an "X" cursor.  

Does this sound familiar to anyone who might have been through some pain before ?   I'd really appreciate a little help from someone in the know.

Failing any specifics on my vnc4server issue, I'd be glad to hear from anyone who's got a vnc server running on ubuntu (I'm on dapper)

Thanks for the help

---

### Post by schoo on 2006-07-21
I have the similar problem too... and still figuring out why...

---

### Post by jrleighton on 2006-07-21
I gave up with vnc4server. I use x11vnc, it's fine.

---

### Post by dodob on 2006-07-31
The reason for the cross-hatched screen and X cursor:

vnc4server starts ~/.vnc/xstartup, which in turn calls twm. twm isn't installed by default on Ubuntu.

Furthermore, if you uncomment the two lines in xstartup, X will start with nothing but a cross-hatch and an X cursor, because /etc/X11/xinit/xinitrc is not executable.

(Note: if you uncomment the two lines, you don't need to uncomment the rest of the file, because "exec" replaces the currently running shell, voiding the rest of the script. I might be wrong about this ;) Someone please correct me if I'm wrong.)

These are some of the possible solutions/workarounds I found:
[INDENT]
**Option A:** Install twm.

**Option B:** Comment out "twm &" and instead start "gnome-session &" or your preferred window manager/desktop manager. (Not recommended?)
```
#twm &
gnome-session &
```
**Option C:** Do as the xstartup file says and comment out the two lines that say "unset SESSION_MANAGER" and "exec /etc/X11/xinit/xinitrc"
[/INDENT]
Option A gives you a very lightweight window manager that might be more responsive over VNC than Gnome or some other full-fledged desktop manager.

Option B works, but I kept getting a Power Manager error window upon X login, saying the the dbus server must be turned on. This is a problem because it would sometimes leave me with dirty processes after gnome logout and vncserver kill.

Option C should start your preferred desktop manager, just as if you were sitting at the computer (Gnome for Ubuntu, KDE for Kubuntu, etc.) At least, that's what I think. As such, it should prevent processes from not starting correctly like in Option B.

And now we're back to the topic in question! Option C does not work straight away. X starts with a cross-hatch pattern and an X cursor and nothing else. This is because xstartup attempts to exec /etc/X11/xinit/xinitrc, which is non-executable. This appears to be some sort of Debian "way of doing things" where executables are kept out of /etc. Refer to: [http://lists.debian.org/debian-x/2003/12/msg00412.html](http://lists.debian.org/debian-x/2003/12/msg00412.html)

(I'm now at a loss. I'm new to Linux and I don't know if I should chmod 755 /etc/X11/xinit/xinitrc for the fear that I might compromise the system's security. FWIW, Fedora Core has 755 on xinitrc.)

/etc/X11/xinit/xinitrc then sources /etc/X11/Xsession, which loads your X settings and starts your preferred manager.


*** ADDENDUM:

As an interesting aside, I initially installed the package vncserver (as opposed to vnc4server).

For clarification, vncserver is version 3.3.7 and vnc4server is version 4.1 of RealVNC ([www.realvnc.com](www.realvnc.com)) The package description for vncserver says: "Note2: A new version of vnc and is available in the vnc4server package. This package exist because of backward compatibility." ([http://packages.ubuntu.com/dapper/x11/vncserver](http://packages.ubuntu.com/dapper/x11/vncserver))

vncserver (3.3.7) works without resorting to A, B, or C. This is because it doesn't look at ~.vnc/xstartup. It calls /etc/X11/Xsession directly :)

However, there's a bug (?) in 3.3.7 where the -localhost switch will block everything, including localhost connections. This makes it useless if you're trying to restrict access to SSH tunneling.

Hope this helps someone, even if there isn't an optimal solution (I'm still looking for one myself).

---

### Post by schoo on 2006-07-31
x11vnc worked well for me... no more fuss with other vnc servers.

---

### Post by HunterPro on 2006-07-31
why don't you stick to the 'remote desktop' function Ubuntu offers? It's easy, it's VNC, and it works out-of-the-box. And you can just take over your running desktop instead of creating a seperate X session.

---

### Post by schoo on 2006-07-31
i use x11vnc because i can change the listening port number ;) and they have additional features where the default "remote desktop" doesn't have.

---

### Post by dodob on 2006-07-31
I'm definitely going to try x11vnc and FreeNX, if only for comparison's sake. I just wanted to get regular VNC running over SSH, which I assumed was a wee bit easier than it turned out to be.

Gnome's Remote Desktop did work for me right away, out of the box, but I can't remember what I didn't like about it that made had me looking at VNC. SSH tunneling perhaps?

Most of the time I'll be connecting to my Ubuntu machine remotely through SSH, operating from a terminal, firing up the GUI only occasionally. I think that's a valid reason not to use Gnome's Remote Desktop.

---

### Post by EnthropyinAction on 2007-08-27
> **HunterPro said:**
> why don't you stick to the 'remote desktop' function Ubuntu offers? It's easy, it's VNC, and it works out-of-the-box. And you can just take over your running desktop instead of creating a seperate X session.

The included remote desktop function uses Vino.  Some people experience problems where the remote screen won't refresh.

---

