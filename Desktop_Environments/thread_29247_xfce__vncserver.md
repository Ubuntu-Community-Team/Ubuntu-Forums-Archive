---
title: "xfce / vncserver"
date: 2005-04-23
forum: Desktop Environments
---

### Post by ubuntu_demon on 2005-04-23
I've just installed ubuntu at the pc of friend of mine.

I can't get vncserver to work. I've done a "server" install. 

when I type in vncserver there don't appear any errors. But when I look for the process using : ps aux | grep vnc ... nothing shows up. When I start vncserver again he complains that he might run already (but really doesn't run)

```

Warning: killerchild:1 is not taken because of /tmp/.X1-lock
Remove this file if there is no X server killerchild:1

```

the vncserver logs that it puts in the homedir look also good :

```

23/04/05 19:18:32 Xvnc version 3.3.7 - built Oct 28 2004 23:57:28
23/04/05 19:18:32 Copyright (C) 2002-2003 RealVNC Ltd.
23/04/05 19:18:32 Copyright (C) 1994-2000 AT&T Laboratories Cambridge.
23/04/05 19:18:32 All Rights Reserved.
23/04/05 19:18:32 See http://www.realvnc.com for information on VNC
23/04/05 19:18:32 Desktop name 'X' (killerchild:1)
23/04/05 19:18:32 Protocol version supported 3.3
23/04/05 19:18:32 Listening for VNC connections on TCP port 5901

```

I tried putting startxfce4 in .xession

I also tried putting the follwing xstartup file in the .vnc dir :

```

#!/bin/bash
/usr/bin/startxfce4

```

and I've also replaced startxfce4 line by :
```

/usr/X11R6/bin/startx

```




these are the packages that I installed :

```

amule
debfoster
deborphan
firestarter
gaim
gparted
grub
isag
iso-codes
linux-386
linux-686
mozilla-firefox
nmap
samba
smbfs
ssh
ubuntu-base
vncserver
x-window-system
xfce4
xfce4-goodies
xserver-xorg

```

I really feel like a n00b now. But I really don't understand this at all. :-P

thnx guys!

---

