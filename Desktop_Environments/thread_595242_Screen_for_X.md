---
title: "Screen for X"
date: 2007-10-28
forum: Desktop Environments
---

### Post by beerfan on 2007-10-28
I would like to find a way to move a running X program from one display to another. For example, with ssh -X I can run a remote X program but I would like to be able to connect to an already running remote program or move it to my local display.

Is there anything like screen for X or some feature of X which allows moving a program to another display?

---

### Post by scorp123 on 2007-10-28
> **beerfan said:**
> I would like to find a way to move a running X program from one display to another. For example, with ssh -X I can run a remote X program but I would like to be able to connect to an already running remote program or move it to my local display.

Is there anything like screen for X or some feature of X which allows moving a program to another display? Look into VNC ... that's where the people who wrote the "screen" utility got their idea from if I am not mistaken. Basically you'd be running a virtual X11 desktop (I personally prefer NOT to run GNOME on that virtual instance but rather a smaller window manager without too much eye-candy such as "fluxbox") and you can connect to it using e.g. the "tsclient" program, run programs inside of that virtual desktop, leave them running while you are disconnected, and so on.

There is also "vino". That's the program you'd activate via this menu: System => Preferences => Remote Desktop.

"vino" too uses the VNC protocol but instead of starting an additional virtual X desktop it exports your current desktop session to the network. You can set a password (in VNC too) so no unauthorised users can connect.

Hope this helped?

---

### Post by beerfan on 2007-10-28
I'm well aware of remote desktop solutions. That isn't what I'm asking for though.

---

### Post by scorp123 on 2007-10-29
> **beerfan said:**
> I'm well aware of remote desktop solutions. That isn't what I'm asking for though. Due to the client-server nature of the X11 protocol I don't think it's possible to move an already running application. When you'd try to move the program the connection between client (= the program) and the X11 server would be interrupted and thus the program would crash and die .... and poooof!! it's gone. So the remote desktop solutions I mentioned in the previous post are probably as close as you can get to what you asked. That's the reason why e.g. VNC was invented so you don't have to move the program's graphical output in the first place ... you leave it running inside the VNC server instance and connect to it whenever you need to; and a disconnect won't kill the program as it would if you get disconnected from a SSH session.

There are commercial solutions such as SUN's "Global Secure Desktop" (SSGD) which is partially based on the VNC technology. With SSGD you can export single program windows (instead of the whole desktop) in a VNC-like fashion and reconnect again whenever you need to. Disconnecting will also leave your programs running. When you reconnect all your open program windows will instantly show up again. But this stuff isn't free and it relies heavily on Java (for facilitating the communication between you and the server). If that isn't a problem, then give SSGD a try.

[http://www.sun.com/software/products/sgd/index.jsp](http://www.sun.com/software/products/sgd/index.jsp)
[https://sgddemo.sun.com/](https://sgddemo.sun.com/)

---

### Post by beerfan on 2007-10-29
Thanks for the informative response. That's the answer that I feared but I hold out hope that some X wizard will come along with a little known solution.

I don't like VNC or other Linux remote desktop solutions because they leave the host screen completely open and visible to anyone standing in front of the machine. What other way is there to access a running GUI program though?

---

### Post by scorp123 on 2007-10-30
> **beerfan said:**
>  I don't like VNC or other Linux remote desktop solutions because they leave the host screen completely open and visible to anyone standing in front of the machine.  Not true if you use a virtual server (e.g. on screen **:1**) instead of exporting your real desktop (screen **:0**). If you have that than anyone standing in front of the machine sees nothing but the login dialogue asking for a valid username and password.

---

### Post by bingoUV on 2007-10-30
beerfan,
   You seem to be interested in security, so either tunnel vnc over SSH, or use NX (I have described NX in another thread [http://ubuntuforums.org/showthread.php?t=592973](http://ubuntuforums.org/showthread.php?t=592973)).

thanks

---

### Post by timcredible on 2007-10-30
the easiest method of doing remote access of desktops/applications is by using XDM, which doesn't show anything on the local screen.  For a how-to on setting it up, please see [http://linux--help.org/joomla2/index.php?option=com_content&task=view&id=12&Itemid=1](http://linux--help.org/joomla2/index.php?option=com_content&task=view&id=12&Itemid=1)

---

### Post by scorp123 on 2007-10-30
> **bingoUV said:**
> beerfan,
   You seem to be interested in security, so either tunnel vnc over SSH, or use NX (I have described NX in another thread [http://ubuntuforums.org/showthread.php?t=592973](http://ubuntuforums.org/showthread.php?t=592973)). yeah, NX is nice too and very fast. Way faster than VNC.

---

### Post by scorp123 on 2007-10-30
> **timcredible said:**
> the easiest method of doing remote access of desktops/applications is by using XDM  But a disconnect will kill your session. I'd rather go the NX route or VNC-over-SSH tunnel.

---

