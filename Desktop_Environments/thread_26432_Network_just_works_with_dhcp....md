---
title: "Network just works with dhcp..."
date: 2005-04-12
forum: Desktop Environments
---

### Post by dangerous666 on 2005-04-12
I have figured out my network just works if I set the dhcp mode up. But i don't like using dhcp cause i have some static ip machines  in the netwok, and It's a problem.

When I configure manually, I can't use internet... I set the ip, broadcast, netmask and the gateway, but it just doesn't  work... I can ping the localhost, the gatway (router) and other computers, but I can't have access to the internet... When I run ifconf, it shows the same information, using dhcp or manual configuration...About the dns? yes I put working ones and it doesn't work...

Using dhcp, the internet access is perfect...

Ah.... I was using Kubuntu RC, and everything was working properly, using manual configuration.

But I decided to upgrade to the final release, making a clean install of Kubuntu... and now i've got this problem.

Could anyone help me?

---

### Post by illek on 2005-04-12
Set your DNS ip to the ip of the router.

---

### Post by heimo on 2005-04-12
If it's about DNS, you can do some troubleshooting with dig. This is what I often do:
```
dig @yourDNSipaddress www.ubuntuforums.org
```
of course subsitute the yourDNSipaddress with your DNS servers ip address. You should get the ip for ubuntuforums:

```
;; ANSWER SECTION:
www.ubuntuforums.org.   1800    IN      CNAME   ubuntuforums.org.
ubuntuforums.org.       1800    IN      A       66.246.118.210

```

if not, the dns is down, blocked or you have wrong dns ip. Try the gateway ip as illek suggests. It might be doing DNS caching and blocking outside access to port 53 (dns). Do a nmap port scan for just the one port on your dns:

```
nmap yourDNSipaddress -p 53

You should get:
PORT   STATE SERVICE
53/tcp open  domain

```

---

### Post by omni_lonnie on 2005-04-12
I had the same problem....  After doing ifconfig I realized that my broadcast was wrong.  To fix it I added a braodcast line to my /etc/network/interfaces file and restarted networking.  Wah-lah it works now :)

here is my that section of my interfaces file:
```
iface eth0 inet static
address 10.0.0.42
netmask 255.255.255.0
broadcast 10.0.0.255
gateway 10.0.0.1
```
I hope that helps!

---

### Post by Jonathan2007 on 2005-04-13
[QUOTE=omni_lonnie]I had the same problem....  After doing ifconfig I realized that my broadcast was wrong.  To fix it I added a braodcast line to my /etc/network/interfaces file and restarted networking.  Wah-lah it works now :)

here is my that section of my interfaces file:
```
iface eth0 inet static
address 10.0.0.42
netmask 255.255.255.0
broadcast 10.0.0.255
gateway 10.0.0.1
```
I hope that helps![/QUOTE]
Oh sweet. Very nice work. I had the same problem where I couldn't get the static to work. I figured it was leaving something out (such as the gateway on my) but I didn't know where to look. This worked perfectly. Of course I had to reboot before the internet started working again but now it works great on a static ip. I am surprised more people haven't had this problem. Must be a lot of dhcp users (I need a static for bittorrent  :grin: )

---

### Post by dangerous666 on 2005-04-13
[QUOTE=heimo]If it's about DNS, you can do some troubleshooting with dig. This is what I often do:
```
dig @yourDNSipaddress www.ubuntuforums.org
```
of course subsitute the yourDNSipaddress with your DNS servers ip address. You should get the ip for ubuntuforums:

```
;; ANSWER SECTION:
www.ubuntuforums.org.   1800    IN      CNAME   ubuntuforums.org.
ubuntuforums.org.       1800    IN      A       66.246.118.210

```

if not, the dns is down, blocked or you have wrong dns ip. Try the gateway ip as illek suggests. It might be doing DNS caching and blocking outside access to port 53 (dns). Do a nmap port scan for just the one port on your dns:

