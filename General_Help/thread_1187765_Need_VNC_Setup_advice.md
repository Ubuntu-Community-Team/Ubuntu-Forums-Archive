---
title: "Need VNC Setup advice"
date: 2009-06-15
forum: General Help
---

### Post by Mattaus on 2009-06-15
Hi all,

Just a quick question...I have TightVNC for Windows and TightVNC for Unix/Linux. I intend on running the server from my Jaunty install, and access it via a client under Windows.

Do I need to mess around with this SSH stuff? I have read the wiki on it but am still not entirely sure. In fact will the cross platform access work? I'm assuming it will. 

I'm kind of hoping I can just install the program on each machine,configure the settings and then punch in the I.P and away I go...just like I have done in the past with 2 XP machines.

Like I said it is only a quick question, but some insight would be appreciated.

Cheers.

- Matt.

---

### Post by Scotty Bones on 2009-06-15
you shouldn't encounter any compatibility problems across the different platforms. SSH is not necessary, however VNC is not considered secure.  Your password is transmitted in plain text and is easily sniff-able by anyone who might be monitoring. Also, your connection is unencrypted which makes it susceptible to the same man-in-the-middle type of attack.  

So, while SSH is not necessary, it is highly recommended.

---

### Post by Mattaus on 2009-06-15
Oh, didn't think of it that way. Annoyingly I have found out most of what I need to know (Just after I posted this as well), but the small explanation of SSH is appreciated. I might get it setup without SSH first to make sure of a few things, and then once I've knocked over all my other problems (the list is long lol) I will come back to it.

Thanks for the reply.

---

### Post by Mattaus on 2009-06-15
Ok, ultra noob moment here...and very embarrassing considering I did a 3 day TCP/IP training course at work not less than 2 weeks ago.

The remote desktop server that comes with Ubuntu says that the IP address I need to use to connect to view the desktop on my local network is 10.1.1.5 - This seems strange to me.

Obviously it does not work - it just says failed to connect to server. The Ubuntu machine is wireless as is the laptop I am trying to connect from (10.1.1.3).

What incredibly stupid thing am I doing wrong here? It may be worth noting that I cannot see my laptop from ubuntu and vice versa.

Might look into that now actually!

---

### Post by Scotty Bones on 2009-06-15
You might be having port issue. Have you set port forwarding in your router config?  You will need to forward port 5900 to the IP address of the machine running the server, which of course means your server will need a static IP address.  

Is there any particular reason for using the Class A address range over the Class C?

---

### Post by Mattaus on 2009-06-15
> Is there any particular reason for using the Class A address range over the Class C?

Everything is the way it is, because its all still set to the defaults. I'll setup port forwarding tonight and assign static IP addresses for all my machines at the same time. (or rather before hand). Hopefully this will do the trick!

---

### Post by andersbk on 2009-06-16
> **Mattaus said:**
> Everything is the way it is, because its all still set to the defaults. I'll setup port forwarding tonight and assign static IP addresses for all my machines at the same time. (or rather before hand). Hopefully this will do the trick!

If the machines you want to access via VNC are behind a firewall, then the ONLY way to do it, IMHO, is to use SSH with tunneling.

Then, you open an ssh port through your firewall and tunnel the VNC ports from the host to the client.

Are you familiar with this type of setup?

I would never open VNC ports to the public Internet.

.

---

### Post by Saghaulor on 2009-06-16
> **andersbk said:**
> If the machines you want to access via VNC are behind a firewall, then the ONLY way to do it, IMHO, is to use SSH with tunneling.

Then, you open an ssh port through your firewall and tunnel the VNC ports from the host to the client.

Are you familiar with this type of setup?

I would never open VNC ports to the public Internet.

.

I am in fact attempting to do just that, namely, tunnel VNC through ssh. However I am having trouble, some assistance is welcome.

I've connected via ssh doing the following
```
ssh -L 5900:localhost:5900 username@servername -p ####

```

From there however, I am not sure what to do.

---

### Post by Saghaulor on 2009-06-16
I think that I've figured it out. Finally!

After the above command, then I ran the following from my local machine, namely, not the server that I was trying to connect to.

```
vncviewer -compresslevel 9 -quality 0 localhost:5900
``` 

And viola, my desktop was broadcasted via VNC to my laptop.

The connection is unbearably slow however, I guess I'll just have to stick to the command line.

---

### Post by HermanAB on 2009-06-16
Howdy,

Please note that VNC is almost always the WRONG solution.

You can do everything you want using SSH only.  That is easier, works better and it is secure.  On Windows, use Xming and Putty (or Cygwin).

