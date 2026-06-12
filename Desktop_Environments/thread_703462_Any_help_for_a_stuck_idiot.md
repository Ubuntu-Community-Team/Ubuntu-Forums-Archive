---
title: "Any help for a stuck idiot?"
date: 2008-02-21
forum: Desktop Environments
---

### Post by Son of Silas on 2008-02-21
Hi, I am typing this on an ubuntu server via VNCviewer from my Ubuntu laptop.

I have a file transfer that I cannot interrupt on this server and the VNC session is running fullscreen. When I intended to disconnect myself from this server by clicking on the VNC icon on the launcher panel, I accidently deleted the icon from the launcher panel by mistake, rather than disconnecting myself.

So no I'm stuck. How can I end this VNCviewer session and return my Keyboard, Video and mouse back to my laptop, without rebooting the server and messing up the file transfer?

Help!

---

### Post by OffAxis on 2008-02-21
you could try restarting the vnc server process in /etc/init.d/
or you could kill the process outright;


```
sudo ps -A
```
to look up the associated process number
and then

```
sudo kill <process number>
```

---

### Post by Son of Silas on 2008-02-21
Thanks!!!!

OK, so now... Ho can I replace that missing icon for next time??

---

### Post by OffAxis on 2008-02-21
I think you can right click on VNC's entry in the program listing and choose 'add icon to panel' or you can right click on the launcher and choose 'add program to launcher'.
I don't quite remember how gnome handles it.
sorry.

---

