---
title: "remote desktop without PCI card"
date: 2009-12-21
forum: Desktop Environments
---

### Post by rahulbhide on 2009-12-21
Hi All,
 
I need help to access my Ubuntu server 2.6.28 from a remote desktop, The setup is something like this:
I have a Soekris Box net4801 which **doesno**t have a pci card on it.
I have installed Ubuntu server on it and also did install
apt-get install ubuntu-desktop 
also started the gdm service. 
 
Tried installing VNC server (on Ubuntu) and VNC cllient on my Windows XP but the connection fails. If I try to open port 5900 by using nc -lvp 5900(I found this command on internet) it tries to establish connection but fails too.
 
So summarising I have 2 questions or issues,
1. With Soekris not having PCI card can I start the GUI at all ?
2. If I can access the GUI from Remote desktop or machine, How do I do it ?
 
My limitations : I have have **serial as well as SSH access** to the Ubuntu Server (installed on Soekris net4801) and my Ubuntu knowledge is limited.:(
 
I have tried several things but in vain. Any suggestions will be greatly appreciated.:cry:
 
Thanks in advance,
Rahul

---

### Post by hugmenot on 2009-12-21
I think you have to start the vncserver. Just installing GDM is not enough. The vncserver will start the session, which will run until you kill the vncserver. You don&#8217;t need a screen for that (re: PCI).

Make sure the server runs before you try connecting with a client.

---

### Post by falconindy on 2009-12-21
VNC is not the way to go. X **needs** to have a graphical output in order to start. Look into X11 forwarding. Essentially, it allows you to run the applications on the server, but the graphical end on the client.

---

### Post by hugmenot on 2009-12-21
> **falconindy said:**
> VNC is not the way to go. X **needs** to have a graphical output in order to start. Look into X11 forwarding. Essentially, it allows you to run the applications on the server, but the graphical end on the client.

No. the VNC server /is/ the graphical output. I know it works like this.

---

### Post by rahulbhide on 2009-12-22
Guys, Thanks for your comments.
 
I ma going to try the VNC option first to start the vncserver and then I will also look at X11 forwarding.
 
When I run VNC server start it gives me following message,
 
*hostname*:~# vncserver
xauth: (argv):1: bad display name "*hostname*:10" in "add" command
New 'X' desktop is *hostname*:10
starting applications specified in /root/.vnc/xstartup
Log file is /root/.vnc/*hostname*:10.log
 
... where *hostname* is my soekris machine name on ubuntu
I tried to compare /etc/X11/xorg.conf file with a server which has it graphics card and they are pretty much different. The xorg.conf file which I have looks like doesnt have any settings like in the other file. Do you think that might be the problem ?
 
Thanks much,
Rahul

---

### Post by hugmenot on 2009-12-22
Actually, it looks like it started. Did you try to connect after this?

If not, can you try to run
```
vncserver :1 -depth 24
```


EDIT: use this help page: [https://help.ubuntu.com/community/VNC/Servers#tightvncserver](https://help.ubuntu.com/community/VNC/Servers#tightvncserver)

---

### Post by hugmenot on 2009-12-22
Oh and you have another option as well: NX

It&#8217;s faster and looks better as well.
There is a company backing it, which provides packages that are easier to install tthan the community versoin of this protocol. If you&#8217;re interested look at [http://nomachine.com](http://nomachine.com)

---

### Post by rahulbhide on 2009-12-22
Thanks Hugmenot,
 
It looks like it started the vncserver. I am trying to use a TightVNC client on my XP laptop to access the ubuntu server. When I fire up my client it still fails to open.
 
And on the ssh window if I type vncviewer *hostname*:1 it does not open giving me a message 
vncviewer; unable to open display ""
 
In either case I am not able to open the GUI.
 
Regards,
Rahul

---

### Post by hugmenot on 2009-12-22
Well, you tried opening the viewer on the server side, when you typed vncviewer into the SSH shell. That can&#8217;t possibly work.

Try this:

On the server side
```
vncserver :1 -depth 24
```

To check what port it is running on use this command:
```
netstat -anp | grep vnc
```

Then on Windows with your graphical client connect to *hostname* display :1, or port 5901.

---

### Post by rahulbhide on 2009-12-22
Hi,
 
Yes I kind of got that I was doing wrong thing by typing vncviewer on the server..that didnt server any purpose. Anyways I tried connecting specifying port 5901 and it has atlease made the connection with a small black window in a grey window. Looks like I have a problem with the display settings...
 
Thanks for the suggestion plz let me know if you have seen this issue before.
 
Rahul

---

### Post by hugmenot on 2009-12-22
I think the small window in the big window is actually a small terminal in front of a blank desktop. Could that be?

Under the help link I gave you above they have a startup script that will give you a Gnome session.

But anyway, why don&#8217;t you just use an NX server instead of VNC? It will be much easier to set up. You just install 3 .debs from nomachine.com on your Soekris and an NX client on your Windows machine. They even setup the Gnome session for you.

---

### Post by rahulbhide on 2009-12-24
Hi hugemont,
 
I was looking at the NX server you suggested however the system reqs are 400Mhz processor for their SW and I have a 266MHz processor on Soekris, I am glad I saw that. 
I will try to work with setting the display, if you have any suggestion s on how to set the display please reply to the post.
If I get the workaround I will let you know. Thanks for the help.
 
Rahul

---

