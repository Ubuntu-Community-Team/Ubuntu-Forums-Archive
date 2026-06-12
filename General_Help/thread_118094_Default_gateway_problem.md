---
title: "Default gateway problem"
date: 2006-01-16
forum: General Help
---

### Post by Demo2006 on 2006-01-16
I have laptop HP ze4125 with Ubuntu 5.10 and I have installed the linuxant modem driver. Modem works fine. One more thing - I have a local network at home (Laptop - Desktop). For dialing I use Gnome-dialer. My local network works fine too. 
Here is **the problem**. 
I try to cennect to the Internet through my modem (in the same time my laptop is connected to the desktop through local network) the connection is established to Internet, but when I enter the URL in FireFox it doesnot go to Internet through my modem connection. **It seems to me that it tries to find this URL in local network and not by using modem connection.** And of course FireFox does not find anything in local network. When I turn off my local network everything goes right. I have just one connection (modem connection) and Internet goes through it. The problem, I think, is in **default gateway settings**, but I didnt find anything in Ubuntu setting to configure it.

Thank you in advance.

---

### Post by Gowator on 2006-01-16
If you use the network-admin tool (its in Gnome desktop/administration somewhere) you will get the interfaces and a box at the bottom showing the default GW device ... this should be set to your modem (ppp) 

(However you can also just adhoc change at the CLI if this is an irregular event   ask if you prefer this)

---

### Post by Demo2006 on 2006-01-16
Thank you for quick reply.

Yes I found this option but it is "grey" and I am not able to change it to modem connection. only to ethernet connetcion (local network) and thst is it. Any other way to fix it?

About second variant - I am a newbie in Linux and I didnt understand whet is it CLI? Please explain it.

---

### Post by Gowator on 2006-01-16
[QUOTE=Demo2006]Thank you for quick reply.

Yes I found this option but it is "grey" and I am not able to change it to modem connection. only to ethernet connetcion (local network) and thst is it. Any other way to fix it?

About second variant - I am a newbie in Linux and I didnt understand whet is it CLI? Please explain it.[/QUOTE]
CLI = command line interface 

A bit more complex so lets stick with #1
I wonder if it is greyed out because your dial-up is not there .. can you describe how many interfaces ?  for me I see wireless/ethernet/modem connection 
I have (at the moment) only ethernet active but the box allows me to select it just not change interface ... 

did you get prompted for your password when you started it ?  

if you can open a terminal (CLI) and type 
route

it will show all the routes ... they should be like
```
root@ubuntu64:/etc/cups # route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
default         192.168.1.254   0.0.0.0         UG    0      0        0 eth0   
```

however what you need is

```
root@ubuntu64:/etc/cups # route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
default         xxx.xxx.xxx.xxx   0.0.0.0         UG    0      0        0 ppp0   
```
where xxx is the IP you are assigned at dial-up time...
This should be under the ppp settings but I can't help a  lot here because I don't have a modem ionstalled to test this.. if you post the results of 

ifconfig

and 

route 

we can try and move forwards though ..:D  
hint
if you need to boot to windows to post then using >file1.txt   will create a file with the resutls opf a command like

route > routeinfo.txt 
will cause a file in the present directory to contain what would have gone to stdout (the terminal)

---

### Post by Demo2006 on 2006-01-16
Thank you for your help. 
I am not near to my computerright now. I will definitely post the results here a little bit later.
Thank you, one more time.

---

