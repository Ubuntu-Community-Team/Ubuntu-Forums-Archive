---
title: "Help setting VNC server at the start"
date: 2011-01-25
forum: Desktop Environments
---

### Post by Dsky on 2011-01-25
```
mulo@mulo-System-Name:~$ sudo vncserver

You will require a password to access your desktops.

Password:
Verify:

New 'mulo-System-Name:1 (root)' desktop is mulo-System-Name:1

Creating default startup script /home/mulo/.vnc/xstartup
Starting applications specified in /home/mulo/.vnc/xstartup
Log file is /home/mulo/.vnc/mulo-System-Name:1.log

```

I just need to do this?

i tried doing this but on windows with another machine if i try to connect at this ip it says me "connection refused"

why?

thanks!

---

### Post by b89.smith on 2011-01-25
Try connecting to mulo-System-Name:5901. The :1 stands for the port number for the desktop you created. Connect to 5900 + the port number.

---

### Post by Dsky on 2011-01-25
uhm... so i don't have to connect to the ip but to mulo-System-Name:5901 ?

i tried but nothing

 "unable to resolve host by name"

---

### Post by Dsky on 2011-01-25
i tryed following this guide and it works..

[http://www.ehow.com/how_6118151_configure-vnc-ubuntu.html](http://www.ehow.com/how_6118151_configure-vnc-ubuntu.html)

to make it work at the star i need only to put this in admin-start application?

sudo x11vnc -forever -usepw -httpdir /usr/share/vnc-java/ -httpport 5800

edit: no it doesn't work like this, maybe couse it need the pwd to be started? :)  some help?

---

### Post by Krytarik on 2011-01-25
You added it to "System -> Preferences -> Startup Applications", right?

Then you don't need to use "sudo", because the command is effectively run by the user.

It wouldn't work anyway with "sudo", because it can only be used at the command line, not in a graphical environment, therefore you would have to use "gksudo", then a password query dialog would get displayed. But in your case, the command simply fails.

Greetings.

---

