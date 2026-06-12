---
title: "Proxy software"
date: 2009-07-29
forum: Desktop Environments
---

### Post by alimooghashang on 2009-07-29
hi all,
i need a proxy software the same as freegate or ultrasurf for ubuntu 9.04.
in m country facebook is filtered.
i need a proxy software for it in ubuntu.
thanks all

---

### Post by asmoore82 on 2009-07-29
maybe Privoxy
it's in the repos.

---

### Post by alimooghashang on 2009-07-29
> **asmoore82 said:**
> maybe Privoxy
it's in the repos.
thanks
how to use it?
does it retrieve the Ips automaticly?

---

### Post by dawgonit on 2009-07-29
I just started using this free VPN. Can you use it?

[http://itshidden.com](http://itshidden.com)

---

### Post by alimooghashang on 2009-07-29
> **dawgonit said:**
> I just started using this free VPN. Can you use it?

[http://itshidden.com](http://itshidden.com)
how to use this in ubuntu?
thanks

---

### Post by zzzqzzz on 2009-07-29
> **asmoore82 said:**
> maybe Privoxy
it's in the repos.

Privoxy is OK but it is intended to be use for anonymous surfing. You need to give an external proxy address to the Privoxy to overcome limitation of your ISP.
In that case if you know such external proxy you can use it directly from you browser. :)

if you don't want to search for free public proxies. (sometimes these proxies are also blocked by your ISP and not stable) I suggest you to use "TOR + Privioxy" or "yourfreedom" It will be little bit slow surfing experience but it is the safest method I have ever know

---

### Post by dawgonit on 2009-07-29
Follow these instructions. Some have trouble some do not. There is a thread about that I will try to find again.

[http://ubuntu-chronicles.blogspot.com/2009/07/jaunty-vpn-itshiddencom.html](http://ubuntu-chronicles.blogspot.com/2009/07/jaunty-vpn-itshiddencom.html)

here is the problem thread

[http://ubuntuforums.org/showthread.php?t=1224517](http://ubuntuforums.org/showthread.php?t=1224517)

---

### Post by zzzqzzz on 2009-07-29
[https://help.ubuntu.com/community/TOR](https://help.ubuntu.com/community/TOR)


[http://www.your-freedom.net/](http://www.your-freedom.net/)

---

### Post by philcamlin on 2009-07-29
> **dawgonit said:**
> I just started using this free VPN. Can you use it?

[http://itshidden.com](http://itshidden.com)

thanks for the site :popcorn:

---

### Post by alimooghashang on 2009-07-29
i have just config the same as this 
[http://free.korben.info/index.php/VPN#Sous_Ubuntu](http://free.korben.info/index.php/VPN#Sous_Ubuntu)

but it doesn't connect
says connect fail.
i don't know what to do.

---

### Post by alimooghashang on 2009-07-29
> **philcamlin said:**
> thanks for the site :popcorn:
thanks
it connected successfully
is this VPN free for ever?

---

### Post by dawgonit on 2009-07-29
What does your log file in messages say? My problem was my firewall and I was able to fix that. 

I saw someone else had entered the wrong password for the default keyring. They simply opened home folder and view hidden settings. They then deleted the key file from ./gnome2/keyring.

They then tried to connect again and used the same password they used for registering the user vpn account and it worked for them.

---

### Post by dawgonit on 2009-07-29
I'm not sure. I'm only using it until my metropipe account gets enabled which I pay for VPN. I know them and trust them but do not know the other free one. It is just convenient for the time being.

---

### Post by alimooghashang on 2009-07-29
> **dawgonit said:**
> I'm not sure. I'm only using it until my metropipe account gets enabled which I pay for VPN. I know them and trust them but do not know the other free one. It is just convenient for the time being.
thanks
it seems that is a freeone
and god knows what will happen
by the way
thanks all for help

---

### Post by dawgonit on 2009-07-29
type in firefox url bar > about:config

double left click to change it from false to true

> network.proxy.socks_remote_dns  true

This lets remote (not your ISP) DNS hook you up.

A little more privacy.

Restart FF

---

