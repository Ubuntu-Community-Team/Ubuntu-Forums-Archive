---
title: "Unable to get filesharing working using NFS - please help."
date: 2005-05-27
forum: Desktop Environments
---

### Post by Sleeper Service on 2005-05-27
I've been searching these forums and trying different things for a few hours, but to no avail.

I've got a dektop PC running Warty and a Laptop running Hoary.  They're both networked via a network switch into which is also connected a smoothwall firewall (which brings in the broadband connection).

Both machines are using DCHP, and I've used ifconfig to find out which IPs they've been assigned.  At the moment, the desktop is 192.168.0.225, and the laptop is 192.168.0.224.

I've installed nfs-common and nfs-kernel-server on each machine.  Each machine has a /home/shared/ directory with permissions set to 777 (/home/ is 755).  And I've added something like the following to /etc/exports on each machine:
192.168.0.225     /home/shared(r,w)

But when I try mounting this from the other machine, I'm getting:
[FONT=Courier New]mount: 192.168.0.224:/home/shared failed, reason given by server: Permission denied[/FONT]

The command I'm using to mount with (each machine has a /mnt/[other-machine-hostname] directory) is:
[FONT=Courier New]mount -t nfs 192.168.0.224:/home/shared /mnt/[other-machine-hostname][/FONT]

I don't know what I'm doing wrong or what else I can try...

---

### Post by f.prisson on 2005-05-27
You have to type the address of the peer machine in that way:```
/mnt/share  192.168.x.x(rw)
``` Also if you use DHCP, make sure that your computers receive the same address everey time.

You also have to mount your shares always with the address of the peer

---

### Post by Sleeper Service on 2005-05-27
[quote=f.prisson]You have to type the address of the peer machine in that way:```
/mnt/share  192.168.x.x(rw)
```[/quote]
Sorry - I made a typo above.  This is just the format I've been using.

With the laptop (running Hoary) I even used System > Administration > Shared Folders to allow any hosts in the eth0 network (at least I think that's what it means?!).  The laptop's /etc/exports now reads:
```
/home/shared/     192.168.0.0/255.255.255.0(rw)
```
But still no luck.

> Also if you use DHCP, make sure that your computers receive the same address everey time.
I thought I'd at least check that nfs is working and I can mount other PCs' directories first - then later I was going to work out how to configure smoothwall to dish out specific IP addresses based on each machine's mac address.

I ought to be able to do it in a temporary, once-per-machine-session kind of a way before that, oughtn't I?

---

### Post by f.prisson on 2005-05-27
> I ought to be able to do it in a temporary, once-per-machine-session kind of a way before that, oughtn't I? That's the best way to find errors before implementation, you are right.

You seem to do everything correct. Is the error message still "permission denied"?

---

### Post by Sleeper Service on 2005-05-27
It is, I'm afraid.  Puzzling, isn't it?  :?

---

### Post by rmjokers on 2005-05-27
I seem to remember that you have to be running portmap (/etc/init.d/portmap start) to get NFS to work.  I have no way of testing this but you might try it out.

---

### Post by stepore on 2005-05-27
[QUOTE=Sleeper Service]
Both machines are using DCHP, and I've used ifconfig to find out which IPs they've been assigned.  At the moment, the desktop is 192.168.0.225, and the laptop is 192.168.0.224.
[/QUOTE]

i'm no networking guru, but isn't .225 a broadcast address? you're not supposed to give that addresss out to any node on a network. unless you have a funky router or DHCP server.

---

### Post by alastair on 2005-05-27
.225 is fine as a host IP.

On the NFS server :

I have in my /etc/exports :

/server         192.168.0.0/24(rw,sync)

I also have in my /etc/hosts.allow :

mountd: 192.168.0.0/24
portmap: 192.168.0.0/24

Could the problem be tcpwrappers?

---

### Post by sbassett on 2005-05-31
Also verify that portmap is actually installed. I went through an hour of adjusting all firewall settings on my network before taking a guess and running apt-get portmap. After that, everything was fine, except for my pride. The simplest thing cause the most frustration.

---

### Post by Gtaylor on 2005-06-06
I'm getting the same error message as well:
> 
gtaylor@gislinux1:/etc/init.d$ sudo mount -t nfs -v gisweb.ath.cx:/home/gisweb /home/gtaylor/gisweb
mount: gisweb.ath.cx:/home/gisweb failed, reason given by server: Permission denied

When I try to start nfs-common I get this in my /var/log/syslog
> 
Jun  6 17:03:24 localhost rpc.statd[11110]: Version 1.0.6 Starting
Jun  6 17:03:24 localhost rpc.statd[11110]: Opening /var/run/rpc.statd.pid failed: Permission denied


---

### Post by nocturn on 2005-06-07
On Warty, there was a howto in the wiki to make NFS work.

Reason was that Ubuntu has portmap bind to the loopback interface (127.0.0.1) only for security reasons.

The page is here:
[http://www.ubuntulinux.org/wiki/NFSServerHowTo/view?searchterm=nfs](http://www.ubuntulinux.org/wiki/NFSServerHowTo/view?searchterm=nfs)

> 
By default, the portmap service is only accessible on the local system. For NFS service to work, access must be allowed from NFS clients as well. Edit the file /etc/default/portmap and remove the -i 127.0.0.1 option from ARGS


---

