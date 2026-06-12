---
title: "internet connection doesn't work"
date: 2005-11-29
forum: Desktop Environments
---

### Post by Barthelomeus on 2005-11-29
Hi,

I have installed ubuntu yesterday, everything works just fine, but I can't get my internet connection to work. I have tried a lot of things and searched a lot on the forums but I can't find a solution.

Here's my situation: I am running a dual boot with windows 2000 professional. In windows internet works fine.
I connect to the internet trough a router (SMC Barricade Broadband Router) to cable.
When I open FireFox, it starts "attempting to connect" but after a while it says "connection timeout".
My network card is activated and looks good.
I am able to ping websites (eg. [www.google.com](www.google.com)) and everything looks good. Also tracing websites works perfectly and gives the right path.
I have tried to disable the IPV6 service, but that doesn't help.

Last strange thing: when I restart my computer after running ubuntu and I go to windows 2000 (hot reboot), internet doesn't work anymore.
I have to shut down my computer and then start my computer again (cold reboot) to get my internet to work.

Does anybody knows a solution for this problem?

Bart

---

### Post by kosmic on 2005-11-29
Please post the result of the comand :
 
sudo ifconfig
 
where in the forum.
 
And post also the IP of the router - it should be something like 192.168.1.1
and the ethernet card you have
 
EDIT.: You can also try to put in the file resolv.conf the ip of your router

---

### Post by greenway on 2005-11-29
Since you're able to ping over the internet and traceroute works ok, it looks like your connection is up and running (otherwise you would not be able to ping and traceroute). Have you tried ohter browsers under Ubuntu?

Also, you might want to make a tcpdump and look at the packets transmitted while firefox is trying to connect to the internet.

---

### Post by Barthelomeus on 2005-11-29
here is the result of the ifconfig command:

eth0      Link encap:Ethernet  HWaddr FF:FF:FF:FF:FF:FF
          inet addr:192.168.123.250  Bcast:192.168.123.255  Mask:255.255.255.0
          inet6 addr: fe80::fdff:ffff:feff:ffff/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:68 errors:0 dropped:0 overruns:0 frame:0
          TX packets:39 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:9100 (8.8 KiB)  TX bytes:3432 (3.3 KiB)
          Interrupt:18 Base address:0xd800

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1709 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1709 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:154339 (150.7 KiB)  TX bytes:154339 (150.7 KiB)

The IP of my router is 84.192.183.190

My ethernet card is: Realtek RTL8129 PCI Fast Ethernet NIC

I added to the resolv.conf file the line "nameserver 84.192.183.190" but that didn't help. After I rebooted I noticed that the line I added was removed and the resolv.conf file was back to its original.

Thanks for the quick reply

---

### Post by jvictor on 2005-11-29
THere are 2 reasons

1)Firefox is talking in IPV6

Soln-: Disable IPV6 in firefox( type about:config in ur add bar and set network.dns.disableIPv6 to true)

Win works fine bcoz it talks in IPV4

2) Try the static DNS instead of DHCP .. 

HTH

