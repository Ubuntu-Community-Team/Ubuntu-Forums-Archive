---
title: "xdmcp in 10.04"
date: 2010-05-03
forum: Desktop Environments
---

### Post by e_defranco on 2010-05-03
Hi, 

I have just installed the new version 10.04 of xubuntu but I cannot enable xdmcp.

1) the gdm.conf (usualy in /etc/gdm/) is missing (where is now this file?);
2) the custom.conf apparently don't work;
3) the remote tab in login windows are missing

Please there are some people that can help me ?

Thank in advance,

Emilio

---

### Post by e_defranco on 2010-05-04
Auto answer (sic) !!!

Partialy resolved
=================

xdmcp work if you setup /etc/gdm/custom.conf as follow:

[daemon]
User=gdm
Group=gdm


[security]
DisallowTCP=true

[xdmcp]
Enable=true
DisplaysPerHost=2
HonorIndirect=false
MaxPending=4
MaxSessions=16
MaxWait=30
MaxWaitIndirect=30
PingIntervalSeconds=60
Port=177

[greeter]

[chooser]
Multicast=false

[debug]
Enable=false 

I have also activated vnc4server.

But, for some strange reason I cannot connect to my pc with a Xming (all working fine if I connect my pc from another linux box with xserver).

When I try to connecnt my 10.04 linux box with xming the xming crash !!!

But if  i connect whit the same pc and the same xming client to another xubuntu 8.04 all working fine ... 

I suspect that the problem is the new gdm 2.30 ... I am reading that there is no interrest to resolve old problem inside the gdm package related to xdmcp ...

If other people have other ideas about xming crash ... I am here :-)

Emilio

---

### Post by e_defranco on 2010-05-04
Ok, all working fine upgrading xming to the version 6-0-9-31

Emilio

---

### Post by cszikszoy on 2010-05-05
Thank you very, very much!  Works perfectly.

---

### Post by iron_horseman on 2010-05-21
Wow that solution worked pretty good for me too, but how secure is it?

---

### Post by Kangarooo on 2010-06-02
Would there be later a gui way to do it?

---

### Post by vasm on 2010-08-07
> **e_defranco said:**
> Auto answer (sic) !!!

Partialy resolved
=================

xdmcp work if you setup /etc/gdm/custom.conf as follow:

[daemon]
User=gdm
Group=gdm


[security]
DisallowTCP=true

[xdmcp]
Enable=true
DisplaysPerHost=2
HonorIndirect=false
MaxPending=4
MaxSessions=16
MaxWait=30
MaxWaitIndirect=30
PingIntervalSeconds=60
Port=177

[greeter]

[chooser]
Multicast=false

[debug]
Enable=false 

I have also activated vnc4server.

But, for some strange reason I cannot connect to my pc with a Xming (all working fine if I connect my pc from another linux box with xserver).

When I try to connecnt my 10.04 linux box with xming the xming crash !!!

But if  i connect whit the same pc and the same xming client to another xubuntu 8.04 all working fine ... 

I suspect that the problem is the new gdm 2.30 ... I am reading that there is no interrest to resolve old problem inside the gdm package related to xdmcp ...

If other people have other ideas about xming crash ... I am here :-)

Emilio

Hello!
I did the same actions with my Ubuntu 10.04 system, and even rebooted it. But XDMCP is apparently not working normally. Here is the output of the netstat utility:
```

root@server:~# netstat -atnup | grep 177
udp6       0      0 :::177                  :::*                                4146/gdm-binary 

```
There is no IPv6 protocol in my network. How do you turn IPv4 listening on your system?

---

### Post by jmagilto on 2010-08-22
Thanks! This was perfect! ;)

---

### Post by semidark on 2010-10-27
Hi Vasm,

had the same problem with ipv6 and GDM. 

I disabled IPv6 via the Kernel Boot Parameters:

I added "ipv6.disable=1" to the Config Line GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" in /etc/defaults/grub.

```
$ grep -i ipv6 /etc/default/grub 
GRUB_CMDLINE_LINUX_DEFAULT="ipv6.disable=1 quiet splash"
```Then updated grub via the command "sudo update-grub" and rebooted.

Now gdm listens on the UDP in IPv4.

```
$ sudo netstat -tuanp |grep gdm
udp        0      0 0.0.0.0:177             0.0.0.0:*    607/gdm-binary
``` :)


Semidark

---

### Post by ls_venkat on 2011-04-16
Install XDM and configure xdm-config. Gdm will not work for Xdmcp in 10.04 LTS

---

