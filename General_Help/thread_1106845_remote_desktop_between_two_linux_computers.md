---
title: "remote desktop between two linux computers"
date: 2009-03-26
forum: General Help
---

### Post by 80aless on 2009-03-26
Hello,
I have a laptop (Suse), computer at work (Ubuntu) and another computer at work (Windows). The last two are on the same network, with different IP of course. 
I can connect from Suse to Windows and vice versa, from Windows to Ubuntu and vice versa, but not Suse to Ubuntu or vice versa. I opened the ports as usual in System>Preferences>Remote desktop as usual. What's the problem? Is it because of the different networks?
Thanks,
Alex

---

### Post by 80aless on 2009-04-06
nobody?
> **80aless said:**
> Hello,
I have a laptop (Suse), computer at work (Ubuntu) and another computer at work (Windows). The last two are on the same network, with different IP of course. 
I can connect from Suse to Windows and vice versa, from Windows to Ubuntu and vice versa, but not Suse to Ubuntu or vice versa. I opened the ports as usual in System>Preferences>Remote desktop as usual. What's the problem? Is it because of the different networks?
Thanks,
Alex

---

### Post by ajmctaggart on 2009-04-06
Well, when you're at work, with your Laptop, are you putting on your work network?  From the way your post reads I'd suspect no.  If thats the case, since you already opened the right ports, did you port forward the router to the Ubuntu machine?

See, you have your internal IP and your external IP, so if you have port forwarding enabled that your external IP forwards to your Windows box, I think it takes more setup to have the option of using both machines on the network...not impossible, just a little more configuration...

like instead of the IP you put into remote desktop being 111.111.111.111, a default you could use with only one machine you want to remote into, it will be 111.111.111.111/XXXX which would be the port you use for Ubuntu, for instance...you'd have to use different ports for each machine, and specify that port when you want to remote in...


THESE SETTING WOULD NEED CONFIGURING ON THE UBUNTU MACHINE AND THE ROUTER, THE CLIENT WILL FIGURE IT OUT WHEN YOU PUT IN THE /XXXX OPTION AFTER THE EXTERNAL FACING IP!
Hope that helps...

---

### Post by 80aless on 2009-04-11
Hi, thank you very much for your reply,but I can't figure out what you want to say...
How do I "port forward the router to the Ubuntu machine" ? 
Thanks

---

### Post by Zack McCool on 2009-04-11
What remote desktop server software are you running on the Linux boxes, and what client software are you trying to use?

Linux doesn't have, by default, any remote desktop type server running.  

So, have you installed something like VNC on the machines (server), or as I prefer, NX server?

---

### Post by 80aless on 2009-04-11
Some time ago, when remote desktop used to work without any problem, I used krdc, but I also have vncserver/vncviewer . If I remember correctly, I have to do vncserver on the server. I just did it via ssh:
> Ubuntu_at_work:~$ vncserver
New 'Ubuntu_at_work:1 (aless)' desktop is Ubuntu_at_work:1

Starting applications specified in /home/aless/.vnc/xstartup
Log file is /home/aless/.vnc/Ubuntu_at_work:1.log

