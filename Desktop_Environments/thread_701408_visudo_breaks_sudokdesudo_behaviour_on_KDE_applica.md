---
title: "visudo breaks sudo/kdesudo behaviour on KDE applications"
date: 2008-02-19
forum: Desktop Environments
---

### Post by realn on 2008-02-19
I want to run application "kcron" as superuser without having to enter everytime the password.

Here is what happens when I must enter the password:
1) kdesu /usr/bin/kcron
Xlib:  extension "XInputExtension" missing on display ":1.0".
Failed to get list of devices
kdesu: WARNING: Could not start daemon, reduced functionality.
Xlib:  extension "XInputExtension" missing on display ":1.0".
Failed to get list of devices
DCOPClient::attachInternal. Attach failed Could not open network socket
Xlib:  extension "XInputExtension" missing on display ":1.0".
Failed to get list of devices
kbuildsycoca running...
Reusing existing ksycoca

2) sudo kcron
[sudo] password for myuser:
Xlib:  extension "XInputExtension" missing on display ":1.0".
Failed to get list of devices
Error: "/tmp/kde-myuser" is owned by uid 1000 instead of uid 0.

On both cases 1) and 2) the kcron window pops up, everything is OK, it's the kcron root's window.

Here is what happens after I added with visudo the following line:
myuser   ALL=(root) NOPASSWD: /usr/bin/kcron

3) kdesudo  /usr/bin/kcron
Xlib:  extension "XInputExtension" missing on display ":1.0".
Failed to get list of devices
Xlib: connection to ":1.0" refused by server
Xlib: Client is not authorized to connect to Server
kcron: cannot connect to X server :1

4)  sudo  /usr/bin/kcron
Xlib: connection to ":1.0" refused by server
Xlib: Client is not authorized to connect to Server
kcron: cannot connect to X server :1

On both cases 3) and 4) the kcron is not launched.

Could someone please enlighten me with the following questions:
1) Why can't I lauch the application in cases 3&4  ?
2)How can i do it?


 Thanks a lot to everyone !

---

### Post by realn on 2008-02-20
Upping the post ....

Please, someone help me at least with telling me if this is a bug or not.

 Thanks a lot!

---

### Post by realn on 2008-02-26
Hello,

Please, can someone please help ?
Thanks a lot!

---

### Post by aysiu on 2008-02-26
> **realn said:**
> 
2) sudo kcron
[sudo] password for myuser:
Xlib:  extension "XInputExtension" missing on display ":1.0".
Failed to get list of devices
Error: "/tmp/kde-myuser" is owned by uid 1000 instead of uid 0. Please do not use *sudo* with a graphical application. Use *kdesu* instead.

> Here is what happens after I added with visudo the following line:
myuser   ALL=(root) NOPASSWD: /usr/bin/kcron Shouldn't it be ```
*username* ALL=(ALL) NOPASSWD:/usr/bin/kcron
``` instead? I'm not sure if that solves the problem or not, but that's the format I've been taught to change for no password on a *kdesu* or *gksudo* application.

---

### Post by realn on 2008-02-29
Hello, thanks a lot
I added to the sudoers file the line as you showed me, I got a slightly different message, but the kcron still doesn't open:
kdesu /usr/bin/kcron
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified
kcron: cannot connect to X server :0.0

If I remove/comment the line, I get the password dialog box on a kdesu /usr/bin/kcron command, I enter it, then the window opens fine:
kdesu /usr/bin/kcron
passprompt
kbuildsycoca running...
kdecore (KProcess): WARNING: _attachPty() 11

Please, can someone help, I really would like not to have to enter passwords everytime I want to do the slightest thing. 
Thanks a lot!

---

### Post by realn on 2008-03-18
Upping it !
Please, could someone help, I still have the problem described above. There must be a simple explanation to this problem and a simple solution, I hope.
Thanks a bunch!

---

