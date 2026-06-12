---
title: "Manual Configuration for Wireless connection disabled"
date: 2011-05-08
forum: Desktop Environments
---

### Post by tim042849 on 2011-05-08
My home network is manually configured with static IP addresses.
I can connect to my network and to the internet with network
manager on an HP mini 110 netbook using ubuntu 10.10 and DHCP,
but I cannot make a manual static DNS connection. If I choose
**manual** from the **Method** dropdown list under
**IPv4 Settings** the [COLOR="Red"]apply[/COLOR] button is disabled.
Any help would be appreciated!
I have posted this problem in the past and never gotten an answer!
thanks
tim

---

### Post by matt_symes on 2011-05-08
Hi

Silly, silly question but you have entered your IP, netmask and gateway address and the apply button is still disabled ?

Do you have a screen shot ?

Kind regards

---

### Post by tim042849 on 2011-05-08
> **matt_symes said:**
> Hi

Silly, silly question but you have entered your IP, netmask and gateway address and the apply button is still disabled ?

Do you have a screen shot ?

Kind regards
Not a silly question at all. :confused: I tried to take a screen
shot with the settings IP Address, netmask, gateway, DNS servers,
and search domains entered and the apply button disabled. I
somehow bungled the screen shot, which also closed the 
**Edit Connections** window, then when I re-opened the
window I found that the **apply** button was enabled and
I was able to set a manual connection!

After many tries, I am at a loss as to why it now works, but I
have a vague theory. Now this is a netbook with a 10-inch
screen. When the **Edit connections** window is opened, the
**cancel** and **apply** buttons are not visible, and
I have to move the window upward. I wonder if the graphics display is causing this?

Any ideas?
Thanks for the reply. 
tim

---

### Post by matt_symes on 2011-05-08
Hi

> Any ideas?To be honest, i have no idea why it's working now. I am just glad it is.

If you want to change them manually because you are having problems with the GUI have a look in 

```
/etc/NetworkManager/system-connections
```On my machine
```

matthew@matthew-laptop:~$ ls /etc/NetworkManager/system-connections/ -l
total 4
-rw------- 1 root root 454 2011-05-09 00:59 Auto eth0
matthew@matthew-laptop:~$ 
```Notice the permissions.

```

matthew@matthew-laptop:/etc/NetworkManager/system-connections$ sudo cat Auto\ eth0 

[connection]
id=Auto eth0
uuid=XXXXXXXXXXXXXXXXXXXXX
type=802-3-ethernet
autoconnect=true
timestamp=0

[ipv4]
method=manual
addresses1=192.168.1.30;24;192.168.1.1;
ignore-auto-routes=false
ignore-auto-dns=false
dhcp-send-hostname=false
never-default=false

[802-3-ethernet]
speed=0
duplex=full
auto-negotiate=true
mac-address=XXXXXXX
mtu=0

[ipv6]
method=ignore
ignore-auto-routes=false
ignore-auto-dns=false
never-default=false
matthew@matthew-laptop:/etc/NetworkManager/system-connections$ 
```Some of the details redacted above. Although i have never tried to change it manually i believe you can from here. 

BTW: I love the selection of operating systems in your signature. Anybody would have though you were addicted to Linux ;)

Kind regards

---

### Post by tim042849 on 2011-05-08
I note your instructions for /etc/NetworkManager/system-connections, and I am now even more baffled. There is no file
there! On my main work station, my eth0 connection is called
**Auto eth0** and there is a file named
**/etc/NetworkManager/system-connections/Auto eth0**, as
in your example.
My connection on the netbook is called **Auto timsrouter**,
and I expect to find **/etc/NetworkManager/system-connections/Auto timsrouter**, but there is no such file there. Can't see it
from mc, or from the shell or from nautilus. [COLOR="DarkRed"]Any ideas for where
else it could be stored?[/COLOR]
Also, a tried a new wireless connection with the same problem with
the disabled **display button**.
:)Oh, and about the various distros. I need to add to my sig **asus** linux. **That** wireless network manager worked
flawlessly with DHCP, static, whatever. Go figure.
thanks again

---

### Post by matt_symes on 2011-05-08
Hi

