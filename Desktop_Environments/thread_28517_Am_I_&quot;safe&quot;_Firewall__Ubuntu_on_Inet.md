---
title: "Am I &quot;safe&quot;? Firewall / Ubuntu on Inet"
date: 2005-04-20
forum: Desktop Environments
---

### Post by fipeso on 2005-04-20
I just had to connect my Ubuntu PC directly to the Internet.

Now I wonder, is there any kind of "basic" firewall on this thing?

I have a "normall" Hoary install.

---

### Post by Leif on 2005-04-20
No, by default there is no firewall installed. If you want one, see [http://ubuntuguide.org/#firestarter](http://ubuntuguide.org/#firestarter)

---

### Post by fipeso on 2005-04-20
Thank you very much :)

I go right a head and install it then.

---

### Post by philipacamaniac on 2005-04-20
No firewall is installed by default. However, a clean Ubuntu install doesn't run any network daemons, so actually it is safe to connect directly to the Internet.

If you do a quick "nmap -vv -P0 Ubuntu_IP_Address" scan on a clean Ubuntu install, you won't find any exploitable services. You only need the firewall when you start forwarding ports and opening services. This ain't Winblows, after all.

---

### Post by shakin on 2005-04-20
A firewall is not needed. Nobody can possibly hack into a computer that is not listening for connections on a port.

The general purpose of a firewall is to block ports that need to be open, but you don't want them to be open from everywhere, or to apply other specialized rules to open ports. For instance, I have a firewall on my servers so SSH is not open to the world, but my static IP at work and a small range of dynamic IPs from home are allowed through on port 22.

On Windows a firewall is always necessary because it's impossible, so far as I know, to actually force Windows to stop from listening on certain ports. Many worms get in this way.

---

### Post by fipeso on 2005-04-20
WOW, that was EASY to install :D

And allready I got 2 serious eeer now 4 serious classed inbound events  :mad: 

Well the names are :
DCOM-scm 
Microsoft-ds

(now 5, they just keep poping in as I type this message)

Well I dont know what those are, but im glad this aint M$ Windows  \\:D/ 

I was a bit worried, as my PC has been a few hours without the firewall, but not any more, after reading your posts about Ubuntu being safe aven without the firewall :)

Thanks guys.

---

### Post by Sam on 2005-04-20
A little bit offtopic, but if you want to check your network/workstation's firewall configuration, check [grc.com](http://www.grc.com/default.htm) and follow the link "ShieldsUP!" on the 2/3 of the page. Click "Proceed" then "All Service Ports". It will scan the first 1056 TCP ports. Very useful ! :wink:

---

