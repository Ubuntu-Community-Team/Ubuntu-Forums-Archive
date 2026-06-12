---
title: "Internet connection issues"
date: 2005-10-17
forum: Desktop Environments
---

### Post by pegaso on 2005-10-17
Hi I am a newbie of last night.

I installed 5.04 and then 5.10 when I found out about it. I have windows XP on one disk drive and Ubuntu Linux 5.10 on a second disk drive.

The wholw thing works fine. I have a problem connecting to the internet. I have a Dlink modem router/ wireless  connected to the broadband connection. All other computers are on windows and wireless and connect ok. My machine is connected by cable to the router and on windows works ok. 

I can see all the computers on the network and can ping the router and also ping the broadband address. I therefore think the hardware side is ok. (I may be wrong) I feel my configuration may be at fault. I have tried various configurations in Firefox settings and the network set up configurations. As I am new to this OS could someone advise me what information is needed to allow you to assist me please.

BTW I am on BT broad band and have a wires only connection.


Best Regards


Peter :-)

---

### Post by dzonekl on 2005-10-18
I had similar issue: 

Type about:config in firefox URL field
filter ipv6
set network.dns.disableIPv6 to true

solved my problem for firefox, but not for other net apps.....
Cheers / Christophe

---

### Post by pegaso on 2005-10-18
[QUOTE=dzonekl]I had similar issue: 

Type about:config in firefox URL field
filter ipv6
set network.dns.disableIPv6 to true

solved my problem for firefox, but not for other net apps.....
Cheers / Christophe[/QUOTE]

Thanks very much for the reply. As you suggested it worked straight away. I still have to get mail working but I now know the connection, cards etc work. I can work on the other things later.

Thanks again, much apreciated.

Regards Peter

---

### Post by dzonekl on 2005-10-19
Hi, Good to hear it helped. I am rounding up similar cases to make a stronger case to whoever can do something about the network issue. 
I hope we can make a case and log a bugreport/configbug report: 

Symptons: 
- Eth0 up, DHCP address assigned, Gateway can be pinged but no other address:
- All net apps fail, firefox can be made to work with IPV6 DNS disabled. 


Possible cause: 
 - Some v6 routing getting in the way of v4 routing??
 - Some DNS problem. 

Please reply to this e-mail if you have this problem with 5.10
(Post your ifconfig and route printout). 
Please help us out if you are good in Linux networking to help troubleshoot. 

Cheers / Christophe

---

### Post by pegaso on 2005-10-19
[QUOTE=dzonekl]Hi, Good to hear it helped. I am rounding up similar cases to make a stronger case to whoever can do something about the network issue. 
I hope we can make a case and log a bugreport/configbug report: 

Symptons: 
- Eth0 up, DHCP address assigned, Gateway can be pinged but no other address:
- All net apps fail, firefox can be made to work with IPV6 DNS disabled. 


Possible cause: 
 - Some v6 routing getting in the way of v4 routing??
 - Some DNS problem. 

Please reply to this e-mail if you have this problem with 5.10
(Post your ifconfig and route printout). 
Please help us out if you are good in Linux networking to help troubleshoot. 

Cheers / Christophe[/QUOTE]


I am using 5.10. I can post ifconfig and route printout but have starting using this OS three days ago and am still finding my way around. If you tel me where to find them I will post them.

Regards Peter

---

### Post by marcolinux on 2005-10-20
hi! 
i've got (maybe) same problem...
i'm using kubuntu 5.10.
i've got a network card and here i've got working internet lan connection (but only after typing sudo route add gateway etc from console...)

but when i try to use my serial modem i can't browse anything.
i've chmodified pppd in order to have users access, i've got dns in resolv.conf and in kppp configuration, but when i ping or browse i didn't have a response.
kppp log correctly and minimize near clock, but i can't access internet!
also networking administration tool hang up searching for linux distribution. on (k)ubuntu 5.04 i was prompt to choose which distribution, but now it simply hang searching...
until yesterday everything works inside mepis, but i want to use kubuntu!

i think it could be a gateway problem... any idea?

thank!
marco

---

### Post by Gordonbp531 on 2005-10-20
[QUOTE=dzonekl]
Symptons: 
- Eth0 up, DHCP address assigned, Gateway can be pinged but no other address:
- All net apps fail, firefox can be made to work with IPV6 DNS disabled. 


