---
title: "installing softwares"
date: 2009-02-27
forum: General Help
---

### Post by kask1984 on 2009-02-27
hi every one i am very new to ubuntu and ubuntu forum .i dont know whether it is the correct way to ask a question.
i installed ubuntu and i have net connection but i am unable to install softwares like amarok from terminal window . can anybody explain step by step process to insatll softwares and what are various ways of installing softwares .

---

### Post by iaculallad on 2009-02-27
Installing using the terminal:

```
sudo apt-get install application_name
```

You could also use Synaptics Package Manager to install applications in your Ubuntu machine.

System->Administration->Synaptics Package Manager

EDIT:

For detailed application installation in Ubuntu, read this [link]("http://www.psychocats.net/ubuntu/installingsoftware").

---

### Post by fooman on 2009-02-27
what do you get when you try:

```
sudo apt-get install amarok
```you could also try using add/remove programs (applications > add/remove) or even better would be synaptic package manager (system > administration > synaptic package manager).  you will find a lot more in synaptic.

also might want to add the medibuntu repositories:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

edit: sorry too slow, iaculallad beat me.

---

### Post by sahabcse on 2009-02-27
Hi

Installing packages follow the below url

============================================
[http://sahabm.blogspot.com/2009/01/package-management-debian-and-ubuntu.html](http://sahabm.blogspot.com/2009/01/package-management-debian-and-ubuntu.html)
===========================================


Regards
Sahab

---

### Post by kask1984 on 2009-02-27
this is the message i am getting when i typed sudo apt-get install amarok
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package amarok

---

### Post by fooman on 2009-02-27
try the medibuntu link i posted above.  that should help you.

---

### Post by iaculallad on 2009-02-27
> **kask1984 said:**
> this is the message i am getting when i typed sudo apt-get install amarok
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package amarok

Use the Add/Remove program to install Amarok. Applications->Add/Remove, Click on the **Sound and Video** column then select **Amarok** on the righ-side pane. Click on **Apply Changes**.

---

### Post by kask1984 on 2009-02-27
when i typed 
sudo wget [http://www.medibuntu.org/sources.list.d/intrepid.list](http://www.medibuntu.org/sources.list.d/intrepid.list) --output-document=/etc/apt/sources.list.d/medibuntu.lis
this one from medibuntu link u gave , i am geeting following in terminal

--2009-02-27 12:32:42--  [http://www.medibuntu.org/sources.list.d/intrepid.list](http://www.medibuntu.org/sources.list.d/intrepid.list)
Resolving [www.medibuntu.org](www.medibuntu.org)... failed: Name or service not known.
wget: unable to resolve host address `[www.medibuntu.org](www.medibuntu.org)'

---

### Post by iaculallad on 2009-02-27
Try to test your nameserver lookup using dig or nslookup:

```
dig +noall +answer medibuntu.org
```

or 

```
nslookup medibuntu.org
```

---

### Post by kask1984 on 2009-02-27
when i followed u r steps
 i am geeting this
[IMG]http:///home/a/Desktop/refresh[/IMG]

[IMG]http:///home/a/Desktop/error.png[/IMG]

what should i do

---

### Post by kask1984 on 2009-02-27
when i followed u r steps
 i am geeting this
[IMG]http:///home/a/Desktop/refresh[/IMG]

[IMG]http:///home/a/Desktop/error.png[/IMG]

what should i do

---

### Post by kask1984 on 2009-02-27
i tried both u r command i have got 
;; connection timed out; no servers could be reached


what is nameserver

---

### Post by iaculallad on 2009-02-27
> **kask1984 said:**
> i tried both u r command i have got 
;; connection timed out; no servers could be reached


what is nameserver

Nameserver is your DNS (Domain Name) server. Could you post your resolv.conf file.

```
cat /etc/resolv.conf
```

EDIT: To make it easier, why not try the method I posted in post # 7 if it will work.

---

### Post by kask1984 on 2009-02-27
i tried post #7 actually i replied in post #11 i inserted pictures but those are not displaying
when i did this Applications->Add/Remove, Click on the Sound and Video column then select Amarok on the righ-side pane
one window came with title the list of of applications not avilable with optins refresh and close
when i clicked on refresh it says downloading package info and after some time error message came saying an error occured .

sorry to ask late, how much speed of internet we should have to download files and which server to keep in software sources.

waiting for u r reply

---

### Post by Peter09 on 2009-02-27
can you type in a terminal

```
ifconfig
```

and also 

```
route
```

and post the output of the commands

---

### Post by kask1984 on 2009-02-27
a@a-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1d:09:52:94:35  
          inet addr:172.20.90.123  Bcast:172.20.255.255  Mask:255.255.0.0
          inet6 addr: fe80::21d:9ff:fe52:9435/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1869288 errors:0 dropped:0 overruns:0 frame:0
          TX packets:39560 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:146561470 (146.5 MB)  TX bytes:4674502 (4.6 MB)
          Interrupt:16 

eth1      Link encap:Ethernet  HWaddr 00:1f:3a:b8:66:a9  
          inet6 addr: fe80::21f:3aff:feb8:66a9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:90 errors:0 dropped:0 overruns:0 frame:0
          TX packets:90 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4460 (4.4 KB)  TX bytes:4460 (4.4 KB)


a@a-laptop:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
link-local      *               255.255.0.0     U     1000   0        0 eth0
172.20.0.0      *               255.255.0.0     U     1      0        0 eth0
default         172.20.0.99     0.0.0.0         UG    0      0        0 eth0

---

### Post by Peter09 on 2009-02-27
You have a connection that is OK.

Try

```
ping google.com
```

to test DNS

---

### Post by kask1984 on 2009-02-27
i am getting like this 
a@a-laptop:~$ ping google.com
ping: unknown host google.com
a@a-laptop:~$ ping [www.google.com](www.google.com)
ping: unknown host [www.google.com](www.google.com)
a@a-laptop:~$ ping [www.google.co.in](www.google.co.in)
ping: unknown host [www.google.co.in](www.google.co.in)


( i tried different possibilities note: i am able to browse google using firefox web browser)

---

### Post by Peter09 on 2009-02-27
Are you behind a proxy server?

Are you at work or home?

---

### Post by kask1984 on 2009-02-27
yes i am behind proxy server i am in college

---

### Post by Peter09 on 2009-02-27
I think the Proxy is blocking your service. You will need to talk to the IT department, they should be able to help you with name resolution, which is the problem that you have.

---

### Post by theozzlives on 2009-02-27
Just go to Applications > Add/Remove. In the upper right, there should be a text box. Type amar, Amarok should appear in the list of applications. Put a check in the box next to it and click Apply in the lower right. Another box will pop up, click Apply again. Enter your password and it'll download and install.

---

### Post by halovivek on 2009-02-27
Try to get the proxy server details from them and add it in the network connection by opening the it by double clicking the icon.

---

### Post by kask1984 on 2009-02-27
yesterday night when i tried from my room ( now i am in lab) i have downloaded some packages. in room net comes slowly.i dont remember what i did , but at that time  ubuntu cd was in cd  drive.( ofcourse not all packages were downloaded).

---

### Post by kask1984 on 2009-02-27
just now in SYSTEM > NETWORK PROXY I HAVE SET THE PROXY  settings 
 add/remove procedure is working it is downloading some files let us see what happens

THANKS A LOT TO ONE AND ALL

---

