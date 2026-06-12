---
title: "DHCP problem"
date: 2005-12-29
forum: General Help
---

### Post by SZF2001 on 2005-12-29
So... I hook up the DSL box through the ethernet cord to my computer, running Ubuntu.

I go into Network Settings, activating it through DHCP.

Now, here's the thing... My computer acts like no internet connection is happening whatsoever. I look at the monitoration thing, and it says my computer has recieved and sent packets successfully, except it always stays 'Idel' (sp). So I go to Firefox with the monitor showing, and it sends out packets and recieves them, but the browser still can't get online. Neither can the Synaptic manager, same thing happens. How do I make it so it's not idel?

---

### Post by darth_vector on 2005-12-29
look in the file /etc/network/interfaces for a pair of lines like:
```
auto etho
iface eth0 inet dhcp
```
do you have them? if not then that is your problem. you can add them by editing the file as root
```
sudo gedit /etc/network/interfaces
```
and you will have to
```
sudo /etc/init.d/network restart
```
for the changes to be made.

you may also have to set the default route. to do this you would run
```
sudo route add default gw <router_ip_address> dev eth0
```
note that the above assumes that your network card is eth0. do an ifconfig do confirm this.


EDIT: oh, this might seem like a dumb question but; are you sure the adsl modem/router is running a dhcp server?

---

### Post by 0MG on 2005-12-29
are you sure you are getting an IP?

I'm going to go really basic, so if this is child's play to you, please don't take it personally.

Go into a terminal and type ifconfig 

does it give you an inet address? 

Also try typing: route

look for a gateway address. If you see one, try pinging it at the prompt by typing: ping 192.168.0.1 (or whatever the default gateway address is).

If your pings are successful, the next step is to try and ping the web somewhere. 

try: ping [www.yahoo.com](www.yahoo.com)

if that works, you are golden. 

If not, let me know where it went wrong.

---

### Post by thespazzz on 2005-12-29
I've been having a similar problum ever since I did the recent Kernel update,  I think it was a week ago or so.

The problum for me is for some reason Ubuntu is seeing my DSLModem/Router as a DNS server and trying to get DNS info from it.  No idea why but If I manualy imput my ISP's DNS info all is well untill I restart agian.

I have about 5 computers on my router and everything else works fine off DHCP but for some reason UBUNTU is the only one doing this.

---

### Post by chocolatetoothpaste on 2005-12-29
I had a similar problem.  I could run ifconfig and it said I had an ip.  I ran ```
nslookup google.com
``` and it would communicate just fine.  The problem was with my DNS entries.  It was specifying the wrong DNS addressess so I had to edit them from the network configuraiton tool.  Try that and see if firefox will work.  You can login to your router through firefox by entering the ip address in the address bar, then you can look at the details of your router to find the proper DNS entries.  Hope this helps.

---

