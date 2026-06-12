---
title: "Nothing happens when connecting to vncserver"
date: 2010-07-14
forum: Desktop Environments
---

### Post by anthalamus on 2010-07-14
Hi everyone,

I am trying to use the Remote Desktop and run into the following issue, when I connect to the vncserver, nothing happens :o   :

    ```
10:21:35 anthony@xxx:~$ vncviewer localhost:0
    ...
     CConn:       connected to host localhost port 5900
```It says connected but no new windows open or anything. I know for a fact that the server is running on port 5900 display :0

    ```
10:20:43 anthony@xxx:~$ lsof -i -n -P
    ...
    vino-serv 14905 anthony   16u  IPv6 2545680      0t0  TCP *:5900 (LISTEN)
    ...
```I disabled the firewall for testing purposes so it can't be it either. I also disabled the prompt for permission to connect (I'm on a very secured network btw). When I use vinagre (the GUI tool), it doesn't ask for the display and only a terminal appears, no desktop.

Now maybe I misunderstand what VNC can do, I'm trying to access my current desktop remotely (well actually locally first), meaning that I don't want to connect to a NEW desktop. Hopefully that's possible with VNC!

Thanks a lot in advance  :wink: 
Anthony

---

### Post by anthalamus on 2010-07-14
Ok, solved my own problem.

I use x11vnc instead of vino, works like a charm.
for info, it works like this: 

- [install x11vnc if you don't have it yet]
- open a terminal
- type "vncpasswd" and specify a password (I recommend saving it in the default ~/.vnc/passwd file)
- then run: 
```
x11vnc -rfbauth ~/.vnc/passwd # tells server which password file to use
```- it will tell you what display to use, on the screen you will see something like:
   ```
The VNC desktop is:      name_of_your_computer:2
   PORT=5902
```- then using vncviewer (locally or from another computer that can see the server computer), use:
```
vncviewer name_or_your_computer :2 # because it runs on display 2 according to what the server said (note that you can specify your own if you want, see man x11vnc)
```note: that if you do run it locally, you will obtain a window that has windows inside them and expand recursively (you know like when you put 2 mirrors in front of each other :)

cheers everyone :popcorn:

---

