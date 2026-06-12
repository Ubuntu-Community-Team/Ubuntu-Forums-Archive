---
title: "Remote from One linux machine into another linux machine ?"
date: 2009-03-10
forum: General Help
---

### Post by Nano_ext3 on 2009-03-10
Hi,

I have a slight predicament.  I used port 21/22 for my SFTP server, so I can remotely obtain material from my server via virtual paths.  Now I want to also remote into my Ubuntu linux box when away, but since I already have port 22 going to my xxx.xxx.1.25 machine running the SFTP server, how can this be accomplished.  I heard of UltraVNC, but I was under the impression that that program was for windows :P

Can anyone help?

Cheers,

-Nano

---

### Post by GCoffee on 2009-03-10
In one of the menus (not sure which im writing from vista) there is a option called remote screen something, possibly viewing, in the options menu of it you can set your pc to act as a VNC server.

On another linux box you can go to the same option to view it, or on windows you can download tightVNC and still view it.

If you plan to do this from outside your LAN (Home wire(less) network then you will need to forward VNC ports, not sure what they are though.

GCoffee.

---

### Post by MiguelS. on 2009-03-10
Hi, do you want to be able to see the screen on your linux box?

If so you have two options,
1) (recommended) Use ubuntu's own screen sharing. (Go to System->Remote Desktop) You can change the port to anything that suits you under the advanced tab. You can connect to a remote desktop using Remote Desktop Viewer. This actually uses VNC (I think) so you could potentially connect from a windows machine using UltraVNC or TightVNC.
2)You could also give a try to [NX]("http://www.nomachine.com/download.php"), but I don't know how to install it or set it up.

Finally, if you just want good old ssh, you could also change the listening port. [These instructions]("https://help.ubuntu.com/7.04/server/C/openssh-server.html") are a bit outdated, but they should do (first example under configuration).

Hope that helps,
MiguelS.

---

### Post by Nano_ext3 on 2009-03-10
Well, how can this be accomplished when im NOT on my local LAN (which works fine), Instructions on server side, and client side please???

---

### Post by bodhi.zazen on 2009-03-10
Change the port of your ssh server to a higher random port , like 4444 or what have you, then tunnel VNC over ssh.

Edit /etc/ssh/sshd-config, change the port, restart the ssh server, forward the new port from your router to the server ...

[http://martybugs.net/smoothwall/puttyvnc.cgi](http://martybugs.net/smoothwall/puttyvnc.cgi)

---

### Post by MiguelS. on 2009-03-10
That actually depends on the router you're using (assuming you're using a router...)

What I would do is to set the router to always give your linux box the same address (on my router this can be done without deactivating DHCP which is convenient for other devices). Then on the router's NAT configuration tool you have to set the ports to be forwarded to your machine. In the most basic case, it would suffice with specifying the ports (5900 for Ubuntu's remote desktop connection) and the (fixed) ip of your linux machine.

Unfourtunately, these steps are router dependant, so I cannot be more precise. [Here's]("http://portforward.com/routers.htm") a webpage that can help you with that.

On the client side everything should work without configuration.

Good luck!

---

### Post by Nano_ext3 on 2009-03-10
Haha, bodhi.zazen, I JUST did that, changed it to 2233.  Just got to get my roommate to give me the router password, as I forget what it is.  I have to wait until I get back to college :(

This method I can only SSH into my linux PC, but thats all I want to do anyway.

ssh xxx.xxx.xxx.xxx:2233 

That should do it?  I just want to pull up terminal on my laptop, and ssh into my desktop linux PC, so I can do some daily tasks while hours away from my local LAN network.  I should mention my server is a diff. IP than the regular "fun" linux box I use for gaming etc.

Thanks

-Nano

---

### Post by bodhi.zazen on 2009-03-10
ssh user@ip_address -p 2233

Use the -p flag to specify a port.

If you are on the LAN , use your LAN IP address (private address).

If you are connecting over the Internet, use the IP assigned by your IP provider (Public IP address).

---

