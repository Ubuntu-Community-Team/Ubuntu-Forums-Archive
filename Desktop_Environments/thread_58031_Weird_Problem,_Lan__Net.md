---
title: "Weird Problem, Lan / Net"
date: 2005-08-18
forum: Desktop Environments
---

### Post by AndreAPL on 2005-08-18
Hi there. I have a strange problem. another computer is serving internet by lan,and it works fine in windowz in this computer. but, don't know how, i couldn't get internet anymore in here  :neutral:  so made ifconfig (ifconfig  eth2 (in this case,to my realtek) )and route (route  add -host default gw 192.168.0.1) command manually, having lan... but not net  :roll: it can ping the lan also...

Gateway : 192.168.0.1 / 255.255.255.0
This computer: 192.168.0.2 (tryed 192.168.0.xxx and DHCP) netmask: 255.255.255.0 gateway 192.168.0.1 ...

what is wrong ? any idea ?
and how can i get this ifconfig/route command updated automatically in linux? can't remender  ](*,) 

thanks

---

### Post by pmjdebruijn on 2005-08-18
Hi,

I don't think the -host part is necessary...

Also, it's better to use the configs in /etc/network/interfaces.

Open that file and declare something like this:

```
iface eth2 inet static
  address 192.168.0.2
  netmask 255.255.255.0
  gateway 192.168.0.1
```

Then save the file, and do 'ifdown eth2', and 'ifup eth2'.

Regards,
Pascal de Bruijn

---

### Post by schdefan on 2005-08-18
Hi!
Check out the DNS of your provider. You can find the two IP adresses in /etc/resolv.conf of your gateway or they should be on the website of your provider.

Add these two IP adresses to your client also into /etc/resolv.conf and do a 
```
sudo /etc/init.d/networking restart
```

This will work without DHCP! If you use DHCP the server should do that for you i think, but i am not sure.
Good luck
schdefan

---

### Post by AndreAPL on 2006-04-16
thanks, that's it. 
now have another problem, it says that /etc/resolv.conf is not a symbolic link to /etc/resolvconf/update(...)/resolv.conf ....
now it doesn't update by himself :/

---

