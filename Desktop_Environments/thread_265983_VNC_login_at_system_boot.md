---
title: "VNC login at system boot"
date: 2006-09-26
forum: Desktop Environments
---

### Post by discombobulation on 2006-09-26
Is there a way to login to the system via VNC as soon as the system boots?

Right now, if I reboot my Ubuntu 6.06 system remotely, I can't login via VNC until after I've done a local login.

Is there some process I can start at boot-time to allow this?  Is there some VNC option I should set?

Please advise.

Thanks!

---

### Post by James79 on 2006-09-26
Yes! This was difficult for me to figure out, as there seems to be several ways of accomplishing it but here's the method I used (I wanted the same thing as you) and it worked beautifully for me:

Use apt-get to install tightvncserver and x11vnc

You need to create a "vnc password file", which will contain the VNC login. I placed mine in /root:
vncpasswd /root/.vncpasswd

Then, add the following line at the very end of /etc/X11/gdm/Init/Default :
/usr/local/bin/x11vnc -rfbauth /root/.vncpasswd -o /var/log/x11vnc.log -forever -bg

Finally, edit the file /etc/X11/gdm/gdm.conf. Find the parameter called KillInitClients, and set it to FALSE. If you do not, your VNC session will get disconnected after you've logged in.

That worked for me !

---

### Post by lamego on 2006-09-26
I am not sure the following howto applies to Dapper:
[http://ubuntuforums.org/showthread.php?t=122402](http://ubuntuforums.org/showthread.php?t=122402)

---

### Post by James79 on 2006-09-26
Oops... I should to mention... you should probably *disable* the vnc server that comes installed with gnome if you have enabled it, to prevent any conflict.

System->Preferences->Remote Desktop

---

### Post by discombobulation on 2006-09-27
> **lamego said:**
> I am not sure the following howto applies to Dapper:
[http://ubuntuforums.org/showthread.php?t=122402](http://ubuntuforums.org/showthread.php?t=122402)

Interesting page, but I whenever I connected all I got was a blank X session.  Not sure what was going on there.

---

### Post by discombobulation on 2006-09-27
> **James79 said:**
> Yes! This was difficult for me to figure out, as there seems to be several ways of accomplishing it but here's the method I used (I wanted the same thing as you) and it worked beautifully for me:

Use apt-get to install tightvncserver and x11vnc

You need to create a "vnc password file", which will contain the VNC login. I placed mine in /root:
vncpasswd /root/.vncpasswd

Then, add the following line at the very end of /etc/X11/gdm/Init/Default :
/usr/local/bin/x11vnc -rfbauth /root/.vncpasswd -o /var/log/x11vnc.log -forever -bg

Finally, edit the file /etc/X11/gdm/gdm.conf. Find the parameter called KillInitClients, and set it to FALSE. If you do not, your VNC session will get disconnected after you've logged in.

That worked for me !

Thank you!  Thank you!  Thank you!

I'm using vnc4server instead of tightvncserver.

Also, I added '-localhost' to the line in /etc/X11/gdm/Init/Default.  This means I have to ssh into the box and forward local port 5900 to localhost:5900 on the remote end... which gives me an end-to-end encrypted session.

---

### Post by James79 on 2006-09-27
Its cool that I've been using ubuntu for only 2 weeks and I'm already able to return some help to someone :) 

Curious thing I've been noticing recently however... Sometimes after disconnecting a (working) VNC session, subsequent connection attempts result in a error message saying something about "incompatible vnc protocols". Which makes no sense, since I'm normally able to connect just fine.

Once I see this message, it never allows me to connect ever again. I have to reboot the machine, then all is well once again. Maybe there's a way to restart a specific service instead of the whole server? (even with VNC connections being refused I can still access the machine via ssh)

It only seems to take 1 or 2 succesful VNC connections before I start getting this error message.

The VNC client I'm using is the latest windows based ultravnc viewer.

Any thoughts on this would be great!

---

### Post by discombobulation on 2006-09-27
> **James79 said:**
> Its cool that I've been using ubuntu for only 2 weeks and I'm already able to return some help to someone :) 


Yes, thank you very much!

> **James79 said:**
> Maybe there's a way to restart a specific service instead of the whole server? (even with VNC connections being refused I can still access the machine via ssh)


If we could get the xinet.d method working, the VNC service would start every time you connected and stop every time you disconnected.  This is why I was trying to use lamego's method: [http://ubuntuforums.org/showpost.php?p=1548036&postcount=6](http://ubuntuforums.org/showpost.php?p=1548036&postcount=6)


> **James79 said:**
> It only seems to take 1 or 2 succesful VNC connections before I start getting this error message.

The VNC client I'm using is the latest windows based ultravnc viewer.

Any thoughts on this would be great!

One reason I went with vnc4server instead of tightvncserver is that vnc4server seems to be a more standard implementation.  (It's also appears to be much more current.)  Also, I am using VNC Viewer 4.1.2 from [http://www.realvnc.com/](http://www.realvnc.com/) for assured compatability.  You might try the same server/client combination to see if it fixes things.

---

### Post by discombobulation on 2007-05-02
> **James79 said:**
> Its cool that I've been using ubuntu for only 2 weeks and I'm already able to return some help to someone :) 

Curious thing I've been noticing recently however... Sometimes after disconnecting a (working) VNC session, subsequent connection attempts result in a error message saying something about "incompatible vnc protocols". Which makes no sense, since I'm normally able to connect just fine.

Once I see this message, it never allows me to connect ever again. I have to reboot the machine, then all is well once again. Maybe there's a way to restart a specific service instead of the whole server? (even with VNC connections being refused I can still access the machine via ssh)

It only seems to take 1 or 2 succesful VNC connections before I start getting this error message.

The VNC client I'm using is the latest windows based ultravnc viewer.

Any thoughts on this would be great!

I use a different VNC client, so I don't get the same error... but I think I am experiencing the same thing.

If I end a vnc session abnormally (like the client system loses network connectivity), I will get errors on the next connection attempt.  To fix it without rebooting the server, you have to kill the x11vnc process ID (which can be found with '[font=courier]ps aux|grep x11vnc|grep -v grep[/font]') and then restart the server with this:
```
sudo /usr/local/bin/x11vnc -rfbauth /root/.vncpasswd -o /var/log/x11vnc.log -forever -bg
```

---

