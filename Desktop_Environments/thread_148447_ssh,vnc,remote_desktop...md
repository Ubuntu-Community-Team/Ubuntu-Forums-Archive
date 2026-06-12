---
title: "ssh,vnc,remote desktop.."
date: 2006-03-22
forum: Desktop Environments
---

### Post by tellnes on 2006-03-22
I would love alittle howto remote desktop guide.
Anyone have the time or know of a site that guides a user trought it?

At work i have a xp, full admin rights, and both putty and vnc.

At home, a ubuntu dekstop, behind a router running nat.

So my pc at home is at 192.168.1.x, i can open ports in the router into the ubuntu. 
How do i set up ssh,vnc to remotly manage my ubuntu from work using vnc viewer..
Any help is much apprisiated.

---

### Post by Sendervictorius on 2006-03-22
Does your pc at home have a permanent copnnection to the internet, and a pemanent ip address, or does it get a new one each time you connect?

---

### Post by tellnes on 2006-03-22
static ip on wan and on local net..the ip configuration is ok i guess and i can do wannt with that..

---

### Post by alamba on 2006-03-22
Don't think VNC is very secure buddy, AFAIK it transmits data via an open (unencrypted) channel. This might be outdated info though. I use ssh to remotely manage my system and scp for file transfers. If you're looking for how to install and get ssh up and running then shout out.

A

---

### Post by Didjit on 2006-03-22
This is exactly what I do. I don't have the exact details, but I can give you a quick overview.

 Install openssh-server. You can use the base VNC installed w/Ubuntu, but  I use Tight VNC ([http://www.tightvnc.com/](http://www.tightvnc.com/)  sudo apt-get install tightvncserver) I found it to be a little faster. In your router, you will need to port forward the SSH port (22 by default). Not a lot of detail, but I can help if you get stuck, I just don't have the time now to dig through my settings.

On your windows machine, you will install Tight VNC Viewer and Putty.  Used putty to tunnel the VNC connection through a SSH2 connection.  There are a handful of article explaining how to do this (this is one [http://people.hmdc.harvard.edu/~mathpre/vnc/putty/](http://people.hmdc.harvard.edu/~mathpre/vnc/putty/))

Good Luck. Let me know if you get stuck.

Chris

---

### Post by dave84 on 2006-03-22
hi!

do you need help about ssh?
i've never connected from a win xp computer to a linux host via ssh.

but for a connection between to linux hosts it's really great :cool: .

lg david

---

### Post by encompass on 2006-03-23
I think too keep things secure you would want to tunnel the vnc information threw the ssh secure lines... that way you get your graphical interface but the security of ssh.  I have been looking for a nice ubuntu howto but nothing so far.  
[http://pigtail.net/LRP/vnc/](http://pigtail.net/LRP/vnc/)
what my first guess, but I am a programming student not a network professional.  I want to learn, not teach... :)
Hope it help us get a good start.
TRY THIS!! I am not sure what he is talking about with putty on the windows side, I need screens when I am working with windows things.
[http://ubuntuforums.org/showthread.php?t=138496&highlight=tunnel+vnc+ssh](http://ubuntuforums.org/showthread.php?t=138496&highlight=tunnel+vnc+ssh)

---

### Post by tellnes on 2006-03-23
I had a linux guru help me once with this, and it worked so smooth.
I know we hacve to use ssh to make a tunnel from host a to b, okay, i do a apt-get ssh and install a ssh server on my ubuntu.

Now, on my windows, i use putty to access the ssh tunnel i guess..but i need to know what files to edit in regards to ip addressing so that my putty at work find my ubuntu at home..im sure we edited some host, ssh.conf files for this..anyone encountered this?

---

### Post by tellnes on 2006-03-23
What i would really apprisiate is this:
Ubuntu- 192.168.1.120, ssh-server.
Router - 192.168.1.1- global IP: 217.156.x.x (just an ex)
Ill put up forrowarding from port 22 from global ip to local ip on router.

Windows XP - putty, vnc viewer.
IP: 172.168.1.x
Global ip: 80.x.x.x

Now..if some one could tell me wich files i need to edit and what to set up with this example in mind, i would send virutal huggs to ya:)

---

### Post by NetMatrix on 2006-03-23
I use ssh and tunnels every day at work so here's a tutorial.

When using putty through windows click on tunnels in the left hand pane.

This will bring up a screen where you can enter the IP of the machine to tunnel into. Also you must add a port # we use 5900 (destination) then you can also enter a source port #.  Side note you can tunnel multiple times using different source ports.

Then after you set that up you click on Session in the left field (AFTER ADDING THE TUNNEL YOU JUST SET UP (CLICK ADD)) and enter the routable or external IP of the machine to ssh into.

Once you've logged in you should be able to open VNC and just point to localhost because you're actually already in the machine.

It's very early so if I've forgotten something someone please post and let me know.

Good Luck.

](*,)

---

### Post by encompass on 2006-03-29
I don't get the concept from the server side... I do I start vnc and run it from my ssh console?  not sure what you mean.  Perhaps a nice bit of screenshots would help. :D

---

### Post by Didjit on 2006-03-29
Server side, just have VNC server and Open SSH server running. 



Didijit

---

