---
title: "very slow remote GNOME X-Window displays"
date: 2006-07-08
forum: Desktop Environments
---

### Post by zimm0who0net on 2006-07-08
OK,  I'm having some trouble getting windows to popup on my desktop machine (running Windows/cygwin) from my Ubuntu Dapper machine.
When I ssh to the Ubuntu machine with the -X option, I get the windows on my local machine, but they render verrrry slowly.  Scrolling a gedit window is like pulling teeth.
So I tried bypassing the ssh tunnel and displaying directly by removing the DISPLAY variable and using the --display=<windowsIP>:0.0  (the machines are right next to one another)  That resulted in a very snappy gedit window (hooray!).  However, then I tried setting my DISPLAY variable (i.e. export DISPLAY=<windowsIP>:0.0 so I wouldn't have to always put --display=... on every line and I got a strange result.  Things like xterm and xeyes popped up quickly, but anyting GNOME related (file-roller, gedit, etc) took about 2 minutes to actually popup, but when they did popup, they were very snappy.  What is GDM doing that is different than other X applications?  Why is it that --display=<IP>:0.0 is somehow different than the environment variable?

Help!
  -Rich

---

