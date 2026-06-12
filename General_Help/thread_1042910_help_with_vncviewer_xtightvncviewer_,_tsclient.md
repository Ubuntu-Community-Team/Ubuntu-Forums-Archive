---
title: "help with vncviewer xtightvncviewer , tsclient?"
date: 2009-01-18
forum: General Help
---

### Post by limanoit on 2009-01-18
i have 2 computer. 

1 ubuntu . 
1 windows. 

they are set up under  1 same network/ router

windows can remote to my ubuntu with no problem

the problem is my ubuntu can not remote to windows computer. 

terminal .vncviewer. as I enter my windows 192.168.123.143. i hit enter. the server dialog does not respond nor does the tsclient able to connect to windows using vnc protocol

i set group policy on windows to allow to connect without password.. 

of course i ping to my windows computer and i got good result. and i currently can share files between ubuntu and windows ( connection shldnt be the problem?) 


ughh any idea how to solve this problem?

---

### Post by DeMus on 2009-01-18
> **limanoit said:**
> i have 2 computer. 

1 ubuntu . 
1 windows. 

they are set up under  1 same network/ router

windows can remote to my ubuntu with no problem

the problem is my ubuntu can not remote to windows computer. 

terminal .vncviewer. as I enter my windows 192.168.123.143. i hit enter. the server dialog does not respond nor does the tsclient able to connect to windows using vnc protocol

i set group policy on windows to allow to connect without password.. 

of course i ping to my windows computer and i got good result. and i currently can share files between ubuntu and windows ( connection shldnt be the problem?) 


ughh any idea how to solve this problem?


I use TightVNC on both PC's and here it works well. I can contact my Windows PC from my Ubuntu machine.
One strange thing though, when i connect, I do have to type the IP address of the Windows PC, then the name of the PC and then the password. I would expect typing just the name would be enough. But since it is running 24/7 I don't start it so often and once running, it is running well.

---

### Post by limanoit on 2009-01-18
how did you type the ip the name and the password on terminal ? 

i have got this 

 

ecs@ecs-desktop:~$ vncviewer 192.168.123.143
vncviewer: ConnectToTcpAddr: connect: Connection timed out
Unable to connect to VNC server


it knows that there is a VNC server listening on that IP (not sure what port ) but it gets timed out.

windows can connect to ubuntu. not vice versa. we can share files. ping reached.. group policy to allow non password is set.. windows firewall allow other computer to connect.. 

what s wrong .....

---

### Post by DeMus on 2009-01-18
> **limanoit said:**
> how did you type the ip the name and the password on terminal ? 

i have got this 

 

ecs@ecs-desktop:~$ vncviewer 192.168.123.143
vncviewer: ConnectToTcpAddr: connect: Connection timed out
Unable to connect to VNC server


it knows that there is a VNC server listening on that IP (not sure what port ) but it gets timed out.

windows can connect to ubuntu. not vice versa. we can share files. ping reached.. group policy to allow non password is set.. windows firewall allow other computer to connect.. 

what s wrong .....

When I start the Tightvnc program in Ubuntu, I get a small window in which I can type the data.
One thing I just remembered, I did have to add Tightvnc to the Windows firewall exceptions to be able to get through it. Since I am too lazy to do that, I just switched of the Windows firewall completely. My modem-router has a good firewall which keeps all unwanted stuff out.

---

### Post by limanoit on 2009-01-18
oh wow nice i am going to try switch of windows firewall completely.

what port is tightvns listening to ? do you know ?

---

### Post by damormino on 2009-01-18
I use rdesktop on my Ubuntu computer control my Windows XP computers remotely.

The Windows XP computer my be set up to allow Remote Desktop.  You can right-click "My Computer" and select "Properties", then go to the Remote tab and check the box "Allow users to connect remotely to this computer."  You need to have a password on the Windows XP computer (which is unfortunate).

Back on the Ubuntu computer, open a Terminal and type "rdesktop 192.168.1.1" (except use the IP address of your Windows XP computer).  You should get a Windows login dialog.  Just log in using your Windows username and password.

Also....

tsclient *should* work also (just like rdesktop).  Just put the IP address in of the Windows computer in the Computer box, use Protocol RDPv5, enter you Windows username and password and click connect.

I believe vncviewer requires a vncserver on your Windows computer (which it appears you already understand).  I don't like this approach as rdesktop always works for me.

Two things to check...
[LIST=1]
[*]Make sure you Windows computer has a username and password.
[*]Perhaps Windows does not like having both a VNC server running along with Remote Desktop enabled.  Try these one at a time.
[/LIST]

---

### Post by limanoit on 2009-01-18
omg i worked. 

gosh firewall is ...bleh.. 
and the display refreshes so slow .. even under one network.

now is a lil bit better but how can i improve this . ughh . thanks by the way.

---

### Post by DeMus on 2009-01-18
> **limanoit said:**
> oh wow nice i am going to try switch of windows firewall completely.

what port is tightvns listening to ? do you know ?

I looked in the Windows machine and it says Main port is 5900, Http port is 5800. Both are greyed out since I use the automatic setting.

You don't need to switch off the firewall completely, you can add exceptions to it. Add Programm and choose Tightvnc. This will make Windows a little bit more safe then completely without a firewall, or you should be, just as I am, behind a router with a good firewall.

Success.

---

### Post by limanoit on 2009-01-18
so its port 5900   oh okay thanks .but now i could nt input keyboard remotely. . 

:( 

the display refreshes so slow. i think it s my old laptop . .that does not have good hardware because windows can remote to ubuntu and it s fast. thanks guys! 

i havent tried rdesktop .

thanks guys for fast help

---

### Post by DeMus on 2009-01-18
> **limanoit said:**
> but now i could nt input keyboard remotely. . 


What do you mean with that?

---

### Post by limanoit on 2009-01-18
i dont block any remote input on vnc server.  i think i should be able to not only use the mouse i should be able to use keyboard as input too . but it somehow does not work

---

### Post by limanoit on 2009-01-18
> **DeMus said:**
> What do you mean with that?

i mean i can control the compute but only with mouse. not with keyboard... 
which is sucks....... 

i guess the vnc server on windows does not say anything that does not allow keyboard as an input . 


were you able to use keyboard as input device to remote computer ?

---

### Post by DeMus on 2009-01-18
> **limanoit said:**
> i dont block any remote input on vnc server.  i think i should be able to not only use the mouse i should be able to use keyboard as input too . but it somehow does not work

Can you read the text in the picture I sent in my earlier post? It's a screendump of the Tightvnc settings.
On the bottom left quadrant it says: Input handling. Did you switch on one of the choices there or are they set just like in my picture?

---

### Post by limanoit on 2009-01-18
nope none of them were switched on  

something weird on the terminal it says 


(tsclient:5374): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.18.2/gobject/gsignal.c:2384: instance `0xa0610f0' has no handler with id `1097'

it might explain why ? haha. 

but anyway i am not gonna use it . it s too slow.

---

