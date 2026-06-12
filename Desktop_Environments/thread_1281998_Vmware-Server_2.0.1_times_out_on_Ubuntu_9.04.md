---
title: "Vmware-Server 2.0.1 times out on Ubuntu 9.04"
date: 2009-10-03
forum: Desktop Environments
---

### Post by tomrue on 2009-10-03
Last night I installed VMware-server-2.0.1-156745.i386 on Ubuntu 9.04 behind a Linksys WRT54GS router. 

Vware It seemed to be working okay last night, to the extent that I was able to create a VM. However, the console window was quite small, which I thought might be related to the absence of VM Tools. After some googling, I ran 

*wget [http://chrysaor.info/scripts/](http://chrysaor.info/scripts/)[I]ubuntu904vmtools*.*sh*[/I]

which seemed to go successfully. 

However, since then, I have be getting time-outs with a white screen while waiting for the VMware Authorization Service service to connect, with the word "Loading..." in the title bar at the top. I left it that way for several hours today, with no change.

*tail /var/log/vmware/hostd.log says...*[INDENT][FONT=Courier New]root@Persephone:/home/tom# tail /var/log/vmware/hostd.log[/FONT]
[FONT=Courier New][2009-10-03 20:01:59.890 'Proxysvc Req00000' 3064597392 warning] PendingServerStrm: client write-completion error: SSL Exception: error:00000001:lib(0):func(0):reason(1)[/FONT]
[FONT=Courier New][2009-10-03 20:01:59.958 'Proxysvc Req00004' 3064597392 warning] PendingServerStrm: client write-completion error: SSL Exception: error:00000001:lib(0):func(0):reason(1)[/FONT]
[FONT=Courier New][2009-10-03 20:02:00.003 'Proxysvc Req00001' 3064597392 warning] PendingServerStrm: client write-completion error: SSL Exception: error:00000001:lib(0):func(0):reason(1)[/FONT]
[FONT=Courier New][2009-10-03 20:03:36.664 'Proxysvc' 3065658256 warning] SSL Handshake on client connection failed: SSL Exception: [/FONT]
[FONT=Courier New][2009-10-03 20:03:40.210 'Proxysvc' 3066452880 warning] SSL Handshake on client connection failed: SSL Exception: [/FONT]
[FONT=Courier New][2009-10-03 20:03:42.245 'Proxysvc' 3070405520 warning] SSL Handshake on client connection failed: SSL Exception: error:1407609C:SSL routines:SSL23_GET_CLIENT_HELLO:http request[/FONT]
[FONT=Courier New][2009-10-03 20:03:43.556 'Proxysvc' 3067247504 warning] SSL Handshake on client connection failed: SSL Exception: error:1407609C:SSL routines:SSL23_GET_CLIENT_HELLO:http request[/FONT]
[FONT=Courier New][2009-10-03 20:03:48.334 'Proxysvc Req00006' 3065658256 warning] PendingServerStrm: client write-completion error: SSL Exception: error:00000001:lib(0):func(0):reason(1)[/FONT]
[FONT=Courier New][2009-10-03 20:03:48.541 'Proxysvc Req00007' 3064597392 warning] PendingServerStrm: client write-completion error: SSL Exception: error:00000001:lib(0):func(0):reason(1)[/FONT]
[FONT=Courier New][2009-10-03 20:03:55.444 'Proxysvc' 3065125776 warning] SSL Handshake on client connection failed: SSL Exception: [/FONT]
[/INDENT]Invoking *vmware *at a console, says...[INDENT][FONT=Courier New]tom@Persephone:~$ vmware
Launching VMware Web Access using /usr/bin/xdg-open[/FONT]
[/INDENT]I still with the same white screen in the Firefox interface.

*tail etc/hosts* says...[INDENT][FONT=Courier New]tom@Persephone:~$ tail /etc/hosts[/FONT]
[FONT=Courier New]127.0.0.1    localhost[/FONT]
[FONT=Courier New]127.0.1.1    Persephone[/FONT]
[/INDENT][INDENT][FONT=Courier New]# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts[/FONT]
[/INDENT]Any suggestions on how to resolve this would be most appreciated. I'm fairly new to VMware, so please be gentle. 

Many thanks and best wishes,
Tom


--
[http://tomrue.net](http://tomrue.net) | tomrue AT gmail.com

---

### Post by eombah on 2009-11-08
Hi Tom,

I'm running into the same problem with Karmic and VMWare Server.
Did you solve your problem?

-Bart

---

### Post by devastator on 2009-11-16
Same problem here with 9.10.
Anyone found a solution ?

---

