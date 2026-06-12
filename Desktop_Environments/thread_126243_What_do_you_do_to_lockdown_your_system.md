---
title: "What do you do to lockdown your system?"
date: 2006-02-06
forum: Desktop Environments
---

### Post by ardchoille on 2006-02-06
I am a security freak and I don't like having my system open to intruders. That being said, here is a list of things I do after a fresh install to maintain some sense of security on my systems. I am also behind a router that does NAT.

sudo apt-get install firestarter
replace "Protocol 2,1" with "Protocol 2" in /etc/ssh/ssh-config
sudo apt-get install rkhunter
sudo rkhunter --update $$ sudo rkhunter --checkall --no-keypress
sudo apt-get install chkrootkit
sudo chkrootkit
sudo echo This is a private network > /etc/issue
sudo echo This is a private network > /etc/issue.net
edit /etc/X11/Xsession.options to remove ssh-agent
sudo killall ssh-agent
sudo echo ALL: 127.0.0.1 > /etc/hosts.allow
sudo echo ALL: PARANOID > /etc/hosts.deny
turn off all services except anacron, atd, cron, klogd, sysklogd and gdm
install and configure Tripwire

What do you do to maintain security for your system(s)?

EDIT: I just learned that editing /etc/X11/Xsession.options is better than doing "sudo mv /usr/bin/ssh-agent /usr/bin/ssh-agent-origin && killall ssh-agent"

---

### Post by alamba on 2006-02-06
Regularly run nmap internally and on the external interface and close any open ports. Run nessus in a timely fashion to make sure no blaring vulnerabilites are being advertised by my system. 

This is ofcourse in addition to some of the stuff u've mentioned.

A

---

### Post by nocturn on 2006-02-06
It depends on whether it is a Server or Client.

I do install firestarter on GUI machines.

Anyone know a good Iptables frontend for a server (no GUI)?  It's a simple server with one NIC on the internal LAN with a hw firewall between the LAN and the outside.

---

### Post by kosmic on 2006-02-06
[LIST=1]
[*]Encrypt all Partitions - Root , Home and Swap :)[/LIST]

---

### Post by alamba on 2006-02-06
nocturn - shorewall...via webmin.

Akshay

---

### Post by chris_andrew on 2006-02-06
Hi,

I use Bastille to set-up my security  

[http://www.bastille-linux.org/](http://www.bastille-linux.org/)

and Tiger to produce regular reports on security issues

[http://www.nongnu.org/tiger/](http://www.nongnu.org/tiger/)

On debian, these aree both in the standard repositories, so i'm guessing they're probably in Ubuntu, too.

With Bastille, it educates, too.  The first time I ran it, I locked my box down so tightly, it was almost unusable!!!  Luckily, there is an undo function :-)

Hope this helps,

Chris.

---

### Post by CharlieC on 2006-02-06
The problem I always run into with Firestarter is I can never get my home network to work. I have tried everything I know to allow it through the firewall. 
Obviously I dont know very much or it would work. 
Can anyone give me some suggestions.

Charlie

---

### Post by alamba on 2006-02-06
What are you trying at your home network? I have my desktop behave as a router and server (I get a ethernet interface from my ISP) with ubuntu and firestarter installed. I use firestarter as a firewall and in order to NAT my internal IP's to the ISP IP.

Akshay

---

### Post by CharlieC on 2006-02-06
I have a NAT router and two computers connected to it. One the XP and the other Ubuntu. All I really do is share files between the two machines. When Firestarter is on they will not connect. I have to turn it off in order for the network to work. I have it set for DHCP. I put in the IP range for my internal network and unchecked block traffic from internal network. ?????

Charlie

---

### Post by alamba on 2006-02-07
Not enough info. This is what I'm getting at, incase your XP machine has to go out to your ISP router and get back to access your ubuntu machine, this would probably fail in your case as it is. This might be because your ISP would be blocking some ports.

Incase your route/IP addressing is such, that u're connected to the router at your end via a hub and have private IP's via DHCP to your 2 machines then potentially you are only routing via your hub and it should work just fine once firestarter is set up to accept samba ports.

Akshay

---

### Post by CharlieC on 2006-02-07
I have both the XP and Ubuntu machines connected to a Linksys NAT router. The communicate fine without Firestarter, I do have a firewall in XP, Kerio. 
    When I turn on Firestarter, I can no longer communicate in either direction. 
    This is just a peer to peer networking situation. I can ping in both directions. If I recall correctly I set up the networking on the Ubuntu side with Samba.
    I hope that helps, it is really all I know.

Charlie

---

### Post by nocturn on 2006-02-07
You need to open the ports used by samba in firestarter.

By default, all incoming connections are blocked.

The easiest way is to open up the GUI, attempt the connection and allow those in the event tab.

---

### Post by CharlieC on 2006-02-08
Sorry again, I am a noob, I looked everywhere for an events tab and dont know what or where it is.

Charlie

---

### Post by byen on 2006-02-08
What nocturn meant was the events-tab in firestarter. What heppens is when the firewall has stopped an attempt to connect to your network from an outside source...the blue firstarter icon changes to red. And in order to see more information you> Right Click Firestarter in System Tray>Show Firestarter>Events tab>
Now, here you will see all the ip addresses from where an attempt has been made. if you know that the ip is from a pc you have..all you have to do is 
>Right click on the Ip address in the events tab> Allow Connections from source.

thats should solce your issue. Hope that helps. Goodluck!

---

### Post by awi on 2006-02-08
[QUOTE=kosmic][LIST=1]
[*]Encrypt all Partitions - Root , Home and Swap :)[/LIST][/QUOTE]

I use [COLOR="DarkGreen"]truecrypt[/COLOR] to protect my sensitive data.   I prefer Linux, but Windoze is a necessary disease, and this particular application, works on both plataforms. In fact, so far the volumes can only be created on windows, but it works really fast and is relatively ease to use.    Depending on the usage, IPsec might also be a must, for the network connections.

---

### Post by CharlieC on 2006-02-08
Thanks, I am getting a lot of stuff when I look at that. I think in time I can work it out now. I appreciate the help.

Charlie

---

