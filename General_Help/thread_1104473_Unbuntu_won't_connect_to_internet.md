---
title: "Unbuntu won't connect to internet"
date: 2009-03-23
forum: General Help
---

### Post by xHumanity on 2009-03-23
I recently installed unbuntu 8.10 desktop edition
and it won't connect to the internet.
it shows my wired connection but its grayed out and wont let me select it all it lets me select is etho1 or sometihng

---

### Post by cariboo on 2009-03-23
In order for us to help you solve your problem we need more information. Open an Applications-->Accessories-->Termianl and type:

```
sudo lshw -C network
```

This will print out the details of your network adaptor. Please paste the output in your next post. Enclose the output in [noparse]```

```[/noparse] tags to make it easier to read.

Jim

---

### Post by xHumanity on 2009-03-23
that isnt working
can you contact me via aim or msn?

---

### Post by lisati on 2009-03-23
> **xHumanity said:**
> that isnt working
can you contact me via aim or msn?

Which isn't working? Going to Applications->acceosries->terminal, or the lshw command?

One option is to type the following in the terminal:
```
sudo lshw -C network > results.txt
```
This will create a file "results.txt" which you can then copy to the machine you're using to access the internet and then include it in your reply.

Replying through these forums is usually preferable to MSN or similar, because it gives a greater number of people the opportunity of helping.

---

### Post by xHumanity on 2009-03-23
> **lisati said:**
> Which isn't working? Going to Applications->acceosries->terminal, or the lshw command?

One option is to type the following in the terminal:
```
sudo lshw -C network > results.txt
```
This will create a file "results.txt" which you can then copy to the machine you're using to access the internet and then include it in your reply.

Replying through these forums is usually preferable to MSN or similar, because it gives a greater number of people the opportunity of helping.

whenever i try both of those it ask me for my password 
but it wont let me type it in
all i can do is hit enter and then it will say incorrect password attempt

---

### Post by lisati on 2009-03-23
> **xHumanity said:**
> whenever i try both of those it ask me for my password 
but it wont let me type it in
all i can do is hit enter and then it will say incorrect password attempt

When you type in your password at the terminal, it won't show (on purpose, so someone looking over your shoulder won't see it). Just type it in as normal.

---

### Post by xHumanity on 2009-03-23
```



*-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: 10
       serial: 00:19:e0:65:76:e5
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full latency=32 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
  *-network:1
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth1
       version: 78
       serial: 00:11:d8:3d:9c:76
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=half latency=32 link=no maxlatency=8 mingnt=3 module=via_rhine multicast=yes port=MII speed=10MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 7a:71:3e:81:61:23
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes


```

---

### Post by xHumanity on 2009-03-23
waits patiently.....

---

### Post by lisati on 2009-03-23
Info spotted..... 
Looks like networking is disabled.
(I'll just go and look to see if I can find out something about what to do about it)

---

### Post by lisati on 2009-03-23
> **lisati said:**
> Info spotted..... 
Looks like networking is disabled.
(I'll just go and look to see if I can find out something about what to do about it)

My bad: I misinterpreted the output. Anyone else is free to jump in and offer suggestions while I go look for something to help the OP.

---

### Post by lisati on 2009-03-23
> **lisati said:**
> My bad: I misinterpreted the output. Anyone else is free to jump in and offer suggestions while I go look for something to help the OP.

Question for xHumanity:
Is there a networking icon showing on the top of your screen? For a wired connection it usually looks like two little computers?

---

### Post by xHumanity on 2009-03-23
yes it is and when i click on it it shows my actual network connections
but they are grayed out

---

### Post by xHumanity on 2009-03-23
anyone help me...

---

### Post by xHumanity on 2009-03-23
is anyone going to help me....

---

### Post by xHumanity on 2009-03-23
you guys ******* blow.
thanks a bunch

---

