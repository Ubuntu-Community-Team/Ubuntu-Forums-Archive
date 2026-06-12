---
title: "Getting Static IP To Work"
date: 2005-09-04
forum: Desktop Environments
---

### Post by fortytwo on 2005-09-04
I just installed Kubuntu (been using ubuntu for about a year) and would like to finally do what I've been putting off for a long time...getting a static IP within our LAN so I don't need to change the port forwards whenever it gets a new IP from DHCP.

I went in and turned off DHCP and set the IP manually to 192.168.1.42 (Our DHCP starts giving addresses at 192.168.1.100).  This started out looking great...other machines on the network could access it through SSH and VNC, but when I tried accessing a website from that machine, I couldn't get through.

Do I need to do something else to be able to get outside the network after turning off DHCP for this machine?

Thanks a lot.

---

### Post by MrCheese on 2005-09-05
[QUOTE=fortytwo]I just installed Kubuntu (been using ubuntu for about a year) and would like to finally do what I've been putting off for a long time...getting a static IP within our LAN so I don't need to change the port forwards whenever it gets a new IP from DHCP.

I went in and turned off DHCP and set the IP manually to 192.168.1.42 (Our DHCP starts giving addresses at 192.168.1.100).  This started out looking great...other machines on the network could access it through SSH and VNC, but when I tried accessing a website from that machine, I couldn't get through.

Do I need to do something else to be able to get outside the network after turning off DHCP for this machine?

Thanks a lot.[/QUOTE]

make sure your default gateway is set to the lan ip of your router and that you have set up the dns server addresses as well.

---

### Post by fortytwo on 2005-09-05
[QUOTE=MrCheese]make sure your default gateway is set to the lan ip of your router and that you have set up the dns server addresses as well.[/QUOTE]
 I've set the default gateway to the lan address of the router, but do the DNS server addresses need to be different than how they were with DHCP enabled?  Also, what should the broadcast address be set to?

Thanks for the help.

---

### Post by Divan Santana on 2005-09-09
[QUOTE=fortytwo]I've set the default gateway to the lan address of the router, but do the DNS server addresses need to be different than how they were with DHCP enabled?  Also, what should the broadcast address be set to?

Thanks for the help.[/QUOTE]
[http://jodies.de/ipcalc](http://jodies.de/ipcalc)
The above link will help you calulate subnet mask, broadcast address etc!

It is most likely your gateway that is not set.(sometimes you set the default gw it doesnt work)

Try the command:
netstat -nr
and double check your gateway.

If not correct do:
sudo route add default gw ???.???.???.???

---

