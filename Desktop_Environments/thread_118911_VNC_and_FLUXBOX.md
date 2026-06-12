---
title: "VNC and FLUXBOX"
date: 2006-01-18
forum: Desktop Environments
---

### Post by D1G1T4L on 2006-01-18
i had vnc installed on gnome and could vnc into it but now i changed to fluxbox and it seems i cant vnc to it, what should i do?

---

### Post by DaMasta on 2006-01-18
vncserver :1 then vnc to your_ip:1

---

### Post by D1G1T4L on 2006-01-18
[QUOTE=DaMasta]vncserver :1 then vnc to your_ip:1[/QUOTE]

i dont really understand what you mean


i used to run VNC server on my ubuntu and used windows xp box/vnc viewer to connect to my box, now that installed fluxbox and use it, it doesnt let me vnc

what should i do in fluxbox so i can vnc to it?

write vncserver:1 in prompt? or can you elaborate more

---

### Post by DaMasta on 2006-01-18
[QUOTE=D1G1T4L]i dont really understand what you mean


i used to run VNC server on my ubuntu and used windows xp box/vnc viewer to connect to my box, now that installed fluxbox and use it, it doesnt let me vnc

what should i do in fluxbox so i can vnc to it?

write vncserver:1 in prompt? or can you elaborate more[/QUOTE]
Yeah, sorry. Open a terminal and type **vncserver -geometry 1024x768 -depth 16 :1**. This will create a vnc session on 5901 at 1024x768 resolution and 16bit color depth. Then, run you windows vnc client and point it to your ip followed by the colon and 1. So, 192.168.0.1:1 or whathaveyou. Now, starting up that vncserver session probably starts gnome. So you need a .xsession file in your home directory that has **exec fluxbox** in it.

---

### Post by D1G1T4L on 2006-01-18
[QUOTE=DaMasta]Yeah, sorry. Open a terminal and type **vncserver -geometry 1024x768 -depth 16 :1**. This will create a vnc session on 5901 at 1024x768 resolution and 16bit color depth. Then, run you windows vnc client and point it to your ip followed by the colon and 1. So, 192.168.0.1:1 or whathaveyou. Now, starting up that vncserver session probably starts gnome. So you need a .xsession file in your home directory that has **exec fluxbox** in it.[/QUOTE]

vncserver command not found

---

### Post by DaMasta on 2006-01-18
sudo apt-get install vncserver

---

### Post by D1G1T4L on 2006-01-19
[QUOTE=DaMasta]sudo apt-get install vncserver[/QUOTE]


ok i installed it and it works but the thing is i am running FLUXBOX but when i VNC, it shows me my GNOME desktop... how do i make it show FLUXBOX?

---

### Post by D1G1T4L on 2006-01-19
Does anyone know?

---

### Post by soulestream on 2006-01-19
the server config file should have an option on what WM to launch when you log in. If its lauching gnome and you are currently running fluxbox, then its not going to be contolling the correct "desktop". 

If thats okay with your just change you config file to launch fluxbox instead of gnome. 


I wish i could be more helpful, but i havent used vnc in awhile

soule

---

### Post by D1G1T4L on 2006-01-19
[QUOTE=soulestream]the server config file should have an option on what WM to launch when you log in. If its lauching gnome and you are currently running fluxbox, then its not going to be contolling the correct "desktop". 

If thats okay with your just change you config file to launch fluxbox instead of gnome. 


I wish i could be more helpful, but i havent used vnc in awhile

soule[/QUOTE]

where is server config file and how / what do i change

---

### Post by DaMasta on 2006-01-19
Did my suggestion for creating a .xsession file not work? It worked for me.

---

### Post by D1G1T4L on 2006-01-19
[QUOTE=DaMasta]Did my suggestion for creating a .xsession file not work? It worked for me.[/QUOTE]

i am really sorry ,i missed that part, about to try it now

---

