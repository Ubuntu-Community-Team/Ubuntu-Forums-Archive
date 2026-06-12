---
title: "Root priveleges on resolv.conf"
date: 2005-10-28
forum: Desktop Environments
---

### Post by otware on 2005-10-28
Ok I have a number of problems.

1. Ubuntu (5.10) thinks that the DNS server is my router (192.168.1.1), which is obviously not true. So I have to change the IP in resolv.conf to the actual DNS server address. I can't use browsers (ie urls), but I can ping servers and IPs in terminal. But I have this problem covered.

2. (/etc/)resolv.conf is 'owned' by root. even using  sudo, I do not have the priveleges required to fix the IP address. I have tried everything from 
'sudo gedit /etc/resolv.conf' to installing a root password and trying to use that (it won't let me log on as root, and I can't use the su feature in terminal).

So basically I need to know how to get complete, out and out, root priveleges on that one file, so i can fix my internet trouble.

---

### Post by kvidell on 2005-10-28
[QUOTE=otware]So basically I need to know how to get complete, out and out, root priveleges on that one file, so i can fix my internet trouble.[/QUOTE]
who IS it owned by?
do this:```
ls -ldh /etc/resolv.conf
```Mine looks like this:> 1/kvidell/happytop: ls -ldh /etc/resolv.conf 
-rw-r--r--  1 root root 73 2005-10-28 08:49 /etc/resolv.confSomeone may want to verify whether this is a sane idea or not, but maybe just try...```
chown root:root /etc/resolv.conf
```Could work...
- Kev

---

### Post by otware on 2005-10-28
OK i'll do the first thing you told me now, and that will show me the priveleges on the file? I can tell you that just be right clicking and going on properties.

---

### Post by otware on 2005-10-28
right i have the same permissions as you:
-rw-r--r-- 1 root root etc. etc.

ok i'll try your insane idea. 

has anybody else had this problem where ubuntu thinks your router is your DNS server, and as such can't access the internet?

---

### Post by otware on 2005-10-28
OK it didn't really work...in fact it didn't do anything. it just went onto another line as if nothing had happened... i assume that that was supposed to kill the permissions on that file?

---

### Post by cydizen on 2005-10-28
Hey Gents,

On my home network, my belkin router (192.168.2.1) handles the incoming wan connectection, so... as far as my pc's are concerned, the router is the gateway AND DNS.  For instance, if I set my gateway @ 192.168.2.1, all the boxes on the network can communicate, but until I drop 192.168.2.1 in the DNS, it does not want to play outside my LAN.  However, instead of editing the resolv.conf, I just use the system -> administration -> networking and do it all right there. 

Hope some of this helps.


Regards,
Bruce

---

### Post by otware on 2005-10-28
yeah you can edit it that way. But you can't add DNS servers to the list, because it drags that list straight from the read-only resolv.conf file. 

hey i just had an idea. maybe if i go to [http://192.168.1.1](http://192.168.1.1) (my router/firewall/adsl model configuration page), I can see what the DNS settings should be.

---

### Post by cydizen on 2005-10-28
you sure can add them! yes, it grabs the resolve.conf entries, but allows you to add/delete there if you want(which edits the resolv.conf file).  I can send you some screenshots if you want to see what I am talking about. 


Let me know,
Bruce

---

### Post by sanjose on 2005-10-28
[quote=otware]Ok I have a number of problems.

1. Ubuntu (5.10) thinks that the DNS server is my router (192.168.1.1), which is obviously not true. So I have to change the IP in resolv.conf to the actual DNS server address. I can't use browsers (ie urls), but I can ping servers and IPs in terminal. But I have this problem covered.

2. (/etc/)resolv.conf is 'owned' by root. even using sudo, I do not have the priveleges required to fix the IP address. I have tried everything from 
'sudo gedit /etc/resolv.conf' to installing a root password and trying to use that (it won't let me log on as root, and I can't use the su feature in terminal).

So basically I need to know how to get complete, out and out, root priveleges on that one file, so i can fix my internet trouble.[/quote]


you don't have to edit your ***/etc/resolv.conf*** because it is overwritten by dhcpclien-script which is installed by default on Ubuntu. 

if you wan't to add manually your ISP DNS you have to edit your ***/etc/dhcp3/dhclient.conf***

add this line:

[INDENT]***prepend domain-name-servers 127.0.0.1;***
  
replace 127.0.0.1 with your ISP DNS
[/INDENT]

---

### Post by otware on 2005-10-28
yeah that sounds like a plan.

---

### Post by otware on 2005-10-28
hang on I think i've got it all wrong plz help!
I think the DNS server is actually supposed to be set to my router (192.168.1.1). But it is allready set to this, but I cannot access any urls. what should I do?

I had a similar problem with Kubuntu 5.10, but I could access webpages using Konqueror. Is it possible that there is something wrong with the firefox installation - it is the version installed with Ubuntu?

Maybe it is something else like the subnet mask?

---

### Post by otware on 2005-10-29
OK i am now certain that my DNS server is supposed to be set as 192.168.1.1 - it is like that on windows. Now I used the terminal and did
'firefox www.weebls-stuff.com', and it started to load the webpage! and it said that I needed to download a plugin (most likely flash). Now I cannot get this to happen at all if I type in a URL into firefox itself. 

I can download packages using synaptic, and that obviously gets them from the internet. I get a response when pinging a website - 'ping -c4 www.google.com' etc. So I can actually access the internet perfectly well in theory. But I cannot go to any webpages really using firefox. sometimes it just hangs and times out, sometimes it starts to download and page and sometimes it actually starts to draw something on the screen! My connection is fine under windows, my signal strenght is good (i have a wireless network card) and I can downbload stuff perfectly using synaptic. However I cannot connect to the GAIM instant messenger using my MSN account. 

So Gaim and firefox don't work, but in theory they should as I can ping websites fine.

So do you think there could be another problem, not related to the DNS server settings?

---

