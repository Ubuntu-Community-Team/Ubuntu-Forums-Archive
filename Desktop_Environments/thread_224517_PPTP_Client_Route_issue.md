---
title: "PPTP Client :Route issue ??"
date: 2006-07-28
forum: Desktop Environments
---

### Post by TheH on 2006-07-28
Hi,



I have two OS's on my laptop (D620) , both configured to dial in to the VPN server of my work but only the XP one works and is passing traffic. Ubuntu connects and gets an ip of the VPN server but is not passing traffic and my entire internet doesn't work if i use the tunnel.



I think the issue is in the Routes not beeing set up but i don't have a clue which route i should at to my linux box in order for it to work..



Windows XP routes (Working config)



```


Interface List

0x1 ........................... MS TCP Loopback interface

0x2 ...00 13 02 a5 05 d5 ...... Intel(R) PRO/Wireless 3945ABG Network Connection

 - Packet Scheduler Miniport

0x10004 ...00 14 22 fb 4b 83 ...... Broadcom NetXtreme 57xx Gigabit Controller -

 Packet Scheduler Miniport

0x20005 ...00 53 45 00 00 00 ...... WAN (PPP/SLIP) Interface

===========================================================================

===========================================================================

Active Routes:

Network Destination        Netmask          Gateway       Interface  Metric

          0.0.0.0          0.0.0.0     172.16.0.211    172.16.0.211       1

          0.0.0.0          0.0.0.0      192.168.9.1     192.168.9.7       26

     70.183.24.xx  255.255.255.255      192.168.9.1     192.168.9.7       25

        127.0.0.0        255.0.0.0        127.0.0.1       127.0.0.1       1

     172.16.0.211  255.255.255.255        127.0.0.1       127.0.0.1       50

   172.16.255.255  255.255.255.255     172.16.0.211    172.16.0.211       50

      192.168.9.0    255.255.255.0      192.168.9.7     192.168.9.7       25

      192.168.9.7  255.255.255.255        127.0.0.1       127.0.0.1       25

    192.168.9.255  255.255.255.255      192.168.9.7     192.168.9.7       25

        224.0.0.0        240.0.0.0      192.168.9.7     192.168.9.7       25

        224.0.0.0        240.0.0.0     172.16.0.211    172.16.0.211       1

  255.255.255.255  255.255.255.255     172.16.0.211    172.16.0.211       1

  255.255.255.255  255.255.255.255      192.168.9.7           10004       1

  255.255.255.255  255.255.255.255      192.168.9.7     192.168.9.7       1

Default Gateway:      172.16.0.211

===========================================================================

Persistent Routes:

  None




```





Ubuntu linux Routes (and debug info)

```


# route -n (after completion)
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
172.16.0.210    0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
70.183.24.xx    192.168.9.1     255.255.255.255 UGH   0      0        0 eth1
192.168.9.0     0.0.0.0         255.255.255.0   U     0      0        0 eth1
10.0.0.0        0.0.0.0         255.0.0.0       U     0      0        0 ppp0
0.0.0.0         192.168.9.1     0.0.0.0         UG    0      0        0 eth1


```

If i can sort out this problem I have everything working on ubuntu so hopefully someone can help me out ! Thanks alot

Tom

---

### Post by OpsVentus on 2006-07-28
Hello Tom,

How do you connect to the internet? via eth1? your ip is 192.168.9.*? and your router is 192.168.9.1?
What program do you use to setup your VPN connection?

The problem of internet failing when you connect to VPN is a routing problem. Instead of only passing the trafic you want through VPN it tries to put everything through there and the VPN server on the other side dosn't allow this.

Cheers,
Bart.

---

### Post by TheH on 2006-07-28
Eth1 is my wireless adapter which connects to our router which is (192.168.9.1) 
I am using pptpconfig to setup my connection.

Thanks,

---

