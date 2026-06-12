---
title: "vnc4server installation problem"
date: 2008-03-18
forum: Desktop Environments
---

### Post by ccclay on 2008-03-18
I follow the steps with this thread 
[http://ubuntuforums.org/showthread.php?t=122402](http://ubuntuforums.org/showthread.php?t=122402) ( HOWTO: Set up VNC server with resumable sessions )

For the first step, it requires me to enable XDMCP
System->Administration->Login Screen Setup
Tab Security->Enable XDMCP
Tab XDMCP--> You can disable "Honor Indirect Requests"

I am using ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016), however, there is no choice of Enable XDMCP in Tab Security, so I do nothing with this step.

For the last step, its Instruction : To test that this is working first try to connect from the same machine (the machine we just set up the VNC server on): code vncviewer localhost:1 . You should be prompted for the VNC password, and then see the GDM login screen where you can login and start a new X session. If that works, you can now go ahead and try to connect from remote machine using your favorite VNC client (remember to first close the local vncviewer we started above).

Following the instruction, I type in the terminal : vncviewer localhost:1

this is what I got :

> @:~$ vncviewer localhost:1
VNC Viewer Free Edition 4.1.1 for X - built Sep 10 2007 17:17:04
Copyright (C) 2002-2005 RealVNC Ltd.
See [http://www.realvnc.com](http://www.realvnc.com) for information on VNC.

Tue Mar 18 11:23:23 2008
CConn:       connected to host localhost port 5901
main:        read: Connection reset by peer (104)
@:~$

Here I have questions :
What is the meaning of CConn: connected to host localhost port 5901 ?
What is the meaning of  main: read: Connection reset by peer (104) ?
According to the instruction it should ask me for password, however, it doesnt ask me for password, and there is no login screen, it just simply goes back to prompt. 

So is it a correct installation ? And now how I have to do ?

---

### Post by Shark4126 on 2008-03-26
I'm having the same problem with the same version of Ubuntu.  Only the XDMCP settings are under the Remote tab... and defaults are fine.  No one out there seems to be answering this particular problem.  I've been searching for hours.

---

