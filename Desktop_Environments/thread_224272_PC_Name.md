---
title: "PC Name"
date: 2006-07-27
forum: Desktop Environments
---

### Post by linmick on 2006-07-27
Hello,

Quick question how do I set my linux box name? Think is my router at: 192.168.1.1 reports ip. Do not know how to translate it to a name. I did give network name "Domainname" "tuck". 


See:


Connection Type:  	   Ethernet
PC Name: 	192.168.1.2  <---- it takes my static address.   Want "192.168.1.2" to become Dappy etc for instance for name.

IP Address: 	192.168.1.2

---

### Post by reclusivemonkey on 2006-07-27
The place you need to look is /etc/hosts;

```

127.0.0.1 localhost mother
192.168.1.4 mother mother.reclusivemonkey.com

```

if you need to know more,

```

man hosts

```

should tell you all you need to know.

---

### Post by jimmygoon on 2006-07-27
You can also just (re)set the hostname on one of the tabs in GNOME's network utility

---

### Post by harisund on 2006-07-27
Wait .. what exactly is your problem? If your problem is that the "router" doesn't see your machine's name, then doing the above 2 wouldn't work. Is that your problem? Or did doing either of the above suggestions fix what you were looking for?

---

### Post by linmick on 2006-07-28
> **harisund said:**
> Wait .. what exactly is your problem? If your problem is that the "router" doesn't seeyour machine's name, then doing the above 2 wouldn't work. Is that your problem? Or did doing either of the above suggestions fix what you were looking for?

Thanks for the reply(s) Correct as you said above. This is a minor problem, the bigger problem is gaim. I tried doing port forwarding as here:    (It does not work still since it probably is for windows). 

