---
title: "Frostwire not connecting to internet"
date: 2008-11-13
forum: Desktop Environments
---

### Post by pvpkiran on 2008-11-13
Hi all,
   I installed Frostwire on my laptop.
But im not able to connect to internet. 

I have set the proxy and port(which i use in my browser) properly. But still it didnt help?

   Then i thought firewall may be blocking it. So i installed firestarter and disabled the firewall. Still didnt work ...

what could be the problem ?

Thank You

---

### Post by alwayshere on 2008-11-13
try reinstalling it by putting below in terminal 

sudo apt-get install frostwire

---

### Post by pvpkiran on 2008-11-13
Hi ,
  Thanx for the reply. 

But Frostwire is not in Ubuntu package. I hav to download the package and install using dpkg. 

Thas how i did it before

Thank You

---

### Post by Tomatz on 2008-11-13
Firestarter is probably blocking it also. Just set up port forwarding on your router and uninstall firestarter. Hardware based firewalls are always better ;)

[http://portforward.com/](http://portforward.com/) *(Look for a limewire howto here)*

---

### Post by pvpkiran on 2008-11-13
Hey thanx again.

  How to set up port forwarding on  router?

I hav uninstalled firestarter


Thanx

---

### Post by jolx on 2008-11-13
i had this problem and it was to do with the firewall

in the frostwire options under advanced > firewall, you might need to change the listening port. mine is set to 46427 but im on arch now so it might be different for you.

---

### Post by Tomatz on 2008-11-13
> **pvpkiran said:**
> Hey thanx again.

  How to set up port forwarding on  router?

I hav uninstalled firestarter


Thanx

Search the website in the link i posted ;)

---

### Post by jolx on 2008-11-13
> **pvpkiran said:**
> I hav uninstalled firestarter

firestarter isn't the firewall, it's just a (!out of date!) tool to configure the firewall which is known as iptables

---

### Post by Tomatz on 2008-11-13
> **jolx said:**
> firestarter isn't the firewall, it's just a (!out of date!) tool to configure the firewall which is known as iptables

Yeah it pretty much does what your router does but less securly ;)

---

### Post by pvpkiran on 2008-11-13
Hey guys thanx for the replies. 

  But still im not able to figure it out.

if i need to change the port number. To wat number shud i change? 

I cant change anything on the router , since im in my office network.

Any other way?


thank you

---

### Post by Tomatz on 2008-11-13
> **pvpkiran said:**
> Hey guys thanx for the replies. 

  But still im not able to figure it out.

if i need to change the port number. To wat number shud i change? 

I cant change anything on the router , since im in my office network.

Any other way?


thank you

Other than binning your router, no :(

Just get all the info you need, figure it out in your head and sort it when you get home.

---

### Post by alwayshere on 2008-11-13
what version os are you using (eg ubuntu 8.10)

maybe installing  gtk-gnutella may help ??

if you are using ubuntu 7.04 i have a fix for that somewhere i would have to find it

---

### Post by pvpkiran on 2008-11-14
Ya its 8.10 . ANy other way?

---

### Post by Tomatz on 2008-11-14
> **pvpkiran said:**
> Ya its 8.10 . ANy other way?

Using a different gnutella client (that doesnt even support upnp) wont help. As said, you need to port forward.

What is your router make and model number?

---

### Post by alwayshere on 2008-11-14
im outa  ideas  tomatz seems to be onto it

---

### Post by Tomatz on 2008-11-14
> **alwayshere said:**
> tomatz if you got the good idea i think he may want a how to /help

Thats why i asked for his router make and model number ;)

So i can tell him how to port forward it.

---

