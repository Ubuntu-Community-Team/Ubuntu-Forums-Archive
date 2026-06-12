---
title: "setting up a network"
date: 2010-07-31
forum: Desktop Environments
---

### Post by Amy_1990 on 2010-07-31
I am looking to set up a home network.I have a desktop pc and a  laptop with a wireless network card i have no windows pc's to add to this network.I used giver but found that it is very slow.I have looked on the internet but found nothing for ubuntu 10.04.Both pc's are running ubuntu 10.04.Thanks
[IMG]http://www.qtl.co.il/img/copy.png[/IMG][[IMG]http://www.google.com/favicon.ico[/IMG]]("http://www.google.com/search?q=the%20way%20ubuntu%20one%20works")[IMG]http://www.qtl.co.il/img/trans.png[/IMG]

---

### Post by Amy_1990 on 2010-07-31
I don't have any pc's running windows i moved them all to ubuntu 10.04.How would i set up home networking using only ubuntu?

---

### Post by sir_cheats_a_lot on 2010-07-31
if you have a wifi-card in your desktop and a wireless router, it should,in my mind, pretty much set itself up.  i think at most you'd have to open firefox and enter.. i think it's 192.168.1.1 or 192.168.0.1(forget which)into your address bar to access the router's control panel. 

 if you don't have a router, then a cross-over cable/switch would be the next best thing. . . though that route is nightmarish if you plan to share internet on the network, especially since the package ipmasq(required for ip-masquerade commands) is not in the lucid lynx repositories.

if you need more specific help, im pretty sure there is a section on setting up networking in ubuntu's wiki page.  good luck.

---

### Post by Morbius1 on 2010-07-31
Since you're already using giver you could go up a notch and try these two methods first. They're easy to set up so if they don't work you haven't wasted too much time:

_Personal File Sharing_
You'll need to install the following packages to make this work:
```
apache2.2.bin
libapache2-mod-dnssd
```Now go to Preferences > Personal File Sharing > Share public files on network.
This utility requires avahi to be running all the machines and it is installed by default in Ubuntu. 
It will only allow you to share one folder: /home/your_username/Public.
I personally find it kind of flaky but some people swear by it.

_Samba_
There are some that will recoil at the mere mention of using samba between two linux boxes and say things like "Real men don't use samba". This shouldn't be a problem for you unless you are in reality a 57 year old truck driver from Des Moines named Earl.

The easiest way to use Samba is this way:
Open Nautilus ( Home Folder )
Right Click on say ... Documents
Select "Sharing Options"
[COLOR=Blue]*If you don't have samba installed already it will ask you if you want to install it ( It won't call it samba but "Windows Networking" or something like that. )*[/COLOR]
Select all three boxes and then select "Create Share"
It will ask you if you want it to modify permissions - you do.
You have just created a samba public share.

_On the other Ubuntu Box_
Go to Places > Network
and you should see the shares created by either of the above methods.

Note: Samba will either work or not. The specific method I outlined above will let you know in 15 seconds if it will work for you. I've never had a problem with it but there are thousands of postings on forums from people who cannot get it to work. There are over a million HowTo's on the web on getting it to work but 99% of them are just plain wrong. 

You have other options like NFS and ssh which are the more traditional ways of doing all linux sharing.

---

