---
title: "ubuntu and asus motherboard"
date: 2009-01-01
forum: General Help
---

### Post by qwertpie on 2009-01-01
currently i am a new ubuntu user. i have downloaded several ubuntu 8.10 copy's from the ubuntu web site. before trying to install i always checked to make sure that it was a good copy. when i try to connect to the internet though ubuntu i run into all kinds of problems. my internet is dsl and its an open network so i should be able to connect to the internet automatically right? i have tried many things to connect to the internet to no avail... could it be that my motherboard dose not run the ubuntu driver for the internet?? i am using a asus-ms motherboard with a nvidia geforce 6150 chipset... if anyone could give me any ideas i would be grateful

---

### Post by mikewhatever on 2009-01-01
Why the motherboard? Do you have any reason to believe the motherboard has something to do with it? I think the thread title should have read something like 'No internet on 8.10, new installation.', thus indicating what the problem is.
Can you post the following info:
1. Are you connected directly to the SDL modem? Ethernet or USB, what model?
2. Is there a router, wired or wireless, what model?
3. Post the output of <ifconfig> from Applications -> Accessories ->Terminal.

---

### Post by jespdj on 2009-01-01
> **qwertpie said:**
> could it be that my motherboard dose not run the ubuntu driver for the internet??
First of all, your motherboard does not run drivers. Drivers are special programs that run in the operating system (Ubuntu). Also there is no "driver for the internet".

Why do you think it has something to do with your motherboard?

---

### Post by tsucol11 on 2009-01-01
> **qwertpie said:**
> currently i am a new ubuntu user. i have downloaded several ubuntu 8.10 copy's from the ubuntu web site. before trying to install i always checked to make sure that it was a good copy. when i try to connect to the internet though ubuntu i run into all kinds of problems. my internet is dsl and its an open network so i should be able to connect to the internet automatically right? i have tried many things to connect to the internet to no avail... could it be that my motherboard dose not run the ubuntu driver for the internet?? i am using a asus-ms motherboard with a nvidia geforce 6150 chipset... if anyone could give me any ideas i would be grateful

I am running ubuntu 8.10 on 2 diff ASUS MB, P4P800E & A8Nsli

Both boards would not connect the the internet following installation.

do the following:

sudo gedit /etc/network/interfaces

you should have:

auto lo eth0
iface lo inet loopback
iface eth0 inet dhcp

if any of the above lines are missing add them.report your findings

Brian

---

### Post by tsucol11 on 2009-01-01
> **tsucol11 said:**
> I am running ubuntu 8.10 on 2 diff ASUS MB, P4P800E & A8Nsli

Both boards would not connect the the internet following installation.

do the following:

sudo gedit /etc/network/interfaces

you should have:

auto lo eth0
iface lo inet loopback
iface eth0 inet dhcp

if any of the above lines are missing add them.report your findings

Brian

I forgot to add that after adding the above mentioned lines everything worked fine at max speed.

Have a good one.

Brian

---

### Post by qwertpie on 2009-01-01
> **mikewhatever said:**
> Why the motherboard? Do you have any reason to believe the motherboard has something to do with it? I think the thread title should have read something like 'No internet on 8.10, new installation.', thus indicating what the problem is.
Can you post the following info:
1. Are you connected directly to the SDL modem? Ethernet or USB, what model?
2. Is there a router, wired or wireless, what model?
3. Post the output of <ifconfig> from Applications -> Accessories ->Terminal.





my im connected useing ethernet there is a wireless router also but i dont have a card for it in my computer. the modem is DPC21000r2 series and the router is MN 500. i did not really know if it had anything to do with my motherboard, but a friend told me to see if there had been other people with problums using my kind of motherboard. thanks for all the help and tips and ill post my findings as soon as i can  thnx.

---

