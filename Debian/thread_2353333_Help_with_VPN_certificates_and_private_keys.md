---
title: "Help with VPN certificates and private keys"
date: 2017-02-20
forum: Debian
---

### Post by issh on 2017-02-20
Hello, I am trying to connect to OpenVPN on my Debian laptop. I don't want to set up a server, I just want to connect and use VPN. However I don't know how to fill in 3 categories to make the connection work. What do I put in 'User Certificate', 'CA Certificate', and 'Private Key?' I have attached an image below. 


[http://i.imgur.com/8jlPLXj.png](http://i.imgur.com/8jlPLXj.png)


I've attached another image below, if I change the authentication type from 'TLS' to 'Password' it seems more simple. I know that username and password is just...

"vpn" and "vpn" 

...according to the VPNGate website, but what do I put in 'CA Certificate?'


[http://i.imgur.com/NiW9rPk.png](http://i.imgur.com/NiW9rPk.png)


In addition, if you know of any better or even easier methods of connecting to OpenVPN servers, would you post them here?

I am running Debian 8.7.1 "Jessie" AMD64
Dell Latitude D630
Intel T7100 CPU

I am posting here because in other places I have posted there doesn't seem to be any support. 
Thank you in advance for any help.

---

### Post by wildmanne39 on 2017-02-20
*Thread moved to **Debian**.*

Please use thumbnails or Url's when posting images because many people have slow internet connections or limited band width.

---

### Post by issh on 2017-02-20
> **wildmanne39 said:**
> *Thread moved to **Debian**.*

Please use thumbnails or Url's when posting images because many people have slow internet connections or limited band width.

Okay, thank you.

---

### Post by bearlake on 2017-02-21
> **issh said:**
> Hello, I am trying to connect to OpenVPN on my Debian laptop. I don't want to set up a server, I just want to connect and use VPN. However I don't know how to fill in 3 categories to make the connection work. What do I put in 'User Certificate', 'CA Certificate', and 'Private Key?' I have attached an image below. 


[http://i.imgur.com/8jlPLXj.png](http://i.imgur.com/8jlPLXj.png)


I've attached another image below, if I change the authentication type from 'TLS' to 'Password' it seems more simple. I know that username and password is just...

"vpn" and "vpn" 

...according to the VPNGate website, but what do I put in 'CA Certificate?'


[http://i.imgur.com/NiW9rPk.png](http://i.imgur.com/NiW9rPk.png)


In addition, if you know of any better or even easier methods of connecting to OpenVPN servers, would you post them here?

I am running Debian 8.7.1 "Jessie" AMD64
Dell Latitude D630
Intel T7100 CPU

I am posting here because in other places I have posted there doesn't seem to be any support. 
Thank you in advance for any help.

Hi,
 
What vpn service are you using or are you just going from one of your computers to another one of your computers?

With most services they will have you download the keys and cert from there site.

---

### Post by issh on 2017-02-21
> **bearlake said:**
> Hi,

What vpn service are you using or are you just going from one of your computers to another one of your computers?

With most services they will have you download the keys and cert from there site.

Thank you for replying. I get my vpn service from this website, [http://www.vpngate.net/en/](http://www.vpngate.net/en/)

I haven't been able to find anything regarding certificates there either.

---

### Post by bearlake on 2017-02-22
> **issh said:**
> Thank you for replying. I get my vpn service from this website, [http://www.vpngate.net/en/](http://www.vpngate.net/en/)

I haven't been able to find anything regarding certificates there either.

I went to the site posted and selected openvpn only, refresh servers and picked one choice. See screen shot.

---

### Post by bearlake on 2017-02-22
Sorry should of added, but just an after thought.

One of the VPN sites liked by many, but not free.

[PIA]("https://www.privateinternetaccess.com/pages/buy-vpn/")

---

