---
title: "Remote Desktope Sharing for networking noob++"
date: 2005-03-02
forum: Desktop Environments
---

### Post by bored2k on 2005-03-02
I have tried for over two hours (yes that is how much of a networking n00b i am) , and couldnt get Terminal Server Client to work.

1. I would like to connect to either a XP box or a box running Ubuntu . I cannot get any of them to work mainly because i dont know what to put in those boxes AND i dont know what to configure in the box im trying to connect to.

Can anyone help me on how to do a 
a. ubuntu <--> ubuntu connection or  maybe
b. ubuntu <--> xp ???


i would b very grateful  =P~

---

### Post by cwaldbieser on 2005-03-02
The ubuntu<->ubuntu connection can be accomplished in a number of ways.  The "Terminal Service Client" on the menu might not be the best client to use, though.  The only option there that will work is the VNC protocol, because there is no RDP server for Linux to the best of my knowledge.  Other simple vnc clients include tightvnc, and vncviewer.

When you log in to the graphical desktop, Ubuntu automatically starts a VNC server called vino.  You should be able to connect to it with vncviewer by doing something like:

```
$ vncviewer remote-computer-or-IP-address:1
```

(from the Remote Desktop Connection or Teminal Server Client, you should be able to just choose the VNC protocol and put in the hostname or IP address).

You can also connect directly via X.  There are a couple ways to do this, and I don't know how to do all of them off the top of my head.  I like to ssh into the remote machine like this:
```

$ ssh -Y -l username host-or-IP-address
```

This is a technique called "port forwarding".  All the X-windows display instructions on the remote host get forwarded back to your local X Display Server.  So while at that comman line you could execute:

```
$ nautilus
```

and you should get a file manager to pop up locally.

The Win XP <-> Ubuntu connection has more caveats.  VNC is still the simplest way to go, as you can install a VNC server  or client on Win XP with relative ease (just download tightvnc, realvnc,  or ultravnc and install).

In the terminal server case, Win XP is not a server, so you can't connect to it with terminal services / remote desktop (both of which use the RDP protocol), not even with another Windows box.  (I am not sure about XP pro, but I am pretty sure you can't with XP home).  Since there is no RDP server I know of for Linux, you can't remote desktop from XP to Ubuntu either.  You can RDP from Ubuntu to say Win2000 or Win2k3, and it is pretty simple (almost exactly like using Terminal Services or Remote Desktop on Windows).

The only other (graphical) way I know to connect from XP to Ubuntu is (surprise!) via X.  This is a trikier than Ubuntu-to-Ubuntu, becuase XP does not have an X Display Server installed by default.  There are docs on the web that tell you how to download and set up Cygwin to do this, though.  If you follow the instructions, you will run a script in Cygwin on your XP box called /usr/X11R6/bin/startxwin.sh that creates a rather unimpressive looking console window and causes an "X" icon to appear in your system tray.  However, if you use the same ssh trick I used in the Ubuntu<->Ubuntu example above, the file manager will open up on in your X Display Server running on XP.

---

### Post by bored2k on 2005-03-02
Thanks a lot ! I'll look into it tomorow when the part of my brain that actually thinks comes back from its rest time (4.40am).

Thnx thnx thnx  :-D  i hope it works!

---

### Post by danip on 2005-03-04
I use tight vnc to access another windows computer works great.  When I try to set my computer up so that the windows computer can access this one it doesnt work.  on the windows computer it gives me a ip address to connect to on the linbox it gives me something like Blackbetty:1 to connect to which i cant ever seem to connect to from the windows box.  any help?

---

### Post by dare2dreamer on 2005-03-04
For a linux-to-linux or windows-to-linux solution I highly recommend looking at freenx/nomachine. It's incredibly fast and very secure as it runs through ssh.

There are packages for freenx, the gpl'ed version, in the ubuntu backports, and you can download clients for almost every platform on [nomachine's homepage](http://www.nomachine.com)

---

### Post by cwaldbieser on 2005-03-04
[QUOTE=danip]I use tight vnc to access another windows computer works great.  When I try to set my computer up so that the windows computer can access this one it doesnt work.  on the windows computer it gives me a ip address to connect to on the linbox it gives me something like Blackbetty:1 to connect to which i cant ever seem to connect to from the windows box.  any help?[/QUOTE]

When you run the VNC server on Linux, and it says "server running on Blackbetty:1", that means that you need to connect to host Blackbetty on port 5901.  The :1 is the display number.  Some VNC clients let you specify the display, some ask for the port, some will accept either.  The post range for VNC usually starts at 5900 and goes up from there.  If your server has the built in web-VNC server, you should be able to http to it at port 5800 + display, or in this case:

[http://Blackbetty:5801](http://Blackbetty:5801)

Your VNC client might want you to enter the address like in a number of ways:
```
Blackbetty:1 # host:display
Blackbetty:5901 # host:port
Blackbetty::5901 # host::port
```

Most windows VNC servers I've seen actually start at display 0 or port 5900, so that "one-off" error might be giving you difficulty.

---

### Post by Magneto on 2005-04-28
dont know if you still are interested Bored2k but the other poster is wrong about connecting to XP

rdesktop is installed by default in Ubuntu and will allow you to connect to a windows terminal server or remote desktop session aka windows nt 4,2000,2003 server or XP/2000 workstation


run 
rdesktop 192.0.0.1

from the commandline - make sure you setup your XP system to accept remote sessions- right click my computer --choose Properties  ---hit the Remote tab and follow the instructions

not hard at all and safer than vnc

vnc is also a choice tool of people who use trojans - be very careful about installing vnc on win boxes

---

### Post by bored2k on 2005-04-28
[QUOTE=Magneto]dont know if you still are interested Bored2k but the other poster is wrong about connecting to XP

rdesktop is installed by default in Ubuntu and will allow you to connect to a windows terminal server or remote desktop session aka windows nt 4,2000,2003 server or XP/2000 workstation


run 
rdesktop 192.0.0.1

from the commandline - make sure you setup your XP system to accept remote sessions- right click my computer hit the Remote tab and follow the instructions

not hard at all and safer than vnc

vnc is also a choice tool of people who use trojans - be very careful about installing vnc on win boxes[/QUOTE]
 Thanks but It was for a friend of mine. Not really interested but thanks.

---

### Post by gotmonkey on 2005-05-27
[QUOTE=Magneto]dont know if you still are interested Bored2k but the other poster is wrong about connecting to XP

rdesktop is installed by default in Ubuntu and will allow you to connect to a windows terminal server or remote desktop session aka windows nt 4,2000,2003 server or XP/2000 workstation


run 
rdesktop 192.0.0.1

from the commandline - make sure you setup your XP system to accept remote sessions- right click my computer hit the Remote tab and follow the instructions

not hard at all and safer than vnc

vnc is also a choice tool of people who use trojans - be very careful about installing vnc on win boxes[/QUOTE]


Thanks for the post, It was exactly what I was looking for. I created a launcher on my desktop and it fires up nicely. I need to play with the switches, but all in all.. works great.

---

### Post by Magneto on 2005-05-30
[QUOTE=gotmonkey]Thanks for the post, It was exactly what I was looking for. I created a launcher on my desktop and it fires up nicely. I need to play with the switches, but all in all.. works great.[/QUOTE]
 glad I could help someone

---

