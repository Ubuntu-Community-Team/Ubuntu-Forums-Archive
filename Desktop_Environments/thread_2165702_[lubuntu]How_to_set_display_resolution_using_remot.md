---
title: "[lubuntu]How to set display resolution using remote access, but no physical monitor"
date: 2013-08-05
forum: Desktop Environments
---

### Post by elpidiovaldez5 on 2013-08-05
I am connecting to a Lubuntu box using Teamviewer8.  It all works fine when my monitor is connected, but when it is disconnected it drops to low resolution.  I found monitor settings, but this does not offfer a higher resolution.  How can I set this up ?
I did some googling and found two possible approaches - an xrandr command in autostart file or a configuration file for x11.  I tried adding an xrandr command to the lxsession autostart file.  It did not work, but I probably got the xrandr command wrong anyhow.  Also not sure I was editing the right autostart file.  I did not have the same files as the original poster of the idea. I am new to Lubuntu and this is beyond my experience.

---

### Post by elpidiovaldez5 on 2013-08-14
Well nobody replied, so I guess that means nobody knows how to do this.  I have found a very inadequate solution.  If I establish the Teambuilder8 connection to my system while it has a monitor connected, then I can disconnect the monitor and the resolution of the display on the remote machine is maintained. I really do NOT want to have to keep connecting a monitor each time I reboot the machine.

I found another solution that is inadequate for me, but may work for some people.  I installed tigervnc on my headless machine and remote machine.  I start a vnc service on the headless server with:
vncserver -geomety 1920x1080

I ask X windows to re-route my display data:
export DISPLAY=1.0

I start the the tigervnc viewer on the remote machine and connect to the screen running my program:
vncviewer 

Now the key to all this working is that tigervnc allows one to specify the screen geometry.  Were Teamviewer to do the same my problems would be solved.  Tigerviewer is much slower than Teamviewer and really not adequate for desktops containing video.

I would still really appreciate somebody telling me how to set the resolution when a monitor is not attached (in a way that would work for Teamviewer8).  I feel that it is a major design error to assume that a computer has a monitor attached, and cannot believe that linux is incapable of running as a headless server.

---

