---
title: "tightvncserver 'almost' after uninst. of vino then this in rc.local"
date: 2009-04-22
forum: General Help
---

### Post by yvonn on 2009-04-22
Hi... loving 9.04 !!

PROBLEM: when I remote into to the machine with tightvncserver I get the X background and the X cursor though don't see anything else.

I need to remote into a friends PC to teach. 

Initially (with stock 8.10 and 9.04) I was able to use my tightvnc viewer from my machine (vncviewer -quality 0 -depth 8 xxx.xxx.xxx.xxx)  which worked fine, and have the remote machine serve me a full desktop via whatever runs on a stock ubuntu 8.10 (updated now to 9.04) 

So then I thought, OK I want to be able to have tightvncserver on there and also x11vnc. First I hoped to get tightvncserver working.

1) I installed tightvncserver on the remote machine while in a remote session via my vncviewer.

2) Then, I removed vino and also vinagre from the remote machine still in the remote session obviously.

3) Then I thought, ok, I need to put in a startup command 'cause if I remote the remote machine remotely I won't be able to login if tightvncserver isn't started. 

4) So, I found a thread here and it said to put this in rc.local
su -c user tightvncserver  
So, I did that.

5) I have a few things set right I think on the remote machine's gnome system > administration > login window though haven't done anything to the XDMCP so it's 'honor indirect requests' box is still checked. I allowed remote connections and obvious stuff.

6) So then I remotely rebooted the remote PC.

After the remote machine's reboot I can still login, though now I have to use:
vncviewer xxx.xxx.xxx.xxx:5901
or
vncviewer xxx.xxx.xxx.xxx:1

And I get the X grid background look and an X cursor and that's it. Can't do anything.

And, I now have to type in the tightVNC password and NOT the other password that's ubuntu's vino needed.
When I remotely login it does:

Enabling TightVNC protocol extensions
Performing standard VNC authentication
Password:

What I'm confused about is that I remember setting this password needed for tightvnc over a week ago. I'm wondering if there's couple of issues because I  uninstalled vino/vinagre and somehow everything messed up??

I only want tightvnc so that's why I uninstalled vino which gave me the full desktop sharing fine.

The router there has ports open for the IP address. 5900 5901.
I'm not yet trying any openssh at all.

REALLY would love to know anything here. Is there a different way to login. Like something after I type vncviewer other than just the IP address and port 5901 ???

Or, anyone know what the tweaks I need to have done the remote machine would be?

big thanks!

---

### Post by cboling on 2009-05-01
If I'm not mistaken, tightvncserver does not connect to a "real" already-running X display (client), but rather starts a new X session not connected to anything, much like RDP in MS Windows does.  I don't know how the package installs in Ubuntu by default.  Did you try right-clicking on the background?  You're either running a very basic window manager (in which case you'll get a menu) or no window manager at all, which is, yes, pretty useless.  You have to tell it to start a window manager when the X session starts.  I'm no expert on it, but there are lots of discussions on it on the Internet.

If you're looking to connect to your "real" X session like most people think of VNC as, you'll want to use x11vnc, It stays pretty current with all the features, and is very flexible.  Similar to how most VNC servers on MS Windows are, you can launch it as a user application, or you can connect it through your display manager with greater privliges to be able to survive outside of a login session.

I'm getting ready to move my new installation from Vino to x11vnc soon, hopefully day after tomorrow.

---