```
nmap yourDNSipaddress -p 53

You should get:
PORT   STATE SERVICE
53/tcp open  domain

```[/QUOTE]

I did this, and this works with the manual setting, so can I conlude that it isn't a DNS problem? Internet continues just working in dhcp mode...

About editing the /etc/network/interfaces, I had alrealdy done it without getting results...

this is what appears when I run ifconfig, both using dhcp or static

eth0       Encapsulamento do Link: Ethernet  Endereço de HW 00:50:8D:5F:F0:11
          inet end.: 192.168.254.1  Bcast:192.168.254.255  Masc:255.255.255.0
          UP BROADCASTRUNNING MULTICAST  MTU:1500  Métrica:1
          RX packets:384 errors:0 dropped:0 overruns:0 frame:0
          TX packets:359 errors:0 dropped:0 overruns:0 carrier:0
          colisões:0 txqueuelen:1000
          RX bytes:47597 (46.4 KiB)  TX bytes:22780 (22.2 KiB)
          IRQ:23 Endereço de E/S:0xe400

the ip, bcast and masc numbers are correct...

Is this a mistery?

:(

PS.: I'm in a network with a DSL modem (router) as server...

---

### Post by heimo on 2005-04-14
:(
 
dangerous666: Yes it seems that your TCP/IP is working and DNS is working... This is a mystery. :) And I love mysteries.
 
Next thing I'd do is telnetting to some web server (port 80), entering HTTP request manually and checking if that works. But you can achieve essentially same thing with wget. Unfortunately I'm not at my Linux box, so instructions will be untested.
 
Try: cd /tmp && wget [http://www.ubuntulinux.org/include/circle.jpg]("http://www.ubuntulinux.org/include/circle.jpg")
 
If you got the file, your http connections, dns and TCP/IP is working.
 
If it didn't work, I'd run */sbin/route -n *to see the routing table. Do it both with DHCP and static addresses and compare if anything is different.
 
Oh, has your ISP assigned you with static IP? There may be problems if you're just selecting IP and not leasing it from DHCP pool (range of IP addresses).
 
EDIT: It's too early morning and I haven't got my three cups of Ubuntu yet. Sorry for the lame answer, you stated very clearly that you're behind ADSL box and I can see that you are using reserved IP addresses.
 
EDIT2: So you must be using NAT (network address translation)? And the ADSL box is working as a gateway? What's its IP address? Is the scenario that you need static lan address for your computer so that the gateway can do port forwarding? In that case I'd still use DHCP and use Mac address to IP address binding in that ADSL box, if it's cabable of acting as DHCP server and can do Mac->IP bindings. That way you would have static IP address using dynamic configuration - done that many times and it rocks. :D
 
EDIT3: ;) Do you need proxy settings to connect to web? I think it's possible to configure also the proxy settings through DHCP, and those may be missing when you have configured static address.

---

### Post by frankO on 2005-04-14
I also have a problem changing the setup to static ip. When I go into Control center, Internet & network, network settings  and change my settings from dhcp to static, fill in all the values and hit apply, the gateway ip becomes a blank. 

It does not matter how many times I re-enter the ip address for the gateway, hitting apply loses the setting. Changing back to dhcp fixes the problem.
Any ideas?

---

### Post by Jonathan2007 on 2005-04-14
[QUOTE=frankO]I also have a problem changing the setup to static ip. When I go into Control center, Internet & network, network settings  and change my settings from dhcp to static, fill in all the values and hit apply, the gateway ip becomes a blank. 

It does not matter how many times I re-enter the ip address for the gateway, hitting apply loses the setting. Changing back to dhcp fixes the problem.
Any ideas?[/QUOTE]
Uh did you even read the posts in this thread? Check omni_lonnie's post and my post following his. I had your exact problem and when I did what omni_lonnie suggested I got the static ip working just fine.

---

### Post by dangerous666 on 2005-04-14
[QUOTE=heimo]:(
 
dangerous666: Yes it seems that your TCP/IP is working and DNS is working... This is a mystery. :) And I love mysteries.
 
Next thing I'd do is telnetting to some web server (port 80), entering HTTP request manually and checking if that works. But you can achieve essentially same thing with wget. Unfortunately I'm not at my Linux box, so instructions will be untested.
 
Try: cd /tmp && wget [http://www.ubuntulinux.org/include/circle.jpg]("http://www.ubuntulinux.org/include/circle.jpg")
 
If you got the file, your http connections, dns and TCP/IP is working.
 
If it didn't work, I'd run */sbin/route -n *to see the routing table. Do it both with DHCP and static addresses and compare if anything is different.
 
Oh, has your ISP assigned you with static IP? There may be problems if you're just selecting IP and not leasing it from DHCP pool (range of IP addresses).
 
EDIT: It's too early morning and I haven't got my three cups of Ubuntu yet. Sorry for the lame answer, you stated very clearly that you're behind ADSL box and I can see that you are using reserved IP addresses.
 
EDIT2: So you must be using NAT (network address translation)? And the ADSL box is working as a gateway? What's its IP address? Is the scenario that you need static lan address for your computer so that the gateway can do port forwarding? In that case I'd still use DHCP and use Mac address to IP address binding in that ADSL box, if it's cabable of acting as DHCP server and can do Mac->IP bindings. That way you would have static IP address using dynamic configuration - done that many times and it rocks. :D
 
EDIT3: ;) Do you need proxy settings to connect to web? I think it's possible to configure also the proxy settings through DHCP, and those may be missing when you have configured static address.[/QUOTE]

Oh yes, let's go. In response to EDIT2
Yes, the adsl modem is working as gateway, his IP adress is 192.168.254.254... My lan ip is 192.168.254.1 and the port forwarding is redirecting the ports to the lan ip, I didn't understand very well the thing about the MAC, and I think that's not the problem, cause i always used this same scenario in another distros (even in Ubuntu/Kubuntu, in older releases, like preview and RC) and in Windows XP, and it always worked fine... I've got this problem only after installing Kubuntu 5.04 final.

EDIT3: I don't need proxy settings...

and the mistery goes on... heheheh

---

### Post by buldir on 2005-04-14
I have the same problem.  I tried setting the static IP, etc. in the GUI network section and no dice.  I'll try this when I get home.  Thanks for posting all.  Long live the CLI and verbose config files!

---

### Post by dangerous666 on 2005-04-16
[QUOTE=buldir]I have the same problem.  I tried setting the static IP, etc. in the GUI network section and no dice.  I'll try this when I get home.  Thanks for posting all.  Long live the CLI and verbose config files![/QUOTE]

I think I gonna back to Kubuntu RC release... Nobody knows how to solve this problem, there are many people in this forum with the same problem... I think this is bug.

---

### Post by heimo on 2005-04-16
[QUOTE=dangerous666]I think I gonna back to Kubuntu RC release... Nobody knows how to solve this problem, there are many people in this forum with the same problem... I think this is bug.[/QUOTE]

There are people in this thread who had problems setting static addresses and then solved it. It'd benefit the community to verify that it is a bug and not a configuration problem, but you're of course free to make your own decisions. Sincerely and with all respect.

Have you made sure that the settings are correct and after restarting networking (/etc/init.d/networking restart) that those settings took effect? (/sbin/route -n and ifconfig).

For just to make sure that this is not problem that affects everybody here, I tried to set static address to my network card and there was no problems at all. This really, really sound like a configuration problem, but if it's software problem, we'd be better if we knew what causes it.

Thanks! :)

