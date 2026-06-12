---
title: "please help cannot open ports."
date: 2009-06-06
forum: General Help
---

### Post by switch10 on 2009-06-06
I used to be able to make a connection through port 5900 for vnc with no problems at all.  It randomly stopped working yesterday (just like a lot of things in ubuntu in my experience) now i cant connect to my computer. and when I go to [http://www.yougetsignal.com/tools/open-ports/](http://www.yougetsignal.com/tools/open-ports/) it says the port (5900) is closed. my firewall and MoBlock are disabled.  all of the settings in remote desktop are unchanged since it worked last time.  

when i try to connect it says connection error, and it also says I have a firewall enabled (i disabled it).  when i add encryption it says "connection error could not create tunnel to 127.0.0.1."

Im getting really sick of Ubuntu.  It seems like im CONSTANTLY fixing or trying to fix little annoying problems like this.  My super key on my keyboard randomly stopped working the other day under Ubuntu as well.  After searching all day yesterday I still havent fixed it.  

I've been using Ubuntu, and just Ubuntu for the past 4 months or so, and im about to go back to XP.  At least it works fairly consistently.

p.s. sorry about the rant I'm just pissed that all of these things keep breaking.

Dave

---

### Post by The Cog on 2009-06-06
Are you trying to connect to your Ubuntu PC, or to connect from the Ubuntu PC to something else?

Assuming you are trying to connect to it, firstly have a look and see if it is listening on port 5900 with the command:
```
netstat -lnt
```
If it's not listening, you need to figure out why the VNC server isn't running. If it is listening, then the problem is in the network somewhere. This could be because the Ubuntu firewall is blocking it. I know you think it's disabled but check with the command ```
sudo itables -nvL
``` and make sure the output looks like this:
> Chain INPUT (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         



Are you trying to connect remotely? If so, check the router si still configured to forward port 5900 to your PC - has your PC changed IP address (supplied by the DHCP server)?

---

### Post by ajgreeny on 2009-06-06
When you say that you disabled the firewall, what exactly do you mean?  If you have been using firestarter or guarddog or even ufw, and then just either uninstall them or stop using them, it does not mean that the firewall configuration you set up using it has now gone back to the default.

The actual firewall in ubuntu is iptables and having configured it in some way you will need to flush the settings you made which is most easily done in the terminal with
```
sudo /etc/init.d/firestarter stop 
sudo /etc/init.d/guarddog stop 
sudo iptables -F 
sudo dpkg -P firestarter guarddog 
sudo /etc/init.d/networking restart

```The first two commands will stop either firestarter or guarddog from running, so may not be needed.  The third command flushes the iptables config back to the default, ie empty, the forth purges firestarter from your system if you still have it and don't want to keep it, and finally the fifth command restarts networking to use the new configuration.

If all this is un-needed and not appropriate to your situation, just ignore it, but many users just don't seem to understand the firewall system in ubuntu, so I thought it worth offering this information.

---

### Post by switch10 on 2009-06-06
im trying to control my desktop from my IPhone using an app called Jaadu vnc.  And it has always worked before with no problems what so ever.  

here is the output from the netstat -lnt
dave@dave-laptop:~$ netstat -lnt
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 0.0.0.0:6881            0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:21              0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN     
tcp6       0      0 :::6881                 :::*                    LISTEN     
tcp6       0      0 ::1:5900                :::*                    LISTEN     
tcp6       0      0 :::22                   :::*                    LISTEN   

So it is listening right?

this is what i get from the iptables -nvL command.  This is after I thought i disabled the ufw firewall using sudo ufw disable.  

dave@dave-laptop:~$ sudo iptables -nvL
Chain INPUT (policy ACCEPT 376 packets, 209K bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 433 packets, 437K bytes)
 pkts bytes target     prot opt in     out     source               destination 

I dont want to have to uninstall my software firewall to get this to work.  I just dont understand why it all of a sudden stopped working.  What should I do?

P.S. ifconfig says my ip address is the same

---

### Post by switch10 on 2009-06-07
bump.  does anyone know how to fix this?

---

### Post by Brandon Williams on 2009-06-07
For some reason, vnc is only listening for IPv6 connections, not IPv4. That what the 'tcp6' means. First, turn off the current vnc server session, then run the netstat command to make sure that there is no longer any indication that your machine is listening on port 5900, and then start the vnc server again. Is it listening on port 5900 for both 'tcp' and 'tcp6' now?

---

### Post by The Cog on 2009-06-07
No it is not listeniing right. It it listening on ::1:5900 which is the PCs loopback port. Other computers will not be able to connect to it, it can only accept connections from itself. It should be listening on either **:::5900** or on **0.0.0.0:5900**. So there is a problem with the configuration of the VNC server. How do you configure and start the VNC server process?

P.S. Your firewall is succesfully disabled.

---

### Post by switch10 on 2009-06-07
COG you're the man!!  I had the only allow local connections checked under advanced in the remote desktop settings.  I don't remember changing this, but it works like a charm now.  Thanks a lot!

---

