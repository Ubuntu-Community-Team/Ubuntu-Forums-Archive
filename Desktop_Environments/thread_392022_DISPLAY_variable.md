---
title: "DISPLAY variable"
date: 2007-03-24
forum: Desktop Environments
---

### Post by baomike on 2007-03-24
Where does ubuntu set the DISPLAY variable. I have searched in vain. 
I have inserted "export DISPLAY=mike:0.0" in a lot of files but nothing seem to survive.


How do you kill the Xwindow display.  Every time I kill it it restarts. 
I am looking for a more elegant way than desecrating the xorg.conf file.

---

### Post by errhec on 2007-03-24
Try to push Ctrl+ Alt + Backspace
You should go to the login screen
Or you can change the screnns  
Ctrl+ Alt + F1 ( or F2 Or F3....)

>)

---

### Post by baomike on 2007-03-24
The display is still on the wrong machine.
I'ave got to find where ubuntu set this variable (DISPLAY).
default is usually "DISPLAY=:0.0" but I want "DISPLAY=mike:0.0"

Also I want to kill off the X windows manager , to save memeory and cycles.

---

### Post by puqing on 2007-03-24
If you use gdm and want to kill it, just type

sudo /etc/init.d/gdm stop

To kill other dms should be similar.

---

### Post by baomike on 2007-03-24
A little progress:
Kdm stop didn't seem to do it , but running kill -9 $PID   did . $PID being the PID of kdm.

Getting the display onto another machine is part way there. The boot process aparently uses the value set in /etc/kde3/kde/kdmrc. The variable is StaticServers and is usually set to :0 . Setting StaticServers to mike:0.0 causes the unbuntu boot to kill Xwindows on mike and I assume then start whatever. Of course it doesn't work because the Xwindows server on mike is dead. I have got to find the script that does the killing. Somewhere also, DISPLAY is set equal to StaticServers. 
Extensive greping of /etc and /etc/init.d have not turned up anything.

xterm -display 192.168.5.4:0.0  will start a terminal on mike just fine so hardware link is OK,  more digging.

---

