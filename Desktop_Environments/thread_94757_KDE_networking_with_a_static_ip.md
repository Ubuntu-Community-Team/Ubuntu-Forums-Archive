---
title: "KDE networking with a static ip?"
date: 2005-11-24
forum: Desktop Environments
---

### Post by wabble on 2005-11-24
I am on the kubuntu wagon again. I now have my networking "working" as long as i use dhcp. I can not store any profiles as of yet.

So what do i do? I need the static ip the way my network is set up at home. I have read alot about problems with networking and admin access but no solution seems to work. I have both wired and wireless devices.

---

### Post by HermanAB on 2005-11-24
I'm sure Ubuntu will have a wizard for it, but the simplest way is to edit a file.

On a RedHat-ish system, it is like this.  I don't have a running Ubuntu now to confirm, but it should be similar enough that you can figure it out:

Edit file /etc/sysconfig/network-scripts/ifcfg-eth0.  

Change: 
BOOTPROTO=dhcp to BOOTPROTO=static

Add: 
IPADDR=1.2.3.4

Then do 'service network restart'

'Hope that helps!

Herman
[http://www.aerospacesoftware.com/linuxhowtos.html](http://www.aerospacesoftware.com/linuxhowtos.html)

---

### Post by ltmon on 2005-11-24
The settings for a static IP are in there.  I'm not at my home pc now so I can't check, but if you start kcontrol there will be a "Networking" section.

In there will be the option to configure each of your known interfaces (e.g. eth0), and the option to turn of DHCP and use a static IP is pretty obvious.

L.

---

### Post by wabble on 2005-11-25
[QUOTE=ltmon]The settings for a static IP are in there.  I'm not at my home pc now so I can't check, but if you start kcontrol there will be a "Networking" section.

In there will be the option to configure each of your known interfaces (e.g. eth0), and the option to turn of DHCP and use a static IP is pretty obvious.

L.[/QUOTE]

I know, i know.

But my network locks up the second i set a manual ip in either kcontrol or systemsettings no matter how i start the apps (kdesu from alt+F2, sudo from konsole). And when i set it back to dhcp it works with no issues. Also when i try to save a profile it does not save the profile, but the gateway ip and card to the gateway are sometimes lost and sometimes stay as the same with additional hostnames added in the hosts. So this is my problem when i am on a laptop and need to use different networks and a static ip with some of them.

Well i will check in the forums later, but weekend is weekend. Have a good one :smile:

---

### Post by wabble on 2005-11-25
[QUOTE=HermanAB]I'm sure Ubuntu will have a wizard for it, but the simplest way is to edit a file.

On a RedHat-ish system, it is like this.  I don't have a running Ubuntu now to confirm, but it should be similar enough that you can figure it out:

Edit file /etc/sysconfig/network-scripts/ifcfg-eth0.  

Change: 
BOOTPROTO=dhcp to BOOTPROTO=static

Add: 
IPADDR=1.2.3.4

Then do 'service network restart'

'Hope that helps!

Herman
[http://www.aerospacesoftware.com/linuxhowtos.html](http://www.aerospacesoftware.com/linuxhowtos.html)[/QUOTE]

Yes i have been thinking about polishing my shell know how. This is kubuntu only issue by the way. I have no problems in ubuntu what so ever.

---

### Post by the_it on 2005-11-25
gui based network editing in linux is known to be fraught with the occasional problem when saving the settings, especially in kde.

But you didn't tell us how your networking was hanging.  Kindly supply some of the details:

-are you setting up a unit to serve files to others, and the files don't appear elsewhere?
or
-are you setting up a unit simply as an internet client?

generally, you'll have to make sure that the following nuances were set properly.
1) ip address/ subnet mask
2) router/gateway (if you have one, this is typically your DSL modem if you have one)
3) DNS servers (if you use them.  You don't need to put this in if your router automatically does the DNS searching for you)

to check your ipaddress, try
```
/sbin/ifconfig
```
and note what ip comes out of eth0 (or whatever device you've got)

to check your gateway/router, try
```
/sbin/route
```
and note what the default gateway is.

If you don't have a default gw in the list but you need one, you can add it using
```
sudo /sbin/route add default gw x.x.x.x
```
where x.x.x.x is the address of your default gw

this is where gui tools usually fail (mandrake was notorious for this one)

to check if your dns works. try
```
ping www.google.com
```

---

### Post by GeneralZod on 2005-11-25
[QUOTE=wabble]I know, i know.
 Also when i try to save a profile it does not save the profile, but the gateway ip and card to the gateway are sometimes lost and sometimes stay as the same with additional hostnames added in the hosts[/QUOTE]

I've noticed this, too.  I'll file a bug report later today.

---

### Post by wabble on 2005-11-25
[QUOTE=the_it]gui based network editing in linux is known to be fraught with the occasional problem when saving the settings, especially in kde.

But you didn't tell us how your networking was hanging.  Kindly supply some of the details:

-are you setting up a unit to serve files to others, and the files don't appear elsewhere?
or
-are you setting up a unit simply as an internet client?

generally, you'll have to make sure that the following nuances were set properly.
1) ip address/ subnet mask
2) router/gateway (if you have one, this is typically your DSL modem if you have one)
3) DNS servers (if you use them.  You don't need to put this in if your router automatically does the DNS searching for you)

to check your ipaddress, try
```
/sbin/ifconfig
```
and note what ip comes out of eth0 (or whatever device you've got)

to check your gateway/router, try
```
/sbin/route
```
and note what the default gateway is.

If you don't have a default gw in the list but you need one, you can add it using
```
sudo /sbin/route add default gw x.x.x.x
```
where x.x.x.x is the address of your default gw

this is where gui tools usually fail (mandrake was notorious for this one)

to check if your dns works. try
```
ping www.google.com
```[/QUOTE]

Ok, i know networking so the settings them self is not an issue (they are correct ;) ).

The tools does not save the information and work (Yes the gateway and gateway device) But even when set i still got no connection when set to a static ip as soon as eth device is set to dhcp it all works. So how to make it all work on a static ip?

The kwifi always reports signals but ip unavailalble when set to static (i don't remember if it reported ip when dhcp was enabled on the wireless (cant check it right now)).

As of the task at hand. I want to set up networking for both internet and mounting nfs folders on a server when at home. And i also want to set up networking at work and all the other places i bring my laptop. So this is a big task when the tools are not working because i dont know much about configuring anything from command line except the hosts file.

I can do all of this when i get around to how to set static ip on my eth devices. The only help i need is to get a static ip up and running. The problem i think is that it does not store gateway info even if it reports it as stored in the gui config tool. I will try what you wrote here on monday and see if it works out.

Thanks for the help for now :)

---

### Post by GeneralZod on 2005-11-25
Just in case it helps, here is my /etc/network/interfaces (which i had to tweak manually to get things like the "gateway" to show up :)).  eth1 is an unused Ethernet thingummy which I haven't gotten around to removing yet.

