---
title: "Gtk-WARNING **: cannot open display: :0.0"
date: 2005-10-24
forum: Desktop Environments
---

### Post by weezill on 2005-10-24
I've been getting the following error for the past week now, running Ubuntu 5.10.

Gtk-WARNING **: cannot open display: :0.0

I keep seeing (form googling) the same replies to this problem, where someone will suggest running "xhost +", or that it's a problem when ssh'ing into a remote server and exporting the display.  I'm not ssh'ing into anything, and when I run the xhost command as a regular user or sudo, I get the "cannot open display" problem again.

The weird thing is, this happens after a while, as if I reboot, I'll be good for hours.

I'm not new to linux, but new to Gnome and X.  I'm not really sure where to start with this.

Any help would be appreciated.

Cheers.

---

### Post by mirkov on 2005-10-30
I am having pretty much the same problem. My setup is dual head nvidia card with 2 X servers on ubuntu 5.10, and it was working perfectly until I went to System -> Administration -> Login Screen Setup, tab XServer and pressed "Remove Server" button before actually reading what the caption is :( ... A digression: in that screen, there is a warning in bold, that says what it says, but a button that basically messes something up should have a confirmation dialog afterwards...
Anyhow, since that incident ;) I am unable to start apps from one server in the other X server. An example is the script for playing dvds in xine on the other monitor.

```
#! /bin/bash

DISPLAY=":0.1"
xine -pv -f dvd:/

```

which reports error 'Cannot open dislplay'. 

Both servers are running fine. 

I just discovered a funny thing: if I replace value of DISPLAY environment variable with :1.0 or :1.1, it is working fine. 

```
mirko@ubuntu:~$ DISPLAY=:0.0
mirko@ubuntu:~$ xhost
xhost:  unable to open display ":0.0"
mirko@ubuntu:~$ DISPLAY=:1.0
mirko@ubuntu:~$ xhost
access control enabled, only authorized clients can connect
INET:localhost.localdomain

```

As it seems, the Remove Server and the later Add Server in that dialog bumped the more significant number. Any idea how to restore the previous state?

---

### Post by mirkov on 2005-10-30
I am a bit thick sometimes ;). OK, in that dialog (Login Screen Setup, XServers tab) there is a number in front of each entry (column VT, virtual terminal?). The number corresponds to the more significant number in DISPLAY environment variable (```
:x.0
```). Changing the number in the dialog back to 0 restored function to my scripts for starting apps on the other x server. 

I also saw that my problem is not all that similar to Yours. Anyway, I wish You luck with Yours.

---

### Post by japurcell on 2006-08-15
so in DISPLAY=:0.1, 0 is the server and 1 is the display?  If I'm only running server 0 and I want to run vmware server on display 1, should the script be "DISPLAY=0:1 vmware"?  Also, will that switch to Display 1 or will I have to manually switch there after running?  Last question is, which VT corresponds to which display?  I know 0 is VT7 or ctrl-shift-7, but what are the rest?

---