but krdc IPAddress_AtWork:0 or :1 does not work, ie the screen in krdc is blue.
Maybe I have to allow more than one user to log in, as described in:
[http://www.movingtofreedom.org/2007/02/16/howto-remote-desktop-with-vnc-in-ubuntu-edgy-gnu-linux/]("http://www.movingtofreedom.org/2007/02/16/howto-remote-desktop-with-vnc-in-ubuntu-edgy-gnu-linux/"), but that I can after the EAter vacations.

---

### Post by juancarlospaco on 2009-04-11
SSH with X redirection.
Graphical and secure...

---

### Post by 80aless on 2009-04-13
you mean ssh -X etc? yes, but it is not what I am looking for.. I am trying matlab and it is terribly slow. And It would be easier to access that computer you know..

---

### Post by ajmctaggart on 2009-04-13
80,

Sorry if I wasn't clear...

Lets assume Suse is NOT on your work network, but Ubuntu and Windows are...

You can get from Suse>Windows vice versa
     and from Windows>Ubuntu vice versa

Windows and Ubuntu are on the same network, which is why they can connect to each other, there's no firewall or external IP involved...

See, if Suse is connecting to your Windows Machine from outside your network, it's because you or someone has told your router that when a computer from the outside vnc's (using the external IP) into your work's network, it is supposed to send that request to your Windows box, this is how you connect your "out of work network" Suse to your "in network," Windows...

When you are already in your work network, ie Ubuntu box and Windows box, your router isn't going to block that communication, which is why you can connect from Ubuntu to Windows and vice versa...

BUT

If you try to connect your Suse "out of network" to Ubuntu "in network", it doesn't connect, probably because it is setup to try to connect to your Windows machine, and I assume you don't leave that in host all the time...

SO 

What will have to be done is for you to go into your router settings and do 1 of 2 things, or both, who knows, depending on your router...You would have to not only use the standard VNC ports, but also turn another port into a "VNC Capable one..."  So lets say you currently VNC on port 5900 (Standard I believe) You would also have to setup another port 5800, 69000, whatever, and tell your router that when someone VNC's in with THE NEW port specified, you accept it and send it to the Ubuntu box's Internal IP...

If port forwarding is enabled, (Please note the wording I use is only specific to my router and typically changes every 2 or 3 years and by router manufacturer, so you'll have to do some poking around), you could also just change the port forwarding from one machine to the next based on your need to get into either the Windows or Ubuntu box, but I'm sure this is a bad idea, since you need each computer for different tasks at random times...

This isn't as hard as it looks and I'm sure most people here could help with that...Here is an old version of Linksys' router firmware with a very basic example of port forwarding, I'm sure you can Google these instructions for any router known to man...

[http://portforward.com/english/routers/port_forwarding/Linksys/WRT54G/default.htm]("http://portforward.com/english/routers/port_forwarding/Linksys/WRT54G/default.htm")

If I am off on this one, I apologize, but from what you've told me, this seems to be the fairest assumption...

Good Luck!

---

### Post by 80aless on 2009-04-22
Hi, thank you for your reply. In these days I have been trying to eneble the ports with guidedog. 

One thing I do not understand is that the IP address in the 'Connection information' at home gives me a 192.***.*.35 IP, while on the site wwwip-address.com i get a 82.***.**.** number .
Anyway I can ssh from home to the office, but not the other way around!
I also did vncserver there (this is another thing I do not understand: do I have to do it?) . In guidedog I put in the forwarding tab all the combinations: 
192.***.**.*.35:TCP 0 -> 0 , meaning the Ip 192... can access the computer via the port 0.
82.***.**.**:TCP 0 -> 0
In the guidedog at home i have 
TCP 0 -> IP of the office

but no success. 
I do not know what to do..

---

### Post by egalvan on 2009-04-22
> **80aless said:**
> 
One thing I do not understand is that the IP address in the 'Connection information' at home gives me a 192.***.*.35 IP, while on the site wwwip-address.com i get a 82.***.**.** number .
 


The 192.***.*.35 is the in-ward facing, private LAN address.
If you didn't set this yourself, the it's probably given out by your router.

The 82.***.**.* is the out-ward facing, public Internet address.
Probably given out by your Internet Provider.

---

### Post by ajmctaggart on 2009-04-23
I see little to no reason to use GuideDog to setup VNC from machine to machine, but that is your decision...Maybe I don't know enough about it to knock it...

Port 0 is probably not a good idea, just my .02

Your home, your router, right?  Have you entered your router's settings menu from a webpage (probably 192.168.1.1, but it could be different, you will have to login with admin and a password) and added the ability to SSH...you would have to open those ports...

The whole process for VNC (Remote Desktop, yes you have to use that) and SSH should be fairly easy...assuming you do these steps and have the right access

You set your local machines to accept the requests for these services, the VNC and the SSH...you check their LAN (Local area network) IPS (the 192...)

You then go to your router's settings, both work and home...pick ports (something better than 0 I would think...who knows what uses 0 though...)and you say, when someone dials my WAN (Wide area network, the 89...) and specifies this port...you then forward that request to X machine...SSH will probably already be preset and you just need to enable it, so if you don't need to vnc into a home machine, youll just need to get SSH enabled, probably with a checkbox or something similar...

So you will from the outside, vnc with 89.xxx.xxx.xxx:1234 and your router get that, sees the 1234, knows that's VNC and sends it to the right machine...

If you tell us the model of your router we could be of more service...you can PM me if you don't want Ip's and things like that listed around here :)

---

