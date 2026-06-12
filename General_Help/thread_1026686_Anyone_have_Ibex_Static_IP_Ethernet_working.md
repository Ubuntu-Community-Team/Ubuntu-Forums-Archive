---
title: "Anyone have Ibex Static IP Ethernet working?"
date: 2008-12-31
forum: General Help
---

### Post by vav on 2008-12-31
It's disconcerting that an Ibex update broke my networking. And this isn't some glitzy new-to-desktop-linux hotplug wifi stuff that broke. It's basic, server-oriented-which-linux-is-historically, wired ethernet with static IP. 

Network Manager complains that the device is unmanaged since it has static ip, and ifupdown can't seem to understand the /etc/network/interfaces file and get the ethernet going.

Now I can make the device managed by disabling it's config in /etc/network/interfaces, but then Network manager gets me a dynamic IP which messes with my ssh setup! And of course setting static settings in network manager means it defers to ifupdown which barfs. And if I force a static IP, host resolution no longer works.

I can see others have experienced the same after one of the recent upgrades, but sadly no fix has come through my update manager. 
</end of rant>
So how do I fix it?

How do I get a static IP assigned to me every time I boot/reboot the computer in Ibex?

---

### Post by 2hot6ft2 on 2008-12-31
I have a static IP address assigned by my router. Lease time: Forever

Until I decide to change it that is.

---

### Post by wmdiem on 2008-12-31
Can't you just force the static address and define the DNS server in resolv.conf?

---

### Post by Titan8990 on 2008-12-31
You just need to put something like this in /etc/network/interfaces:

```
auto eth0
iface eth0 inet static
        address 192.168.0.100
        netmask 255.255.255.0
        gateway 192.168.0.1

```

Change IPs and interface name as needed. To restart networking:

sudo /etc/init.d/networking restart

---

### Post by 2hot6ft2 on 2008-12-31
I've read of others having problems trying to do that. A search might turn something up with a solution. I just let the router do it for both pc's myself.

Don't know if the router trying to change the ip address and the pc trying to keep it would be an issue or not.

---

### Post by Slim Odds on 2008-12-31
> **2hot6ft2 said:**
> I've read of others having problems trying to do that. A search might turn something up with a solution. I just let the router do it for both pc's myself.

Don't know if the router trying to change the ip address and the pc trying to keep it would be an issue or not.

These things are not magic. The router does not "try" to do anything. It does what it's told. You don't get a "static" IP address from a router, you get a dynamic IP address assigned by the router. But even in that case, the PC **asks** for the address from the router via DHCP.

The OP was asking about defining a static IP address. Sometimes this is what you want, so that you know that the address will not change.

On my home network, I setup the desktops with static IP addresses so that I can always know where they are. The laptops connect via DHCP and get dynamic IP addresses.

Under the System->Administration->Networking menu there is a GUI that will allow you do setup whatever configuration you want (I'm using 8.04),

---

### Post by vav on 2008-12-31
I don't have control over the router/gateway :( This is on a public network. Otherwise I would have just tied a fixed ip to my computers mac address.

I have a /etc/network/interfaces file that looks like that, but if I enable that (i.e. network manager says it's unmanaged), then It seems to connect but host resolution doesn't work so I can't connect to anything. Even ping with a numerical ip address doesn't work so I don't know if ifup has actually worked.

---

### Post by wmdiem on 2009-01-01
what does ifconfig give you?
If ping isn't working, then it probably isn't just host resolution that isn't working, but everything from ip up the stack. Are you sure you aren't duplicating another computer's ip address. Are you assigning it a static address that is on the same subnet as the router?

---

### Post by jongkind on 2009-01-01
> **vav said:**
> 
How do I get a static IP assigned to me every time I boot/reboot the computer in Ibex?

Wicd as alternative for network manager worked for me (and for lots of other people according to the network forum): wicd. It can be downloaded from here:

[http://wicd.sourceforge.net/]("http://wicd.sourceforge.net/")

---

### Post by ravi.xolve on 2009-01-01
I upgraded from 8.04 with a static ip. I use KDE, KNetworkManager didn't try to interfere and later I removed NetworkManager from init.

---

### Post by OneMixDJ on 2009-01-03
I upgraded to Ibex from Hardy.

What I will tell you (and sorry if this sounds retarded), but if I didn't hit Enter key on every entry I typed (IP, Netmask, DNS, etc...) it didn't save my entries. 

I learned this after enough failed attempts.
When I first installed Hardy I didn't have to do this.:-k

---

