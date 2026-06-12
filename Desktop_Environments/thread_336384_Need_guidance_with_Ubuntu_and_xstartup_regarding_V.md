---
title: "Need guidance with Ubuntu and xstartup regarding VNC"
date: 2007-01-11
forum: Desktop Environments
---

### Post by kdnewton on 2007-01-11
Hi all.

I'm looking to install vncserver from the command line (I'm at school right now trying to set up vnc on my home computer).

Here's what I can do: I've run "sudo apt-get install vncserver" and run "vncserver :1"

I, through the computers WinXP connected to my home address:1 through realVNC and it's connecting to it. The screen I'm greeted with is the traditional VNC session with the Ubuntu startup screen, but nothing happening with the Ubuntu startup screen.

I then wrote an xstartup and placed it in ~/.vnc/xstartup (is it required that I change the permissions? chmod 777 even didn't work later)

After that I modified /etc/vnc.conf and changed the /etc/X11/Xsession path to $vncUserDir/xstartup

and killed the vncserver -kill :1

then ran vncserver :1 again and checked the log. It's telling me it ran the xstartup fine (with 777 permissions) but it's complaining about permissions for another file in /etc/...



So! My question. What is the best solution for this? I suppose I could follow the tutorial on the forums for setting up a remote desktop ...when I finally physically get back in front of that computer. But I'm looking for an easy command line solution. Thank you.

I'll even be happy with telling my xstartup (which didn't exist before I wrote it, but it seems tutorials for other distros assume it already exists) to start with startx and one xterm.

---