Possible cause: 
 - Some v6 routing getting in the way of v4 routing??
 - Some DNS problem. 

Cheers / Christophe[/QUOTE]

I had exactly this problem with all my distros due to the way my router is set up. (The router is supplied by my wife's company and is pre-configured and completely inaccessible - but they do pay for the broadband!)

The solution is to edit /etc/dhc3/dhclient.conf and unremark the line "prepend...." and replace the default dns with your ISP's dns.

HTH

---

### Post by pegaso on 2005-10-20
[QUOTE=gendibal]I had exactly this problem with all my distros due to the way my router is set up. (The router is supplied by my wife's company and is pre-configured and completely inaccessible - but they do pay for the broadband!)

The solution is to edit /etc/dhc3/dhclient.conf and unremark the line "prepend...." and replace the default dns with your ISP's dns.

HTH[/QUOTE]

I found the file ok but can't modify it. It is read only and I can't change permissions as I am not the owner. I thought I was but am not. The owner is root. Obviously I am missing something. Any idea how to change the owner please? I can't get over the speed of this OS and would love to get it fully working. Then I can forget Windose and all its problems.

Regards Peter

---

### Post by Efwis on 2005-10-20
[QUOTE=pegaso]I found the file ok but can't modify it. It is read only and I can't change permissions as I am not the owner. I thought I was but am not. The owner is root. Obviously I am missing something. Any idea how to change the owner please? I can't get over the speed of this OS and would love to get it fully working. Then I can forget Windose and all its problems.

Regards Peter[/QUOTE]
to do this type or copy and paste the following:

```

sudo gedit /etc/dhc3/dhclient.conf

```

This will open gedit/text editor with permissions to modify the file.

---

### Post by pegaso on 2005-10-21
[QUOTE=Efwis]to do this type or copy and paste the following:

```

sudo gedit /etc/dhc3/dhclient.conf

```

This will open gedit/text editor with permissions to modify the file.[/QUOTE]

Thanks very much I will try it when I get home tonight.

Regards Peter

---

### Post by pegaso on 2005-10-21
[QUOTE=pegaso]Thanks very much I will try it when I get home tonight.

Regards Peter[/QUOTE]

worked well

I thought it hadn't worked as a delay occured but all of a sudden files started pouring in, mail poured in. Thanks very much for the advice.

Best Regards Peter

---

### Post by Efwis on 2005-10-21
[QUOTE=pegaso]worked well

I thought it hadn't worked as a delay occured but all of a sudden files started pouring in, mail poured in. Thanks very much for the advice.

Best Regards Peter[/QUOTE]
glad you got it up and running have fun :)

---

### Post by drtvasudevan on 2005-10-21
[QUOTE=dzonekl]Hi, Good to hear it......
Possible cause: 
 - Some v6 routing getting in the way of v4 routing??
 - Some DNS problem. 

Please reply to this e-mail if you have this problem with 5.10
(Post your ifconfig and route printout). 
Please help us out if you are good in Linux networking to help troubleshoot. 

Cheers / Christophe[/QUOTE]

i have had the same problem.
and solved by this very method.
but when i use win xp the firefox has the same settings of having the disableIPv6 value false and it works.
it is only in linux (distroes after distroes have the same problem suse, ubuntu,slackware...) that the problem arises.:confused: 

tv

---

### Post by Efwis on 2005-10-22
[QUOTE=drtvasudevan]i have had the same problem.
and solved by this very method.
but when i use win xp the firefox has the same settings of having the disableIPv6 value false and it works.
it is only in linux (distroes after distroes have the same problem suse, ubuntu,slackware...) that the problem arises.:confused: 

tv[/QUOTE]
based on that it sounds like its a bug report that needs to told to Mozilla developers. I didnt' have this issue but I don't use a gateway setup.

---

### Post by dzonekl on 2005-10-22
Thanks, solved my problem as well. (Noticed immidiatly after reboot, The NTP synchronization worked when loading the modules). 

It's interresting that ubuntu is not able to configure it's IP DNS from the router. 
This is never an issue in windows. I vote this is a BUG or misconfiguration and
should be fixed. 
 
So you know, and from this post I judge many other users have this problem. 
I am a first time user of linux and already lost 2-3 days trying to solve this problem.  I don't think this is the first impression people should get, as sofar I love the looks, the feel and the speed of ubuntu. 

Cheers / Christophe

---

