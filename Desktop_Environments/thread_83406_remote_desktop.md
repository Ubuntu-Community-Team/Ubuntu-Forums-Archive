---
title: "remote desktop"
date: 2005-10-28
forum: Desktop Environments
---

### Post by DarkManX4lf on 2005-10-28
what i want to do is access my linux machine from my windows laptop from anywhere....how would i do that? i made sure that remote desktop is enabled on my linux machine, and i get realVNC viewer on my laptop but when i try to connect to my linux machine (which is on a router) it wont connect....is there some ports that i should forward on the linux machine router?

---

### Post by Kyral on 2005-10-28
Hmm....

Stupid question, but did you check the "Let Others Control My Desktop" box?

Or try pinging the Linux box

---

### Post by DarkManX4lf on 2005-10-28
yea i have it enabled but i just cant connect when i put in the ip address of my linux machine

---

### Post by HermanAB on 2005-10-28
You have to open or forward 2 ports.

See this guide:
[http://www.aerospacesoftware.com/vnc-howto.html](http://www.aerospacesoftware.com/vnc-howto.html)

---

### Post by DarkManX4lf on 2005-10-28
ok i forwarded the ports 5800-5802 and 5900-5902 (i set them both to TCP and  UDP) in my router and i still cannot connect to my linux machine from outside my lan.

---

### Post by HermanAB on 2005-10-28
Uhmm - can you connect on itself to itself?

What I mean is: On the Linux box, run VNC Server, then open a VNC client and connect to itself.  If you cannot get it going on one machine, then there is no way you are going to make it work between two machines.

Run 'ps -e' to verify that the processes are running.

Try to test little by little.

'Hope this helps!

Herman

---

### Post by DarkManX4lf on 2005-10-28
[QUOTE=HermanAB]Uhmm - can you connect on itself to itself?

What I mean is: On the Linux box, run VNC Server, then open a VNC client and connect to itself.  If you cannot get it going on one machine, then there is no way you are going to make it work between two machines.

Run 'ps -e' to verify that the processes are running.

Try to test little by little.

'Hope this helps!

Herman[/QUOTE]

well i can connect to it by my laptop when im in my own network, so if i type in the lan ip adress to my linux box (192.168.0.xxx) vnc will work, but lets say if i go to my friends house and use his internet to access the linux box and i type my wan ip address it wont connect.

---

### Post by DarkManX4lf on 2005-10-29
ok i ran ps -e and i saw a bunch of processes i dont know if this vnc is running on the linux machine, what should i see when i type "ps -e" just vnc, or remote esktop or something?

---

### Post by Zwack on 2005-10-29
Well, it sounds like you are running VNC properly if you can connect to it on your local network...

So the problem is in your router...   Without knowing much about your router it looks like you are using some form of NAT setup, so you have to translate incoming IP ports X and Y from the router so that they are allowed in and connect to your linux box.  Depending on what you are trying to do you may find it easier to just allow SSH connections and do port forwarding through SSH.  That means that you only have one port you need to worry about and the connection is secure.

Z.

---

### Post by DarkManX4lf on 2005-10-31
[QUOTE=Zwack]Well, it sounds like you are running VNC properly if you can connect to it on your local network...

So the problem is in your router...   Without knowing much about your router it looks like you are using some form of NAT setup, so you have to translate incoming IP ports X and Y from the router so that they are allowed in and connect to your linux box.  Depending on what you are trying to do you may find it easier to just allow SSH connections and do port forwarding through SSH.  That means that you only have one port you need to worry about and the connection is secure.

Z.[/QUOTE]

well as suggested above (in a link) i forwarded ports 5900 and 5800, i even made it a range from 5900-5902 and  5800-5802 but it still doesnt work.

---

### Post by DarkManX4lf on 2005-11-01
bump

---

### Post by the_purulent on 2005-11-01
I had this problem too:
In the Remote Desktop settings tab, make sure the 'require my verification' (or something like that) box is unchecked. Otherwise you won't be able to connect unless someone on the linux box pushes the accept connection button that will pop up.

---

### Post by DarkManX4lf on 2005-11-01
yea i made sure that is checked off but it still wont connect.

---

### Post by HermanAB on 2005-11-01
You can debug it without walking to your friend's house, by typing in the address of your router on your Notebook, while connected to your LAN.  It should loop back.

First try to connect using something really simple, such as telnet to see whether the port forwarding works:
# telnet serverip vncportnumber

Try a few ports till the VNC server responds, eg:
telnet  192.168.1.1  5802

The VNC server should answer with some VNC text string.  Press "Ctrl-], quit" to close telnet.

Now do the same using the router IP:
# telnet routerip vncportnumber

If port forwarding works, then the server should respond exactly as before.

When debugging connectivity, always use the simplest possible tool, to rule out other problems.

Cheers,

Herman

---

### Post by gordyt on 2005-11-01
[QUOTE=DarkManX4lf]what i want to do is access my linux machine from my windows laptop from anywhere....how would i do that? i made sure that remote desktop is enabled on my linux machine, and i get realVNC viewer on my laptop but when i try to connect to my linux machine (which is on a router) it wont connect....is there some ports that i should forward on the linux machine router?[/QUOTE]

DarkManX4lf  I have some notes here [http://www.gordontillman.info/index.php?n=Development.Vnc]("http://www.gordontillman.info/index.php?n=Development.Vnc") and here [http://www.gordontillman.info/index.php?n=Development.OsxSsh]("http://www.gordontillman.info/index.php?n=Development.OsxSsh") that talk about using Vnc to access your desktop remotely by tunneling through SSH.  That is the way I prefer to do it because (1) it is secure and (2) you have to only have one port for SSH open on your firewall that is mapped to your machine on the internal network.

--gordy

---

### Post by DarkManX4lf on 2005-11-01
[QUOTE=HermanAB]You can debug it without walking to your friend's house, by typing in the address of your router on your Notebook, while connected to your LAN.  It should loop back.

First try to connect using something really simple, such as telnet to see whether the port forwarding works:
# telnet serverip vncportnumber

Try a few ports till the VNC server responds, eg:
telnet  192.168.1.1  5802

The VNC server should answer with some VNC text string.  Press "Ctrl-], quit" to close telnet.

Now do the same using the router IP:
# telnet routerip vncportnumber

If port forwarding works, then the server should respond exactly as before.

When debugging connectivity, always use the simplest possible tool, to rule out other problems.

Cheers,

Herman[/QUOTE]


ok i tried that and none of the ports that i forwarded seem to work...
this is what i did in winxp

telnet 192.168.0.100 5800  (and this wouldnt connect)

i did that for ports 5800-5802 and 5900-5902.

using my laptop within my lan i tried to use vncviewer (on my winxp laptop) with my wan ip and it wouldnt connect either.....

> DarkManX4lf I have some notes here [http://www.gordontillman.info/index....evelopment.Vnc](http://www.gordontillman.info/index....evelopment.Vnc) and here [http://www.gordontillman.info/index....lopment.OsxSsh](http://www.gordontillman.info/index....lopment.OsxSsh) that talk about using Vnc to access your desktop remotely by tunneling through SSH. That is the way I prefer to do it because (1) it is secure and (2) you have to only have one port for SSH open on your firewall that is mapped to your machine on the internal network.

i dont want to use ssh, because then i would have to use putty on my laptop which will only give me a terminal command line which is what i dont need i need a graphical view of my desktop/menu's etc....

---

### Post by DarkManX4lf on 2005-11-01
ok i managed to get it to work while outside my lan (it worked after i install vnc4server from synaptic), but the bad thing is it only works in gnome and i currently use xfce...how can i get remote desktop to work with xfce?

---

### Post by DarkManX4lf on 2005-11-02
bump

---

### Post by DarkManX4lf on 2005-11-02
wow this board moves fast, bump again

---

### Post by NewWithoutClue on 2005-11-02
i have a rather insecure suggestion:
On my router i have an option to 'DMZ' myself ( making the ip i provide visible to the putside world ). I use that because my other computer is windows ( family computer ) and i wouldn't need to have open ports on it anyway.
Needless to say, be aware of the risks involved.

w00t,
Paul.

---

### Post by NewWithoutClue on 2005-11-02
another suggestion:
monitor open ports and connections on the server side when connecting to it.
( see what port your connection actually lands on )
netstat is your friend.

w00t
Paul.

---

### Post by DarkManX4lf on 2005-11-02
i actually got the vnc to work, with the ports forwarded i guess i had to install vnc4server from synaptic...but i tonly works when my linux machine is in gnome,  but i currently use xubuntu/xfce how would i get vnc to work with xfce?

---

### Post by DarkManX4lf on 2005-11-03
bump

---

### Post by DarkManX4lf on 2005-11-04
bump

---

### Post by gordyt on 2006-01-27
[QUOTE=DarkManX4lf]
i dont want to use ssh, because then i would have to use putty on my laptop which will only give me a terminal command line which is what i dont need i need a graphical view of my desktop/menu's etc....[/QUOTE]

DarkMan that isn't correct -- what you are actually doing with that procedure is tunneling over SSH - I do it every day and I use a graphical vnc client so I can see all of my desktop, windows, etc., of the remote machine, no problem!

--gordy

---

