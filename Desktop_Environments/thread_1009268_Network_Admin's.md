---
title: "Network Admin's"
date: 2008-12-12
forum: Desktop Environments
---

### Post by moviewithnotitle on 2008-12-12
Hi all,
Any Network Administrators out there? I use Ubuntu mostly at work and have installed a few programs for networking in a Corporate environment, but I was curious to know what others are using for Desktops and programs. 

Anyone in a similar situation, Please share. 

MWNT

---

### Post by Rudy507 on 2008-12-12
I'm not a Network Admin by any means. However, I would like to be one someday... and I work do work as a student in our Technology Services department. We've got a Windows environment right now running Active Directory here at the school. I've been assigned the task of setting up a guinea pig Ubuntu desktop, as we are trying to think of ways in cutting costs. In addition to the IBMs that we have in the student labs, we've got mainly Dell workstations for the faculty and staff. We also have a Mac lab for our Art / Graphics Design department. 

Another guy and myself in Technology Services are working on this Ubuntu machine, and we've got Microsoft Office running almost flawlessly under Wine on Ubuntu 8.10. It wouldn't surprise me if we started migrating people over sometime in the next year. Of course, I graduate in the spring, so I may miss all of the excitement!

---

### Post by iponeverything on 2008-12-12
> **moviewithnotitle said:**
> Hi all,
Any Network Administrators out there? I use Ubuntu mostly at work and have installed a few programs for networking in a Corporate environment, but I was curious to know what others are using for Desktops and programs. 

Anyone in a similar situation, Please share. 

MWNT


traceroute, ping, nmap, nslookup, tcpdump, perl, expect, etc. etc.

---

### Post by moviewithnotitle on 2008-12-12
> **iponeverything said:**
> traceroute, ping, nmap, nslookup, tcpdump, perl, expect, etc. etc.

I already know those, I was curious about sniffer prgms, graphing prgms, SNMP trap prgms, Mgt tools for devices, switches etc and what people use to connect.

---

### Post by lwhitmore on 2008-12-12
I'm not a network admin by any means but I've picked up a bit of information about ubuntu+networking.

Try [http://www.kismetwireless.net/](http://www.kismetwireless.net/) and ettercap ([http://ettercap.sourceforge.net/](http://ettercap.sourceforge.net/)) for wireless detection/sniffing, and nmap for port scanning.

I've found sshfs ([http://fuse.sourceforge.net/sshfs.html](http://fuse.sourceforge.net/sshfs.html)) really useful for creating persistent connections to remote machines.  Basically, you get to browse the remote machine as if the machine is connected directly - and the connection is encrypted.

I use the standard terminal server client to connect to windows machines - and it seems to do a pretty good job.

---

### Post by iponeverything on 2008-12-13
> **moviewithnotitle said:**
> I already know those, I was curious about sniffer prgms, graphing prgms, SNMP trap prgms, Mgt tools for devices, switches etc and what people use to connect.

sniffer:

tcpdump, etherreal

graphing:

caci, mrtg 

SNMP traps.. 

Mgt tools for devices, switches:

minicom to conole in to a cisco.

and what people use to connect.

ssh and telnet

---

