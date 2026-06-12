---
title: "connection problems"
date: 2009-05-02
forum: General Help
---

### Post by Jason_McKinley on 2009-05-02
**[SOLVED] Thanks for all the help!**

ok, I started my ubuntu and tried to use firefix but it keeps telling "address not found" The wired connection is showing up as connected, the connection info is showing up correct. I also connot update with update manager, everything is showing up as failed. If you need anymore information let me know.


Thanks for the time,
Jason

---

### Post by Peter09 on 2009-05-02
Go to a terminal and type
```
ifconfig
```

post the output here

---

### Post by Jason_McKinley on 2009-05-02
Ok, heres what i got off the ifconfig



```
eth0    Link encap:Ethernet  HWaddr 00:08:74:f7:fb:98  
          inet addr:192.168.254.1          Bcast:192.168.254.255  Mask:255.255.255.0
          inet6 addr:             fe80::208:74ff:fef7:fb98/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST          MTU:1500  Metric:1
          RX packets:88 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0         txqueuelen:100 
          RX bytes:15784 (15.7 KB)  TX bytes:1836 (1.8 KB)




lo      Link encap:Local Loopback  
         inet addr:127.0.0.1  Mask:255.0.0.0
         inet6 addr: ::1/128 Scope:Host
         UP LOOPBACK RUNNING  MTU:16436  Metric:1
         RX packets:128 errors:0 dropped:0 overruns:0 frame:0
         TX packets:128     errors:0 dropped:0 overruns:0 carrier:0
         collisions:0 txqueuelen:0 
         RX bytes:10304 (10.3 KB)  TX bytes:10304 (10.3 KB)




virbr0       Link encap:Ethernet  HWaddr f2:ca:e9:3c:22:6d  
                inet addr:192.168.122.1          Bcast:192.168.122.255  Mask:255.255.255.0
                 inet6 addr:         fe80::f0ca:e9ff:fe3c:226d/64 Scope:Link
                UP BROADCAST RUNNING MULTICAST          MTU:1500  Metric:1
                RX packets:0 errors:0 dropped:0 overruns:0 frame:0
                TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
                collisions:0         txqueuelen:0 
                RX bytes:0 (0.0 B)  TX bytes:468 (468.0 B)


```

---

### Post by Peter09 on 2009-05-02
Both your wireless and wired connections appear to be connected, but to different networks!

What is your setup, are you using a router or a modem to connect to the Internet. Are you using a static IP?

The problem does not appear to be with the connection itself but the network setup.

Edit: can you post the output of the ```
route
``` command

---

### Post by Jason_McKinley on 2009-05-02
> **Peter09 said:**
> Both your wireless and wired connections appear to be connected, but to different networks!

What is your setup, are you using a router or a modem to connect to the Internet. Are you using a static IP?

The problem does not appear to be with the connection itself but the network setup.


I'm using a modem to connect, and i'm not sure about my ip. Also I shouldn't have a wireless connection because the computer doesn't have a wireless card or anything. Letting me know how i can check my ip to see if its a static ip or not.


Heres the route code:
```

Kernel IP routing table

Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.254.0   *               255.255.255.0   U     1            0          0 eth0
192.168.122.0   *               255.255.255.0   U     0            0          0 virbr0
link-local             *               255.255.0.0       U     1000      0         0 eth0
default                192.168.254.254 0.0.0.0   UG    0           0          0 eth0

```

---

### Post by Peter09 on 2009-05-02
Can you post the output of the

```
route
```

command

---

### Post by Peter09 on 2009-05-02
Ahh - perhaps virbr0 is your modem connection (usb?) while eth0 is another connection?

---

### Post by Jason_McKinley on 2009-05-02
> **Peter09 said:**
> Ahh - perhaps virbr0 is your modem connection (usb?) while eth0 is another connection?

no. my only connection that i have is the ethernet, i don't have any connection through usb... although i do have a external hard drive attached.

---

### Post by Peter09 on 2009-05-02
Hi Jason, must admit I'm not sure I understand you network setup. Ifconfig is telling me that you have two connections, eth0 and vibr0 not sure what that means. 

Try 
```
tracepath www.google.com
```

that might tell us where your system is trying to get to.

---

### Post by Jason_McKinley on 2009-05-02
I get "unknown host" when i put in the code tracepath

---

### Post by lisati on 2009-05-02
It's got me puzzled: I agree that it looks like there are two networks. I'm wondering if the "vir" in "virbr" (which I haven't seen before) is an abbreviation of "virtual"....

---

### Post by Peter09 on 2009-05-02
Just got this off the internet

> "virbr0 192.168.122.0" is the virtual bridge network created by F8 VM  (virtual machine) implementation.
All guest machines hosted by the host machine will be part of this  192.168.122.0 network.  I imagine
you installed some package from the 'Virtual Machine' group.  If you  don't really need it, you can remove
the VM option and I think F8 would clean itself up.

So are you running in a virtual machine?

---

### Post by Jason_McKinley on 2009-05-02
> **lisati said:**
> It's got me puzzled: I agree that it looks like there are two networks. I'm wondering if the "vir" in "virbr" (which I haven't seen before) is an abbreviation of "virtual"....

could be be because i've been experimenting with get virtualbox working through my windows partition.

---

### Post by Peter09 on 2009-05-02
Well its certainly a bridged connection - virtualbox does not do this but I think it may be VMware or something similar. Normally in a bridged connection you will need to set the hardware interface (eth0) to 'promiscuous' mode to get things working with a bridged connection. 

What version of Ubuntu are you running?

---

### Post by Jason_McKinley on 2009-05-02
I'm running 9.04, is there a way to get rid of the virtual bridge? I don't see that i need it.

---

### Post by Peter09 on 2009-05-02
Well here is a bug report

[http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg1361035.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg1361035.html)

Still looking for the command to remove the bridge

---

### Post by Jason_McKinley on 2009-05-02
OK, good news guys, I removed all virtual machine programs from ubuntu and tried the internet then and it work! Thanks for all your time and effort in helping me find out the problem. I really appreciate it.



Thanks again,
Jason

---