EDIT:

I checked the other thread you're on. Do you have something like this in /etc/networ/interfaces:
(edit: I got the numbers wrong first, fixed)

 ```

iface eth0 inet static
   address 192.168.254.1
   netmask 255.255.255.0 
   broadcast 192.168.254.255
   gateway 192.168.254.254

auto eth0

``` 

And after /etc/init.d/networking restart, can you ping these?


[list]
[*]192.168.254.254
[*]192.168.254.1
[/list]

---

### Post by dangerous666 on 2005-04-16
[QUOTE=heimo]There are people in this thread who had problems setting static addresses and then solved it. It'd benefit the community to verify that it is a bug and not a configuration problem, but you're of course free to make your own decisions. Sincerely and with all respect.

Have you made sure that the settings are correct and after restarting networking (/etc/init.d/networking restart) that those settings took effect? (/sbin/route -n and ifconfig).

For just to make sure that this is not problem that affects everybody here, I tried to set static address to my network card and there was no problems at all. This really, really sound like a configuration problem, but if it's software problem, we'd be better if we knew what causes it.

Thanks! :)

EDIT:

I checked the other thread you're on. Do you have something like this in /etc/networ/interfaces:
(edit: I got the numbers wrong first, fixed)

 ```

iface eth0 inet static
   address 192.168.254.1
   netmask 255.255.255.0 
   broadcast 192.168.254.255
   gateway 192.168.254.254

auto eth0

``` 

