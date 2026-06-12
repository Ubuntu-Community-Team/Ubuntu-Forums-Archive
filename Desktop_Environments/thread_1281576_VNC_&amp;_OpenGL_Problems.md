---
title: "VNC &amp; OpenGL Problems"
date: 2009-10-03
forum: Desktop Environments
---

### Post by JohnnySage50307 on 2009-10-03
At present, I am running VNC4server and I am trying to remotely connect to it.  The methodology is as follows:

From my laptop (running Vista), I use PuTTY to ssh into my server.  Before connecting, I enable X11 forwarding.  Upon connection, I type
```
vncserver -geometry 1270x720
```and it returns
```
New 'JTH4-Ubuntu:1 (johnny)' desktop is JTH4-Ubuntu:1

Starting applications specified in /home/johnny/.vnc/xstartup
Log file is /home/johnny/.vnc/JTH4-Ubuntu:1.log
```I continue to open VNC Viewer 4 (provided by RealVNC) and log in using the password I specified.  It displays my desktop, however when I attempt to run a program that I wrote using OpenGL, terminal responds with the following error:
```
johnny@JTH4-Ubuntu:~$ Graphics/Assignment1
freeglut (Graphics/Assignment1): OpenGL GLX extention not supported by display ':1.0'
```A collegue of mine attempted to switch the monitor that it should display (he claimed that :1.0 should reference my server's physical monitor), however that did not affect anything.  I have tried other VNC clients and that also does not seem to help; infact, not-selecting X11 forwarding through PuTTY doesn't affect anything.

I am trying to get a VNC server/client working because there is someone I know who is interested in learning how to program OpenGL applications in Linux.  Because of this, I am not interested in setting up only a remote desktop (i.e. port 5900) as I do not want my potential student having access to my desktop.  My gut feeling is that it has more to do with the VNCserver program, rather than the clients.

On my server, I am running Ubuntu 9.04 (Jaunty) Desktop Edition.  Any assistance is highly appreciated!

---

### Post by JohnnySage50307 on 2009-10-03
After running a test, I have confirmed that is must be the VNCserver program.  I attempted to VNC physically from my server back into my server (yay recursion), and I have received the same errors.  So, does anyone know of a VNCserver program that *does* pass GLX?

---

### Post by andylinux on 2009-10-15
Take a look at,
[http://www.virtualgl.org/](http://www.virtualgl.org/)
and
tigervnc.

Thanks,
Andy

---

