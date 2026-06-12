---
title: "Cisco vpn on ubuntu"
date: 2006-06-05
forum: Desktop Environments
---

### Post by mathiraj on 2006-06-05
I'm using cisco vpn "4.8" on ubuntu 6.06. I'm able to connect to my work, access the network and do stuff.

After a few minutes of using vpn, I'm not able to access any system in the company's network by their hostname but i'm able to access the systems only using IP address

i.e.,
ping hostname doesn't work
ping IP address works

I previously had fedora core 5 and things worked fine on it.
Anyone knows any ways to fix this?

thanks 'n advance....

---

### Post by t0mc4t on 2006-06-05
Sorry for different issue..
But I have problem installing the vpn client on Ubuntu..
Would you please tell me how did you install it?
Thank you..

---

### Post by aysiu on 2006-06-05
mathiraj, no idea. I wish I could help.

t0mc4t, what you need to do is install the header files for your kernel and the appropriate packages for building from source.

In Synaptic (or Adept), search for the word *headers* and mark for installation the appropriate ones for your kernel. Also, mark the *build-essential* package for installation. Then, if the installer file is called vpn_install, then go to the directory and run the command (most likely it'll look something like this): ```
cd ~/Desktop/vpnclient
chmod +x vpn_install
sudo ./vpn_install
```

---

### Post by meng on 2006-06-05
I have a tiny bit of experience, having tried the Cisco VPN client. Firstly let me say that while it worked, I had equal success with vpnc. Mathiraj, your problem (recognizes IPs but not textnames) sounds like you need to specify the DNS. vpnc detected the DNS automatically, IIRC.

---

### Post by t0mc4t on 2006-06-06
[QUOTE=aysiu]mathiraj, no idea. I wish I could help.

t0mc4t, what you need to do is install the header files for your kernel and the appropriate packages for building from source.

In Synaptic (or Adept), search for the word *headers* and mark for installation the appropriate ones for your kernel. Also, mark the *build-essential* package for installation. Then, if the installer file is called vpn_install, then go to the directory and run the command (most likely it'll look something like this): ```
cd ~/Desktop/vpnclient
chmod +x vpn_install
sudo ./vpn_install
```[/QUOTE]


Thanks... I'll try it...

---

### Post by dudus on 2006-06-06
Just for information:
OpenVPN probably will be very well integrated to Edgy.It has been discussed on devel list

---

### Post by t0mc4t on 2006-06-06
I have some problem here..
I have installed the vpn_client... But when I tried to run it
sudo ./vpnclient connect myProfile
it shows an error :

[I]Cisco Systems VPN Client Version 4.8.00 (0490)
Copyright (C) 1998-2005 Cisco Systems, Inc. All Rights Reserved.
Client Type(s): Linux
Running on: Linux 2.6.15-23-386 #1 PREEMPT Tue May 23 13:49:40 UTC 2006 i686
Config file directory: /etc/opt/cisco-vpnclient

Could not attach to driver. Is kernel module loaded?
The application was unable to communicate with the VPN sub-system.[/I]

I have copied myProfile into /etc/opt/cisco-vpnclient/Profiles.  Any idea why did it happen?

---

### Post by t0mc4t on 2006-06-06
When I try to run
sudo /etc/init.d/vpnclient_init start

it produce an error too.. it's said
[I]Starting /opt/cisco-vpnclient/bin/vpnclient: insmod: error inserting '/lib/modules/2.6.15-23-386/CiscoVPN/cisco_ipsec.ko': -1 Invalid module format
Failed (insmod)[/I]

Em... confusing... :(

---

### Post by t0mc4t on 2006-06-06
Please ignore my previous posting...
It's working now...
I installed the 686 headers which was wrong. I should install the 386 headers.. :)

---

### Post by mathiraj on 2006-06-06
> Mathiraj, your problem (recognizes IPs but not textnames) sounds like you need to specify the DNS. vpnc detected the DNS automatically, IIRC.

meng, thanks for your reply.

do I need to setup the DNS manually? doesn't vpn do it? i'm wondering then how come I was able to ping systems by hostname for the first few minutes of using vpn

---

### Post by meng on 2006-06-06
I think the Cisco client is supposed to do it. Can you post the contents of your /etc/resolv.conf, while the client is running?

---

### Post by Melvil on 2006-06-06
Why don't you just use *vpnc*? It works fine. The only thing you need to do is to decrypt the group password in the .pcf profile, you can then use vpnc as a substitute for the original cisco client.

---

### Post by mathiraj on 2006-06-06
hi meng,

thanks for your reply.

my /etc/resolv.conf points to the correct dns entries. I also have a search pattern to search systems from different domains. the dns entries are IP addresses and not hostnames and i can ping the dns IP Addresses.... but still, after vpn connect, i can ping the systems only with their IP addresses 

On a related note, i just installed ubuntu on one of the systems at work. Here too I can't ping the systems just by their hostnames. I need to use the full hostname+domainname to ping them even though I have a search pattern to search the domainname. But atleast at work, i can use the hostname+domainname and not the IP Address.

---

### Post by mathiraj on 2006-06-06
[QUOTE=Melvil]Why don't you just use *vpnc*? It works fine. The only thing you need to do is to decrypt the group password in the .pcf profile, you can then use vpnc as a substitute for the original cisco client.[/QUOTE]
Melvil,

thanks for you reply.

I get your point. But i'm not an experienced vpn user and won't be able to fix anything if I run into any problem.

---

### Post by phace on 2006-06-06
Are you sure that your /etc/resolv.conf is pointing to the dns servers inside your network ? I am using Cisco VPN client as well but I have no issues. My /etc/resolv.conf is pointing to the nameservers and I can ping normally.

predrag@cartmanland:~$ ping dementia.servers.localdomain
PING dementia.servers.localdomain (192.168.1.4) 56(84) bytes of data.
64 bytes from dementia.servers.localdomain: icmp_seq=1 ttl=252 time=8.53 ms

--- dementia.servers.localdomain ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms

predrag@cartmanland:~$ cat /etc/resolv.conf
# BIHnet provider DNS
nameserver 195.222.32.10
nameserver 195.222.32.20

# Company DNS
nameserver 192.168.1.232
nameserver 192.168.5.232

---

### Post by mathiraj on 2006-06-06
[QUOTE=phace]Are you sure that your /etc/resolv.conf is pointing to the dns servers inside your network ?[/QUOTE]
yes, i'm very sure they point to the dns server inside the network. In fact the same values work on my other system which has fedora core 5.
>  I am using Cisco VPN client as well but I have no issues. My /etc/resolv.conf is pointing to the nameservers and I can ping normally.
I too can ping the dns servers using their IP addresses and other systems with their IP Addresses.
For the first 5 minutes of connecting via vpn, I'm in fact able to ping all the systems with this (hostname+domainname)'s
After 5 minutes I can only ping the systems with their IP Addresses and not with thier hostnames or hostname+domainnames and that's the problem I'm facing.
> predrag@cartmanland:~$ ping dementia.servers.localdomain
PING dementia.servers.localdomain (192.168.1.4) 56(84) bytes of data.
64 bytes from dementia.servers.localdomain: icmp_seq=1 ttl=252 time=8.53 ms

--- dementia.servers.localdomain ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms

predrag@cartmanland:~$ cat /etc/resolv.conf
# BIHnet provider DNS
nameserver 195.222.32.10
nameserver 195.222.32.20

# Company DNS
nameserver 192.168.1.232
nameserver 192.168.5.232

---

### Post by meng on 2006-06-06
I'm not sure of the answer, mathiraj. Cisco VPN client just worked for me. (Then again, so did vpnc.) Your resolv.conf suggests that the DNS is recognized. Did you try turning off your firewall?

---

### Post by phace on 2006-06-07
[quote=mathiraj]
I too can ping the dns servers
[/quote]

I can ping every computer/server by IP and by name.

---

### Post by valnar on 2006-06-07
[QUOTE=Melvil]Why don't you just use *vpnc*? It works fine. The only thing you need to do is to decrypt the group password in the .pcf profile, you can then use vpnc as a substitute for the original cisco client.[/QUOTE]

I never quite understood why there was a free alternative.  The official Cisco client works fine.  If a company has a VPN Concentrator, then the client is freely available.  If you don't have a Cisco concentrator (or router, or PIX) to connect to, then having a free alternative like VPNC is pointless.

Sorry, just thinking out loud.  I love and support OSS, but never understood this one.  :confused: 

-Robert

---

### Post by WrathofthePenguin on 2006-06-07
Well, it's not really a "free alternative". It's a free VPN client. There are LOTS of VPN endpoint devices out there, and lots of reasons to use different VPN clients. Some of the endpoint devices are consumer products (like a home router) and others are enterprise products. VPN client programs don't often coexist well - sometimes one will prevent the other from running correctly or even installing. If you have a VPN endpoint, the client is not always free. Many times you have to have a support contract in place to download the client. If you are a small business or a home user, would you rather use a free client or pay for a support contract?


[QUOTE=valnar]I never quite understood why there was a free alternative.  The official Cisco client works fine.  If a company has a VPN Concentrator, then the client is freely available.  If you don't have a Cisco concentrator (or router, or PIX) to connect to, then having a free alternative like VPNC is pointless.

Sorry, just thinking out loud.  I love and support OSS, but never understood this one.  :confused: 

-Robert[/QUOTE]

---

### Post by mathiraj on 2006-06-07
[QUOTE=meng]I'm not sure of the answer, mathiraj. Cisco VPN client just worked for me. (Then again, so did vpnc.) Your resolv.conf suggests that the DNS is recognized. Did you try turning off your firewall?[/QUOTE]

thanks once again for your reply meng and thanks a lot to all those who replied.

yes, firewall is turned off on the system.

---

### Post by mathiraj on 2006-06-15
hello all,

sorry, it took a while for me to get back..... back to the topic now.

Yesterday I installed ubuntu on a office laptop and tried vpn again. Ubuntu runs fine though the laptop is only 400MHz with 256 MB RAM :)

This is what I noticed.

Once vpn connects to the office network, the name servers entries in /etc/resolv.conf points to the nameservers in the office. Everything works fine.

I just opened up firefox and typed google.com. Firefox doesn't have any proxy. I noticed that firefox was able to load google.com. I was surprised how come firefox connects to the internet when vpn connection is on. So, I immediatly checked the resolv.conf. It points to my ISP's nameservers.

I can't ping any systems at work with their hostnames anymore.

resolv.conf changed to my ISP settings when I accessed internet with firefox. Sorry I didn't notice this earlier. So, i kept replying in my previous posts that resolv.conf points to the correct dns servers.

It all looks like some sort of puzzle to me. Now, has any one faced this behaviour? Any solutions? How to prevent the resolv.conf from changing to the ISP's dns server entries once vpn is active?

thanks a lot in advance.....

---

### Post by stillingen on 2006-06-16
[QUOTE=mathiraj]
It all looks like some sort of puzzle to me. Now, has any one faced this behaviour? Any solutions? How to prevent the resolv.conf from changing to the ISP's dns server entries once vpn is active?
[/QUOTE]

Have you looked at the set up of your vpn group on the Concentrator or PIX? Using both Cisco VPN 3000 and Cisco PIX VPN set up allows you to add entries like DNS for the specific vpn group which your user is a part of. It also allows you to tunnel only specific network ranges. 

I've installed the newest vpn client from Cisco, and it works nice. I do however have an issue with system hang. I not skilled enough to debug in Linux, so I'm not sure if it caused by the vpn client software or not, but I have a sneaky feeling it is. Anyone with hot tips on debug documentation/howto's?

When installing the vpn client, it asked you 'if you want to run at start up' .
If one answer yes, the service does not run when Ubuntu is up and running. 
I manually have to do a; sudo /etc/init.d/vpnclient_init start
How can I avoid this?

---

### Post by timbl on 2006-07-05
I am experiencing similar problems with resolv.conf. From what I can tell, the resolv.conf file is being replaced every time the DHCP lease is being renewed. Typically DHCP renews the lease at 1/2 the lease time.

So for a 24 hour lease one would expect that the lease would be renewed every 12 hours and there would be no issue here - except on rare occasions. 

The problem appears to be that Network manager is renewing the lease much more frequently then required. My log files indicate that the lease is renewed every 700 seconds or so, which gives about 10 minutes of vpn access before the resolv.conf is replaced.

At this time I don't have any solution, except to write some sort of script that will keep the vpn version of resolv.conf current.

---

### Post by mathiraj on 2006-07-06
[QUOTE=timbl]At this time I don't have any solution, except to write some sort of script that will keep the vpn version of resolv.conf current.[/QUOTE]

hi timbl,

thanks for the reply. I too wrote a script that would replace the ISP version of resolv.conf with vpn version every 15 sec  which helps me use vpn on ubuntu

Wonder what the actual solution to this problem would be. Disabling Network Manager? Will that work?

thanks
Mathi

---

### Post by flar on 2006-07-12
> **stillingen said:**
> 
When installing the vpn client, it asked you 'if you want to run at start up' .
If one answer yes, the service does not run when Ubuntu is up and running. 
I manually have to do a; sudo /etc/init.d/vpnclient_init start
How can I avoid this?

By default it only install init scripts to runlevels 3 4 and 5, ubuntu needs it to start in runlevel 2.
If you want it to start automatically type this:

sudo update-rc.d vpnclient_init defaults

---

### Post by thegnark on 2006-07-12
very strange problem you're getting. i'm also using the 4.8 cisco client, but i haven't run into any problems with it i don't see why any settings should change. the only thing that should go through the vnc are connections that would otherwise not resolve.

i've installed on my desktop and laptop and not had a single problem. sorry to hear about this one.


also, in reasponse to vpnclient_init not running on startup, i would expect you could go the route of simply adding a line to your startup programs list

---

### Post by metalheart on 2006-07-12
I had problem with connection 'dropping' using Cisco VPN Client (on Windows) using a router with 'packet filtering' turned on (3Com OfficeConnect in my case). Turning this option off solved problem.

---

### Post by ariel on 2007-04-13
Hi mathiraj, could you finally fix the problem? If still using the script, would you mind posting the script here? I have exactly the same problem, using cisco vpn client and edgy.

Thanks


> **mathiraj said:**
> hi timbl,

thanks for the reply. I too wrote a script that would replace the ISP version of resolv.conf with vpn version every 15 sec  which helps me use vpn on ubuntu

Wonder what the actual solution to this problem would be. Disabling Network Manager? Will that work?

thanks
Mathi

---

### Post by mathiraj on 2007-04-17
while [ 1 ]
do
        diff my_resolv.conf /etc/resolv.conf
        if [ $? != 0 ]
        then
                cp my_resolv.conf /etc/resolv.conf
        fi
        sleep 60
done
-------------------------------------------------------------------------------------

my_resolv.conf is the file that points to your work nameserver and domain names. I'm still using this script when ever i use cisco vpn to connect to my work.

---