### Post by D1G1T4L on 2006-01-19
ok i created it now but now it says "unable to connect to host: Connection refused (10061)

---

### Post by DaMasta on 2006-01-19
[QUOTE=D1G1T4L]ok i created it now but now it says "unable to connect to host: Connection refused (10061)[/QUOTE]
Try **vncserver -kill :1**. Then run the vncserver command with the options again. I bet you had one running and it put it on :2.

---

### Post by D1G1T4L on 2006-01-20
[QUOTE=DaMasta]Try **vncserver -kill :1**. Then run the vncserver command with the options again. I bet you had one running and it put it on :2.[/QUOTE]

nope still cant connect


it says

New "x" desktop is esintein:1

when i start the vncserver

---

### Post by DaMasta on 2006-01-20
See if you connect to :1 on that machine. So from esintein, type **xvncviewer 127.0.0.1:1** or vncviewer.

---

### Post by D1G1T4L on 2006-01-20
[QUOTE=DaMasta]See if you connect to :1 on that machine. So from esintein, type **xvncviewer 127.0.0.1:1** or vncviewer.[/QUOTE]

yea i can

---

### Post by D1G1T4L on 2006-01-20
Never mind! i made it work
when i connect from windows, i forgot to add :1 at the end


can u explain to me the difference between :1 :2 etc

---

### Post by DaMasta on 2006-01-20
You can have mutilple server sessions running. For example, if two people wanted to connect via vnc, you could have one connect to :1 and the other connect to :2.

---

### Post by D1G1T4L on 2006-01-20
for some reason though, it just shows fluxbox and it doesnt show all my windows etc, when i move the mouse, it doesnt move around on the other screen

its like running its own instance

for example when i open xterm window in vnc from windows, it doesnt show it on my linux desktop, its like they are 2 different desktops

---

### Post by DaMasta on 2006-01-20
Yeah, it won't. You're desktop in linux is using :0 and I'm not sure how to view that. You can try replacing :1 with :0 and see what happens.

---

### Post by D1G1T4L on 2006-01-20
[http://ubuntuguide.org/#remotedesktop](http://ubuntuguide.org/#remotedesktop)

shows that you can somehow connect to :0


when i try to run a vncserver :0 on flubox through eterm it says

Warning: einstein:0 is not taken because of /tmp/.X0-lock
Remove this file if there is no X server einstein:0
A VNC server is already running as :0

---

### Post by D1G1T4L on 2006-01-20
seems like if i get into gnome, i can connect to :0
however it doesnt even say vncserver :0 is running

i am sure there is a way to get into fluxbox using :0 if it's possible with gnome, someone has to know =/

---

### Post by DaMasta on 2006-01-20
Yeah, gnome uses vino. Not really sure what that is. I never bothered looking into it. But vino may be the ticket.

---

### Post by D1G1T4L on 2006-01-30
i found this
[http://www.realvnc.com/products/free/4.1/x0.html](http://www.realvnc.com/products/free/4.1/x0.html)

but i really dont understand the directions, it suppose to explain how to connect :0

maybe you can help me out? thanks

---

### Post by D1G1T4L on 2006-02-01
anyone

---

### Post by andlinux21 on 2006-02-05
I have vncserver running on my main box but when i try to connect using my breezy laptop nothing happens. I can connect using my XP box using TightVNC viewer just fine I dont know what I am doing wrong is there another viewer I can install on my laptop to see if that works?:confused:

---

### Post by D1G1T4L on 2006-02-07
[QUOTE=andlinux21]I have vncserver running on my main box but when i try to connect using my breezy laptop nothing happens. I can connect using my XP box using TightVNC viewer just fine I dont know what I am doing wrong is there another viewer I can install on my laptop to see if that works?:confused:[/QUOTE]

when you connect, you connect to :0 ?

---

### Post by ninocass on 2006-04-05
did nayone get this fixed?  im able to connect but the currently opend windows are not displayed its like its starting another session

---

