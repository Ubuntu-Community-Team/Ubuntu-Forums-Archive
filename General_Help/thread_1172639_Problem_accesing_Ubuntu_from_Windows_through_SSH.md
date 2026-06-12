---
title: "Problem accesing Ubuntu from Windows through SSH"
date: 2009-05-28
forum: General Help
---

### Post by walid97 on 2009-05-28
Hi there,

I want to access my Ubuntu box from my Windows box.

For that reason, I have installed openssh:
```
sudo apt-get install openssh-server
```I have then configued the sshd_config file:
```
sudo gedit /etc/ssh/sshd_config
```And changed the default port to 222:
```
Port 222
```I have then opened port 222 on my 3COM Adsl Router:
```
http://www.portforward.com/english/routers/port_forwarding/3com/3CRWDR101A-75/SSH.htm
```IP address: 192.168.1.2
LAN port: 222
Public port: 222


The Windows machine is connected to the ADSL Router and has a static IP of 192.168.1.6.

My Ubuntu machine is on a Windows Virtual Machine (VMWare), the network interface is directly connected to the physical network interface and it is having an IP from the ADSL Router (DHCP) = 192.168.1.2

My NOD32 Smart Security is disabled on the Windows machine, and no other firewall is turned on. I can ping the Ubuntu machine from the Windows machine.

SSH works when I try to connect from my Ubuntu machine to SSH:
```
ssh -p 222 myname@mymachine
```But from Windows (putty), SSH does not seem to work: Connection timed out.

What can the problem be? Can it be the Virtual Machine?

Thank you.

---

### Post by walid97 on 2009-05-30
bump.. ^^

---

### Post by trench.me on 2009-05-30
I know this isn't what you want to do but install FileZilla and see if SFTP works. 

SFTP is what Nautilus uses to manage graphical SSH in Ubuntu and I know that FileZilla has SFTP available so it's worth the attempt. Other than that I'm so far removed from Windows I wouldn't know where to begin. At least this would give you another way of checking the connection. If FileZilla fails (as PuTTY has been) then you've definitely got something blocking you. And my bets are on the VM.

---

### Post by fokmar on 2009-07-03
Try using a webbased ssh-client, with the one at [http://webssh.strangled.net]("http://webssh.strangled.net/") you can be sure that it will work on every operating system and that if the connection would fail that it would not be the fault of the client and neither the fault of a firewall between client or server.

---

### Post by Hobgoblin on 2009-07-03
> **walid97 said:**
> Hi there,

I want to access my Ubuntu box from my Windows box.


If they are on the same network then there is no need for port forwarding and trying to connect via the WAN IP will probably not work anyway.

> My Ubuntu machine is on a Windows Virtual Machine (VMWare), the network interface is directly connected to the physical network interface and it is having an IP from the ADSL Router (DHCP) = 192.168.1.2


In putty just enter 192.168.1.2 in the hostname and change the port to 222

[edit]Oops, sorry, just realised this is an old thread after opening another one bumped by fokmar, looks like someone is spamming.  Shouldn't use active topics at 4am when I only got 4 hours sleep yesterday.

---