> My connection on the netbook is called **Auto timsrouter**,
and I expect to find **/etc/NetworkManager/system-connections/Auto timsrouter**, but there is no such file there. Can't see it
from mc, or from the shell or from nautilus. [COLOR=DarkRed]Any ideas for where
else it could be stored?[/COLOR]

Now you have me baffled. I'm not sure what to make of that. You have a vanilla install of 10.10 with NetworkManager ?

You could try greping the file system as root looking for your IP address or even better, your MAC address. It will take ages but it should find it.

The only other place is can think it might be is in the GConf settings. Install gconf-editor to make it easy (if it's not installed) and have a look under /system/networking/connections.

Please inform me of what you find. I am interested.

Kind regards
[COLOR=DarkRed][/COLOR]

---

### Post by tim042849 on 2011-05-08
Stayed tuned. I'm grep'ing my brains out.

---

### Post by tim042849 on 2011-05-08
Matt, here's what I am finding: It looks like
1)Network manager is using and has written to /etc/hosts and /etc/resolve.conf
2)And ~/.gconf/system/networking/connections has xml files which
by their timestamp appear to be modified around bootup time.

I'd like to make a couple of comments here:
1)I really appreciate your (matt) help. It has helped me
to get a better grasp of the issue, although we have not solved
the issue of the **apply** button, at least we know have
eyes looking at it.
2)I disagree with ubuntu's **black-boxing** of network management and what appears to be a **unfriendly** environment
for those of us using manual DNS. Having said that, I can attest
that DHCP connections are no-brainers to use and I can adapt to
that. 
 
System administrators and other network professionals will have similar and perhaps more enduring disagreements.

Good thread. Time to get used to DHCP.
I do not believe that it would be appropriate for me at
this time to label this thread as solved. But again, kudos
to Matt for his help.

cheers
tim

---

### Post by matt_symes on 2011-05-09
Hi

Sorry for the late reply. Timezones and all that.

> **tim042849 said:**
> Matt, here's what I am finding: It looks like
1)Network manager is using and has written to /etc/hosts and /etc/resolve.conf


Yes. Network manager likes to overwrite /etc/resolve.conf with any nameservers it gets from a DCHP server. This has caused me issues in the past.

The only way i could get around it was to make the file immutable.

```
sudo chattr +i /etc/resolv.conf
```Not so sure about /etc/hosts but it does something similar i expect

> 2)And ~/.gconf/system/networking/connections has xml files which
by their timestamp appear to be modified around bootup time.On my laptop, this is where network manager keeps info about my DHCP wireless connections. One again, it reads/modifies them at startup. Obviously the keys are kept in the keyring.

> 
I'd like to make a couple of comments here:
1)I really appreciate your (matt) help. It has helped me
to get a better grasp of the issue, although we have not solved
the issue of the **apply** button, at least we know have
eyes looking at it.
2)I disagree with ubuntu's **black-boxing** of network management and what appears to be a **unfriendly** environment
for those of us using manual DNS. Having said that, I can attest
that DHCP connections are no-brainers to use and I can adapt to
that. 

System administrators and other network professionals will have similar and perhaps more enduring disagreements.Glad to help. Not that i was really much help, but it has been interesting discourse.

I understand what you mean about network manager hiding details from one. It was designed this way. What i read the other day, that i did not know, was that Network Manager was written by Red Hat back in ~2004/2005. The original  design decisions were hide  as many of the inner workings from the user. Its main focus was to make roaming easier on wireless networks  and they kind of shoehorned wired connections into it as well. This is fine if that's what you need, but requires research to see what's going on under the bonnet and time is a valuable commodity.
 
You could just uninstall Network Manager and use the old way of connecting to networks.

If you find where its storing the info for your connection then please tell me as that would also help me out for a project i am working on.

Kind regards

---

### Post by tim042849 on 2011-05-09
Matt, I will keep this on my radar and inform you if I have more
info. It appears that I have a static DNS now, but I'm going to resign myself to using the DHCP Method when/if that doesn't work.

For My my purposes, it is enough to know that network shares are
mounted under **~/.gvfs** so that I can synchronize some directories between the netbook and my workstation.

Using the old method, which to me is removing NM and working directly from
/etc/networking/interfaces, would make roaming difficult. I found that
what I traveled last month with this unit that NM was spot on at every
wireless connection I came across, using DHCP.

Talk to you later
tim

---