And after /etc/init.d/networking restart, can you ping these?


[list]
[*]192.168.254.254
[*]192.168.254.1
[/list][/QUOTE]

Yes, using static setting I can ping the router, the localhost eand other machines in the network.... The only thin that doesn't work is the internet access...Ah, I restarted network many times..

---

### Post by heimo on 2005-04-16
And you have checked that the settings took effect? That the default gateway setting is ok? Can you ping outside ip (for example nameserver IPs from /etc/resolv.conf)?

Try running traceroute or tracepath on the other machines to outside IP, check what is the next hop (next ip after your ADSL) and try pinging that ip from your problematic machine, then try tracerouting it, post as much debug information as you can.

Try doing
dig slashdot.org
dig -x 66.35.250.150

Try entering 'http://66.35.250.150/' on browser.

If you have logging on that ADSL box, check if there's something.

Oh, and if you will, attach *interfaces*, output of *route -n and *ifconfig

---

### Post by buldir on 2005-04-16
Thanks omni_lonnie!  I gave it a whirl using the CLI approach, rebooted, and bickity-bam...a working static IP!

---

### Post by dangerous666 on 2005-04-17
Hello people!

I think I have found the problem... The first one is the network utility of kcontrol... It's not working properly, it always mess up the /etc/network/interfaces and /etc/resolv.conf... So It's better not to even open this utility... It was what I was doing...

So, when I figured it out, I did all the settings manually, editing /etc/network/interfaces and /etc/resolvconf with proper values, not running kcontrol or another network utility.... Bingo! the static way is working, after a network restart, of course. The problem now is the resolv.conf file, It's owerwritten each boot... and I have to put the dns adresses and restart teh network each boot... it's overwritten by a "blank" file containing just teh following:

# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN

Every entry I put in resolv.conf desappear after rebooting...

need help! ehehehe

---

### Post by heimo on 2005-04-18
I guess it's */etc/init.d/dns-clean*. This may be a bit rough solution, but may work:

 ```
update-rc.d -f dns-clean remove

``` 

Instead of that, you could also just rename the symlink in /etc/rc2.d/ beginning with S and having name dns-clean in it. (if you are running runlevel 2 by default) Rename it to begin with K and it will not run.

---

### Post by dangerous666 on 2005-04-19
I solve the problem...

I uninstalled the package "resolvconf" and now my resolv.conf isn't being owerwritten each boot...

What is the resolvconf package for?

---

### Post by heimo on 2005-04-19
Good work solving it!


apt-cache show resolvconf
```
Description: Nameserver information manager
 Resolvconf is a framework for keeping track of the system's
 information about currently available nameservers. It sets
 itself up as the intermediary between programs that supply
 nameserver information and programs that use nameserver
 information. Examples of programs that supply nameserver
 information are: ifupdown, DHCP clients, the PPP daemon and
 local nameservers. Examples of programs that use this
 information are: DNS caches, resolver libraries and the
 programs that use them.

```

---

