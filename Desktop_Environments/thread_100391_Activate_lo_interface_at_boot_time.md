---
title: "Activate lo interface at boot time"
date: 2005-12-07
forum: Desktop Environments
---

### Post by gatopolar on 2005-12-07
Hi
Could you tell me how to activate the lo interface at boot time. I have to activate it manually each time I boot my box (sudo ifconfig lo up)

Thank you in advance

Alvaro.

-------------------------------------
Here is my /etc/network/interfaces file:


# The loopback network interface
auto lo
     iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth1

# The primary network interface
iface eth1 inet dhcp

iface dsl-provider inet ppp
     provider dsl-provider

auto eth1

    iface eth1 inet manual

auto eth1

    iface eth1 inet manual

auto eth1

    iface eth1 inet manual

auto eth1

    iface eth1 inet manual

auto eth1

    iface eth1 inet manual

    pre-up /sbin/ifconfig eth1 up # line maintained by pppoeconf

---

### Post by GeneralZod on 2005-12-07
I'm no expert on interfaces, but I've just tried my (working!) /etc/network/interfaces file and have two lines under 

```

 iface lo inet loopback

```

that you don't, these being:

```

address 127.0.0.1
netmask 255.0.0.0

```

---

### Post by gatopolar on 2005-12-07
Thanks i will try it now..

A.

---

### Post by gatopolar on 2005-12-07
It did not work,
Some other idea?

Alvaro

---

### Post by GeneralZod on 2005-12-07
That's the only thing I could think of, unforttunately :/

---