### Post by qwertpie on 2009-01-01
ubuntu@ubuntu:~$ ifconfig
eth0   Link encap:Ethernet  HWaddr 00:1d:60:18:c8:a5  
       UP BROADCAST RUNNING MULTICAST  MTU:64  Metric:1
       RX packets:44 errors:0 dropped:0 overruns:0 frame:0
       TX packets:9 errors:0 dropped:0 overruns:0 carrier:0
       collisions:0 txqueuelen:1000 
       RX bytes:6911 (6.9 KB)  TX bytes:1933 (1.9 KB)
       Interrupt:21 

lo  Link encap:Local Loopback  
    inet addr:127.0.0.1  Mask:255.0.0.0
    inet6 addr: ::1/128 Scope:Host
    UP LOOPBACK RUNNING  MTU:16436  Metric:1
    RX packets:216 errors:0 dropped:0 overruns:0 frame:0
    TX packets:216 errors:0 dropped:0 overruns:0 carrier:0
    collisions:0 txqueuelen:0 
          RX bytes:13536 (13.5 KB)  TX bytes:13536 (13.5 KB)

ubuntu@ubuntu:~$ sudo gedit/etc/networks/interfaces
sudo: gedit/etc/networks/interfaces: command not found

---

### Post by dcstar on 2009-01-01
> **qwertpie said:**
> ubuntu@ubuntu:~$ ifconfig
eth0   Link encap:Ethernet  HWaddr 00:1d:60:18:c8:a5  
       UP BROADCAST RUNNING MULTICAST  MTU:64  Metric:1
       RX packets:44 errors:0 dropped:0 overruns:0 frame:0
       TX packets:9 errors:0 dropped:0 overruns:0 carrier:0
       collisions:0 txqueuelen:1000 
       RX bytes:6911 (6.9 KB)  TX bytes:1933 (1.9 KB)
       Interrupt:21 

lo  Link encap:Local Loopback  
    inet addr:127.0.0.1  Mask:255.0.0.0
    inet6 addr: ::1/128 Scope:Host
    UP LOOPBACK RUNNING  MTU:16436  Metric:1
    RX packets:216 errors:0 dropped:0 overruns:0 frame:0
    TX packets:216 errors:0 dropped:0 overruns:0 carrier:0
    collisions:0 txqueuelen:0 
          RX bytes:13536 (13.5 KB)  TX bytes:13536 (13.5 KB)

ubuntu@ubuntu:~$ sudo gedit/etc/networks/interfaces
sudo: gedit/etc/networks/interfaces: command not found

You have a ethernet interface but no IP address, you can try using the Network Manager to set it to use DHCP and see what happens.

This is on the assumption that you have a "normal" network setup and not one that is tied into some specific DSL modem setup.

---

### Post by mikewhatever on 2009-01-02
> ubuntu@ubuntu:~$ sudo gedit/etc/networks/interfaces
sudo: gedit/etc/networks/interfaces: command not found

You are getting an error, because there is no space between gedit and /etc, and there is no 's' in network. If possible, try copying and pasting.
> **gksudo gedit /etc/network/interfaces**

---

### Post by tsucol11 on 2009-01-02
> **mikewhatever said:**
> You are getting an error, because there is no space between gedit and /etc, and there is no 's' in network. If possible, try copying and pasting.

Mikewhatever is right. Also we are assuming that your router is supplying  dchp.

The same problem occurs with the Ubuntu 8.10 live CD. Problem corrected with Ubuntu 8.10 server edition & ubuntustudio-8.10-alternate.

Brian

---

### Post by qwertpie on 2009-01-05
so u think i should try the server addition?

---

### Post by tsucol11 on 2009-01-05
> **qwertpie said:**
> so u think i should try the server addition?

No, use the desktop. It is more user friendly.

As stated before, open your text editor (applications, accessories, text editor). Open the file [COLOR="Red"]interfaces[/COLOR] located in /etc/network.

post the content of the text file "interfaces" to the forum. If it is not as follows we have probably found your problem:


auto lo eth0
iface lo inet loopback
iface eth0 inet dhcp

correcting it is easy, but 1 step at a time

Brian

---

