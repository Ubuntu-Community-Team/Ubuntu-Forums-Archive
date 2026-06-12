---
title: "Configuring a Static Route in Ubuntu 8.10"
date: 2009-04-12
forum: General Help
---

### Post by icemanizaki on 2009-04-12
Ok, I installed Ubuntu,everything worked,when I tried to login for the first time, it froze. The screen just froze,but the mouse could move. So I went online (here),I got a few suggestion to try to do:  [B]sudo apt-get update
        sudo apt-get upgrade[/B]

When I do these commands,I get outputs saying that it can't find the ubuntu web site.  Then they suggested if that didn't work, I can try to check my network connection using the **ifconfig** command. I did that and all I get is the loopback address stuff, not eth0 or something else.  So I tried to put a static ip using the **sudo vi /etc/network/interfaces** command.  When I do this, I see

[B]auto lo
iface lo inet loopback[/B]

So do I put my ip network info below the stuff above (loopback stuff)? Or there is another way.

Please help, new to ubuntu.

---

### Post by hyper_ch on 2009-04-12
you need to edit /etc/network/interfaces, /etc/resolv.conf and remove the network manager (otherwise that will interfere).

Use something like the following in the interfaces fie:
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
allow-hotplug eth0
iface eth0 inet static
address 192.168.1.5
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.0.255
gateway 192.168.1.1

```

and something like this for the resolv.conf
```

nameserver 192.168.1.1

```

---

### Post by icemanizaki on 2009-04-13
> **hyper_ch said:**
> you need to edit /etc/network/interfaces, /etc/resolv.conf and remove the network manager (otherwise that will interfere).

Use something like the following in the interfaces fie:
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
allow-hotplug eth0
iface eth0 inet static
address 192.168.1.5
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.0.255
gateway 192.168.1.1

```

and something like this for the resolv.conf
```

nameserver 192.168.1.1

```
Ok,I've seen what you say somewhere.  When I do the **sudo vi /etc/network interfaces** command in the safe mode drop shell , I get 

[B]auto lo
iface lo inet loopback
~
~
~
~
~
~
~
~
~
~
~
[/B]
Is that how it suppose to look like when I put that command.

After I see the above I hit enter and go down and enter

[B][B]auto eth0
iface eth0 inet static
address *my ip here*
netmask *ip here*
network *ip here*
broadcast *ip here*
gateway i*p here*
[/B][/B]
then I put the command to save and close

**[B]sudo /itc/init.d/networking interface**[/B]

when I press enter, Nothing happens, it moves to the next line


Again when I do the ***ifconfig*** command, all I get is my loopback stuff

---

### Post by hyper_ch on 2009-04-13
/etc/network interfaces --> that's not a path to a file

---