```

 This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

# The primary network interface
iface eth0 inet static
        # wireless-* options are implemented by the wireless-tools package
        wireless-mode managed
        wireless-essid <my router essid>
        address 192.168.1.110
        netmask 255.255.255.0
        gateway 192.168.1.1

iface eth1 inet dhcp

auto eth0

```

---

### Post by wabble on 2005-11-25
[QUOTE=GeneralZod]I've noticed this, too.  I'll file a bug report later today.[/QUOTE]

Ok, when you do could you put a link to the bug reported here?

---

### Post by wabble on 2005-11-25
GeneralZod thanks!

I am sure i can make something of it on monday when i get back home. Will post back then.

---

### Post by GeneralZod on 2005-11-25
[QUOTE=wabble]Ok, when you do could you put a link to the bug reported here?[/QUOTE]

Sure! :)

[https://bugzilla.ubuntu.com/show_bug.cgi?id=20094](https://bugzilla.ubuntu.com/show_bug.cgi?id=20094)

---

### Post by wabble on 2005-11-28
[QUOTE=GeneralZod]Sure! :)

[https://bugzilla.ubuntu.com/show_bug.cgi?id=20094](https://bugzilla.ubuntu.com/show_bug.cgi?id=20094)[/QUOTE]

Ok, i got it working back home now. But i have to say.. It's kind of a slow solution when moving around ;)

Thanks for the help :smile:

---