Systems with VNC are notorious for getting hacked in no time.  Almost every hack complaint on these forums can be traced back to VNC.

---

### Post by Mattaus on 2009-06-16
But can SSH be used for graphical interaction?

I'm sort of lost so I think i will have a fair bit of reading to do here. I may end up leaving this until I have everything else on my system working exactly the way I want it, and then tinkering...

EDIT:

> If the machines you want to access via VNC are behind a firewall, then the ONLY way to do it, IMHO, is to use SSH with tunneling.

Then, you open an ssh port through your firewall and tunnel the VNC ports from the host to the client.

Are you familiar with this type of setup?

I would never open VNC ports to the public Internet.

Not familiar (obviously :p) is there a good resource somewhere that I can go look at for setting up a VNC connection through SSH? I have a few bookmarks but it is pretty tough to follow. As it stands I cannot even see the ubuntu machine on the network at all from my windows box - but I have not spent anytime investigating that problem yet as I have been so busy with everythign else.

---

### Post by bodhi.zazen on 2009-06-16
> **Mattaus said:**
> But can SSH be used for graphical interaction?

yes. You forward X via ssh.

from the command line you ssh -X user@server.

from windows use putty, specify X forwarding. On windows you need XMing.

once you connect you have a terminal. Start your command in the terminal and it will run on the server and output to your local computer.

VNC over ssh is very easy. Basically establish your ssh connection, then on the vnc clinet point it to localhost.

[http://martybugs.net/smoothwall/puttyvnc.cgi](http://martybugs.net/smoothwall/puttyvnc.cgi)

[http://members.shaw.ca/nicholas.fong/vnc/](http://members.shaw.ca/nicholas.fong/vnc/)

---

### Post by Chris Musampa on 2009-06-16
Freenx beats vnc for me, works acceptably over slow internet connections as well. I use it to access my home kubuntu box from my windows machine at work.
[https://help.ubuntu.com/community/FreeNX](https://help.ubuntu.com/community/FreeNX)

---

### Post by Mattaus on 2009-06-16
I have Ubuntu now setup as a Virtual Machine on my windows laptop if that possibly makes things any easier?

I most likely try out the [http://members.shaw.ca/nicholas.fong/vnc/](http://members.shaw.ca/nicholas.fong/vnc/) guide as it does not use that smoothwall stuff which got me confused. If I set this up so that I can access the HTPC from basically anywhere, will it still work in exactly the same manner if I do it from the same network as the HTPC? (A home wireless network)

---

### Post by AboveTheLogic on 2009-06-16
> **Mattaus said:**
> Hi all,

Just a quick question...I have TightVNC for Windows and TightVNC for Unix/Linux. I intend on running the server from my Jaunty install, and access it via a client under Windows.

Do I need to mess around with this SSH stuff? I have read the wiki on it but am still not entirely sure. In fact will the cross platform access work? I'm assuming it will. 

I'm kind of hoping I can just install the program on each machine,configure the settings and then punch in the I.P and away I go...just like I have done in the past with 2 XP machines.

Like I said it is only a quick question, but some insight would be appreciated.

Cheers.

- Matt.

I haven't read through this whole thread yet, but if you want to stick with VNC and not have to worry too much about its insecurities, definetely do it through SSH.

First things first:
Get into your router, [forward port 22]("http://techysteve.blogspot.com/2009/05/internet-security-firewalls-and-ports.html") to the IP of the machine you want to access. That machine should have a static IP set that is outside of the DHCP range of the router.

If you do not know the IP address of the router, try ipconfig/all in windows and look at the default gateway. In linux the only thing I can think of is something like tracert yahoo.com - the first IP might be the router.

If you do not know the password, you can use the reset button on the router, but be ready to set everything up again.

Once you have port forwarding working properly, test it using your external IP:

[http://www.whatismyip.com](http://www.whatismyip.com)

You can test it simply by using the command "ssh <IP>", if you get a login, the networking part is completed.

If you have a dynamic IP, you should use [dynamic DNS]("http://techysteve.blogspot.com/2009/06/networking-dynamic-dns-dynamic-vs.html") so that you don't have to worry about the IP changing on you.

Once you have SSH working, set a client-to-server rule to get to port 5900 on your home machine (once you get to this point, if you need help, just ask).

I recommend Tunnelier as a windows client, PuTTY works well too.

---

### Post by Mattaus on 2009-06-16
I know I'm going to get stuck on something trivial but google is my friend ;)

Hopefully I will make some headway tonight.

---

