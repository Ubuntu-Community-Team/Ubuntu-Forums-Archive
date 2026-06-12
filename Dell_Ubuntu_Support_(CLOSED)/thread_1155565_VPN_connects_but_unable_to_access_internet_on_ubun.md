---
title: "VPN connects but unable to access internet on ubuntu 9.04"
date: 2009-05-10
forum: Dell Ubuntu Support (CLOSED)
---

### Post by derrek.cooper on 2009-05-10
Setup vpn on ubuntu 9.04, mini 9. Connects successfully, but unable to connect to the internet once vpn is established?

If I disconnect from vpn, internet access is fine.

---

### Post by aot2002 on 2009-06-02
same here ive been trying to figure it out since vpnc works fine but cisco is not working even with a import of my .pcf file?

---

### Post by itoregon on 2009-07-20
> **derrek.cooper said:**
> Setup vpn on ubuntu 9.04, mini 9. Connects successfully, but unable to connect to the internet once vpn is established?

If I disconnect from vpn, internet access is fine.

Have you found a solution yet?   If not, one thing you will want to do is edit your VPN settings.  Under the "IPv4 Settings" tab, click on "Routes".  Once in there, check the box that says "Use this connection only for resources on it's network.  This makes it so the VPN is NOT used as the default internet connection which is what your problem is.  By default it is not checked so all your internet traffic is trying to go over the VPN.

I am using Ubuntu 9.04 "Jaunty Jackalope" with pptp-linux and Network-Manager-PPTP

I hope this helps you out.

Jaysen

---

### Post by ozgurk on 2009-07-27
It worked out for me :) thanks...

---

### Post by ericab on 2009-07-28
ok solution is here:

[http://ubuntuforums.org/showthread.p...61#post7598961](http://ubuntuforums.org/showthread.p...61#post7598961)

look specifically at 'ufw masquerading'

---

### Post by gewei on 2009-11-10
> **itoregon said:**
> Have you found a solution yet?   If not, one thing you will want to do is edit your VPN settings.  Under the "IPv4 Settings" tab, click on "Routes".  Once in there, check the box that says "Use this connection only for resources on it's network.  This makes it so the VPN is NOT used as the default internet connection which is what your problem is.  By default it is not checked so all your internet traffic is trying to go over the VPN.

I am using Ubuntu 9.04 "Jaunty Jackalope" with pptp-linux and Network-Manager-PPTP

I hope this helps you out.

Jaysen

This worked well for me, thanks

---

### Post by aot2002 on 2009-11-11
> **itoregon said:**
> have you found a solution yet?   If not, one thing you will want to do is edit your vpn settings.  Under the "ipv4 settings" tab, click on "routes".  Once in there, check the box that says "use this connection only for resources on it's network.  This makes it so the vpn is not used as the default internet connection which is what your problem is.  By default it is not checked so all your internet traffic is trying to go over the vpn.

I am using ubuntu 9.04 "jaunty jackalope" with pptp-linux and network-manager-pptp

i hope this helps you out.

Jaysen


perfect that works

---