[edit]
Hot reboot... try powering off the router and reboot it theres some option in the router which i cant recall now (i'm at office )that allows the router to continue in the same state as it was runnig linux .. I'll chk it from home and let u know  [/edit]

---

### Post by mrmcctt on 2005-11-29
This is a shot in the dark but are you running any kind of firewall (Firestarter perhaps)?  I had a similar problem and had to set the policies to allow http, https, ftp, etc... in Ubuntu.

Also, did you change your MAC address in the post above?  The address > Ethernet HWaddr FF:FF:FF:FF:FF:FF just does't seem to be a valid address for your hardware.

The only puzzling thing is losing connection in Windows after reboot.

---

### Post by Barthelomeus on 2005-11-29
I tried the IPV6 thing, it didn't help.

I am not running a firewall and I can't remember doing something that could have changed my MAC adress.

---

### Post by cwaldbieser on 2005-11-29
[QUOTE=Barthelomeus]I tried the IPV6 thing, it didn't help.

I am not running a firewall and I can't remember doing something that could have changed my MAC adress.[/QUOTE]
Can you wget or curl a page from the terminal?
```

$ curl http://www.google.com

```
If so, it is probably a Firefox problem.  If not, it may be a more general problem.

---

### Post by Barthelomeus on 2005-11-29
when I do "wget http://www.google.com" I get this:

--14:42:47--  [http://www.google.com/](http://www.google.com/)
           => `index.html'
Resolving [www.google.com](www.google.com)... 66.249.93.99, 66.249.93.104
Connecting to www.google.com|66.249.93.99|:80...

and nothing happens after that

---

### Post by jvictor on 2005-11-29
Have u disabled IPV6 for Ubuntu & Firefox both ? I assume that u meant fr Ubuntu..

---

### Post by handy on 2005-11-29
Hi, this helped me, as well as turning off ipv6 in the browser you need to do the following:

Open a terminal and enter:
sudo gedit /etc/modprobe.d/aliases

Look for the line that reads:
alias net-pf-10 ipv6

Change it to:
#alias net-pf-10 ipv6

Save and reboot your PC.

The above is courtesy of mips.

Happy to pass it on, I hope it helps.

handy

---

### Post by greenway on 2005-11-29
I am still going for a Firefox specific issue here. Why don't you make a tcpdump and see what extra information that provides...

---

### Post by maol62 on 2005-11-29
I had the same problem as you and regarding the resolv.conf file that is changing back to what it was before you changed it, try the command:

sudo chattr +i /etc/resolv.conf

after you have added the nameserver(s), and saved, that your ISP provide. Then it should be locked.
I dont think you should add your routers public address, you should add the addresses that your ISPs DNS-servers have.

I have posted a post [here]("http://www.ubuntuforums.org/showthread.php?t=94352") which describes how I solved it.

---

### Post by kosmic on 2005-11-29
Yes go to your router administation page, and see what is the DNS you are using and copy paste that dns number in the file resolv.conf and the do what maol62 says.
 
 
Another questions when I asked for your router IP was the internal IP that your router give to ohter pc, and not the external IP (The ip assigned by your provider)
 
if your ethernet card is configured it this ip : inet addr:192.168.123.250 
 
Then the router ip should be something like : 192.168.123.1
 
 
Another thing see if in your router you are not blocking port 80

---

### Post by Aenyn on 2005-11-29
Truly, my resolution is still up in the air, as my router has been a little flakey for everyone in the house.  

I followed the instructions [in this post](http://www.ubuntuforums.org/showpost.php?p=477981&postcount=6) to disable IPV6 globally.  I also set up my network connection statically and did not list my router as a DNS.  I had immediate results after reboot with all internet applications (gaim, apt-get, klibido, evolution).

---

### Post by Barthelomeus on 2005-11-29
> Have u disabled IPV6 for Ubuntu & Firefox both ? I assume that u meant fr Ubuntu..

yes, i have disabled IPV6 for Ubuntu & Firefox.

> I am still going for a Firefox specific issue here. Why don't you make a tcpdump and see what extra information that provides...

Can you explain a little bit how I can do that? I am not really an expert.

> I had the same problem as you and regarding the resolv.conf file that is changing back to what it was before you changed it, try the command:

sudo chattr +i /etc/resolv.conf

after you have added the nameserver(s), and saved, that your ISP provide. Then it should be locked.
I dont think you should add your routers public address, you should add the addresses that your ISPs DNS-servers have.

I have posted a post here which describes how I solved it.

I've just tried all the steps, but it doesn't help (I added the adress: 192.168.123.254, I guess this is my internal IP)

> Another thing see if in your router you are not blocking port 80

how can I see that?

> I also set up my network connection statically and did not list my router as a DNS. I had immediate results after reboot with all internet applications (gaim, apt-get, klibido, evolution).

How do I do that, and won't this mess up the connection of the other users on the router? (I don't want to have too much trouble with the rest over here)

---

### Post by Aenyn on 2005-11-29
I'll create screens when I get home.

---

### Post by Barthelomeus on 2005-11-30
I tried Gaim and I got the message: could not connect, so I don't think it's only a Firefox problem.

> I also set up my network connection statically and did not list my router as a DNS. I had immediate results after reboot with all internet applications (gaim, apt-get, klibido, evolution).

Anybody has an idea how I can do that?

I am getting a little desperate here...

---

### Post by Aenyn on 2005-11-30
```
sudo gedit /etc/modprobe.d/bad_list
```add;```
alias net-pf-10 off
```

Set up your connection staticaly, remove your router from the list of name servers, reboot.

ed;   I was unable to create screens last night due to previous plans.  I apologize.

---

