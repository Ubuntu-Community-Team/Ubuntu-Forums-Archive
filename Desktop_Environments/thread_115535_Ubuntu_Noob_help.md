---
title: "Ubuntu Noob help"
date: 2006-01-10
forum: Desktop Environments
---

### Post by _LOphT on 2006-01-10
k this is my first linux distro and so i have my xp box which is my primary box, than my secondary box (old computer) which i decided to set up so i can fool around with linux distros,

now all i need help with cuz i cant find it n e where is, how do i set up my internet connection on the second box. thx for help

sorry if this is very noob question but i cant find it n e where lol.

---

### Post by zoiks on 2006-01-10
Start with System|Admin|Networking.

---

### Post by darth_vector on 2006-01-10
what kind of internet connection are you thinking of using?

---

### Post by _LOphT on 2006-01-10
im using mts dsl highspeed

---

### Post by darth_vector on 2006-01-10
the easiest way to set up you internet connection would be to get a switch. you then will have to configure you IP, netmask, default gateway and dns. look at you windows machine, you will have very similar settings.

if your adsl modem/router supports DHCP then you wont even need to do this since the router will set up the interface for you. if you have (or can set up) DHCP on the router, edit the file /etc/network/interfaces as root
```
sudo gedit /etc/network/interfaces
```
and add the following
```

auto eth0
iface eth0 inet dhcp
```
and you will be ready to go after a network restart

---

### Post by _LOphT on 2006-01-10
darth vector i just did what u said and its still not connecting, n e one else got n e other resolutions?

---

### Post by leech on 2006-01-10
What sort of network card do you have in the system?

Run 'sudo ifconfig' and post here what it shows.

Leech

---

### Post by cotcot on 2006-01-11
The way to connect depends on your network connection. Dial-up, ADSL, cable , ...  .
Have a look to the ubuntu unofficial guide  :   [http://ubuntuguide.org/#networking](http://ubuntuguide.org/#networking)

Maybe you have to release your IP-lease (if you have one) when you swap from your new box to the old.

---

