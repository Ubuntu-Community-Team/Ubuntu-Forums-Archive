---
title: "updating KDE, yet keeping breezy"
date: 2006-08-21
forum: Desktop Environments
---

### Post by KhaaL on 2006-08-21
Hey all

I wonder how I can update KDE to the latest version without having to upgrade my breezy kubuntu to dapper?

(I'm keeping it since my WLAN card works in breezy and not in dapper)

I tried to add in the KDE repo, but i ended up having error messages...

---

### Post by Princey on 2006-08-21
> **Khalid Rashid said:**
> Hey all

I wonder how I can update KDE to the latest version without having to upgrade my breezy kubuntu to dapper?

(I'm keeping it since my WLAN card works in breezy and not in dapper)

I tried to add in the KDE repo, but i ended up having error messages...

kde isn't kubuntu. So upgrading kde to the latest version won't upgrade breezy to dapper. Just make sure you include the right sources in the sources.list.

---

### Post by fdoving on 2006-08-21
Hi.
You can't. 
KDE 3.5.4 is not backported to breezy. 
I strongly recommend upgrading to dapper.

What is your network card name and number?

---

### Post by KhaaL on 2006-08-21
> **fdoving said:**
> Hi.
You can't. 
KDE 3.5.4 is not backported to breezy. 
I strongly recommend upgrading to dapper.

What is your network card name and number?

Hi, my cards name isn't very distinct, its a Ericsson card with the following numers on it:

Type: HA691, product identity: KRD 901 39/1 R1A


It works without any problem in breezy, in dapper it dosen't to seem to work correctly (it shows as a 802.11NG - not as 802.11b as it should be). it sees my router but it refuses to connect to it.

---

### Post by fdoving on 2006-08-21
What kernel module does it use in breezy?

---

### Post by KhaaL on 2006-08-21
> **fdoving said:**
> What kernel module does it use in breezy?

I have no idea how to check that... care to share? :)

---

### Post by fdoving on 2006-08-21
Can you post the output of 'lshw', or if you run 'lshw|less' and scroll down till you find the device you will see something like this:

```

        *-network
             description: Wireless interface
             product: BCM4306 802.11b/g Wireless LAN Controller
             vendor: Broadcom Corporation
             physical id: 12
             bus info: pci@10:12.0
             logical name: eth1
             version: 03
             serial: 00:11:XX:XX:XX
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical wireless
             configuration: broadcast=yes driver=bcm43xx driverversion=2.6.17-6-powerpc ip=XXX.XXX.XXX.XXX link=yes multicast=yes wireless=IEEE 80
2.11b/g
             resources: iomemory:80084000-80085fff irq:52

```


As you can see it says
```

driver=bcm43xx

```

then bcm43xx is the driver (kernel module)


- Frode

---