[http://www.portforward.com/english/routers/port_forwarding/Actiontec/GT704-WGv2/Yahoo_P2P_Instant_Messages.htm]("http://www.portforward.com/english/routers/port_forwarding/Actiontec/GT704-WGv2/Yahoo_P2P_Instant_Messages.htm")

My router is a: Actiontec GT704-WGv2

===============================================
Please check my steps below in sequence:

**_Opened Gnome network:_**
1. Connection tab selected ethernet and checked static.
2. Ip address: 192.168.1.2
3. Subnet Mask: 255.255.255.0
4. Gateway Address: 192.168.1.1

**_Opened General tab:_**

1. Hostname:     Dappy (think it is cute for dapper).
2. Domain Name:  tuck

**_Opened Dns tab:_**

1. Dns Servers: 192.168.1.1
2. Search domains: tuck

========================================================
**_Done with configuring computer_** and proceed configuring gateway:

[http://www.portforward.com/english/routers/port_forwarding/Actiontec/GT704-WGv2/Yahoo_P2P_Instant_Messages.htm]("http://www.portforward.com/english/routers/port_forwarding/Actiontec/GT704-WGv2/Yahoo_P2P_Instant_Messages.htm")
========================================================

Completed..... 

**_Results:_**

It will not connect on commandline as help from searching help:
~$ telnet scs.msg.yahoo.com 5050
Trying 216.155.193.151...

Will stay here or start retries. Gaim stays at connecting window and eventually gives up. It seems as if the port was not even opened.

Please help me if possible, feels like a panic attack. If possible lets try to do out of order second first. What am I doing wrong here? The old router connected without a problem.

Thank You

---

### Post by harisund on 2006-07-28
I am not sure I complete understand what you are talking about. You wouldn't have to open any ports to connect to the outside world. Opening of ports would only be required if you are running a server of some sorts. 

First, why are you not using DHCP and static instead? 

Second, with the current setup, ignoring Gaim connectivity issues, are you able to connect to the internet and surf regularly?

---

### Post by linmick on 2006-07-28
> **harisund said:**
> I am not sure I complete understand what you are talking about. You wouldn't have to open any ports to connect to the outside world. Opening of ports would only be required if you are running a server of some sorts. 

First, why are you not using DHCP and static instead? 

Second, with the current setup, ignoring Gaim connectivity issues, are you able to connect to the internet and surf regularly?

> **harisund said:**
> 
"First, why are you not using DHCP and static instead? 

I have tried using dhcp first and static after. My reasoned out plan was wrong in this case. I thought if I use static, perhaps it will reroute differently to the pc  and correctly. Don't ask it was flawed and you have confirmed it. Nothing has changed as a result of changing connection methods to the router.


> **harisund said:**
>  Second, with the current setup, ignoring Gaim connectivity issues, are you able to connect to the internet and surf regularly? 

To the point:
In the current form (static) I can access the internet and surf normally.  

Bit extra: in DHCP mode I can connect as well, my internet connection does work. So modes do not matter dhcp or static seems fine. But should stick to dhcp maybe?

**_*To get an idea of what is going on for you:*_**
[U][B]
I can use the following apps without any changes:[/B][/U] Firefox, apt-get, synaptic.

_**Following apps only work with changes:**_ 

Ftp client gftp:  Must remove passive mode.
Gaim: To work: must change all protocols to port 80. That is port 5000, 5001, 5050, 5190 do not work.  Which limits gaim what it can do.
Ubuntu System Updater: Will only show updates if synaptic or apt-get has been run first.

**_Following apps that will refuse to even connect:_**
Xchat: Will not work at all.
Peekko Browser IRC plugin: Needs port 8080 and as a result will not work.

Summary: Basic internet yes but not with all programs.
Reasoning for opening some ports: To be able to connect to the said services. Without turning off the firewall and compromising the computer. Turns out that those ports would be needed to be open, for remote access only.  So this is not the correct attempted fix. 

For two reasons 

1. did not fix my issue 
2. Was not the correct method to fix it with. 

 Sends "chills" doing that opening too many ports for outside.  

Actually the static is fine too so unless you ask me to change. I will probably stick to the static method.
 If it prevents you from helping me let me know.

Hopefully their is a fix please tell me so that their is! :(  Thanks :)

---

### Post by linmick on 2006-07-28
Here are bit more details on the connectionto yahoo:
@Dappy:~$ netstat
Active Internet connections (w/o servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State
tcp        0      1 192.168.1.2:36223       scs.msg.yahoo.com:5050  SYN_SENT

---

### Post by jimmygoon on 2006-07-28
Why are you having to do all of this stuff? Simply connecting to the internet, via static or dynamic should allow you access to all of those applications... Are you behind a proxy? What is the deal that is different about your setup... and what is the end goal you are trying to achieve?


Please tell me I'm wrong but if I'm not all you're trying to do is forward a few ports through your router? At one point up above you set your router to use your computer as a search area for DNS lookups which is almost guarenteedly not what you wanted....

So... What are you trying to do?!

---

### Post by linmick on 2006-07-28
Hello again!


> **jimmygoon said:**
> Why are you having to do all of this stuff? Simply connecting to the internet, via static or dynamic should allow you access to all of those applications... Are you behind a proxy? What is the deal that is different about your setup... and what is the end goal you are trying to achieve?


Please tell me I'm wrong but if I'm not all you're trying to do is forward a few ports through your router? At one point up above you set your router to use your computer as a search area for DNS lookups which is almost guarenteedly not what you wanted....

So... What are you trying to do?!


>  "Why are you having to do all of this stuff? Simply connecting to the internet, via static or dynamic should allow you access to all of those applications... 

Setting firewall to off allows me to connect to everything. But that does defeat the purpose of being secure correct? Am trying to keep the firewall on. Wondering  what changes  need to be done since port forwarding is not needed? My routers  firewall is odd it  does not allow to add any additional applications.


>  Are you behind a proxy? What is the deal that is different about your setup... 

Nope, not behind a proxy.


>  and what is the end goal you are trying to achieve? 


To keep my connection secure, that is keep firewall on medium and still be able to connect to gaim, xchat, peekko, ftp normally.

I thought that if I were to port forward it would work. Lets forget port forwarding now, I misunderstood the technology,  and just try to get all to work without port forwarding.

Please, if you have the time tell me how you would setup the connection given with now knowing my routers ip address and local machine. Step by step if you can otherwise just clear to understand.

**_Currently:_**
After all the discussions did a "1" step process. Reverted to just use dhcp. However as long as firewall is medium and not off. Problems described above will continue to exist. 

Guess better  question arriving to is. How to get my router to behaive with my operating system while the firewall on it is on?

Thank You

---

### Post by linmick on 2006-07-28
TO ALL SOLVED :p 

It seems this router does NAT and also has a more restrictive firewall.

---

