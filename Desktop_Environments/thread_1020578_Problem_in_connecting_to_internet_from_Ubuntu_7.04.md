---
title: "Problem in connecting to internet from Ubuntu 7.04"
date: 2008-12-24
forum: Desktop Environments
---

### Post by balaji_n on 2008-12-24
Hi all,
This is my first post about ubuntu since i installed ubuntu 7.04 first time in my laptop (256 MB RAM). Its great to work but with one problem. It is not connecting to the internet.
I have an ADSL2 Router(450BXI). Ubuntu version i have installed is 7.04.

What i did till now:
Right after installing the OS, the ethernet connection was up and if you right click on the network symbol, the connection information showed 100mbps but the ip was 0.0.0.0. Also, if i try to open [www.google.com](www.google.com) firefox browser said 'server could not be found'. 
When i changed something in network, like changing the mode to static ip address, the connection got lost altogether and it is not detecting the ethernet link i feel. 

Please guide me to overcome this problem. Many Thanks in advance.

---

### Post by hrod beraht on 2008-12-24
> **balaji_n said:**
> When i changed something in network, like changing the mode to static ip address, the connection got lost altogether and it is not detecting the ethernet link i feel.

What exactly did you change in networking?
Does your **/etc/network/interfaces** file now look similar to this? (numbers may be slightly different depending on your network/router)
```
# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.0.100
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.1.0

```
Bob

---

### Post by balaji_n on 2008-12-24
Thanks for a quick repnly.

Out of the 5 listed, my interfaces file only have address, net mask and gateway. i have neither network not broadcast listed. Following is the interfaces file
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.1.15
netmask 255.255.255.0
gateway 192.168.1.1

auto eth1 ......

```

Bob, before you mention, i am not aware of this file. I changed the static ip thing and entered those address through GUI. Also added DNS address in that dialog box (4.2.2.1 and 4.2.2.2).I dont know whether this DNS thing is required, but after adding, firefox took little longer to come back with "404 error"

---

### Post by ugm6hr on 2008-12-24
> **balaji_n said:**
> This is my first post about ubuntu since i installed ubuntu 7.04 first time in my laptop (256 MB RAM).

7.04 is no longer supported.  I'd suggest you re-install a newer version (8.04 or 8.10).

---

### Post by balaji_n on 2008-12-25
Can my laptop with 256 MB RAM support 8.X version of Ubuntu..?

---

### Post by kostkon on 2008-12-25
> **balaji_n said:**
> Can my laptop with 256 MB RAM support 8.X version of Ubuntu..?
You could try the latest *Xubuntu*. It's very good and lightweight.

---

### Post by namdung on 2008-12-25
I second Hardy Heron 8.04.1 because it's LTS. Intrepid has more features than Hardy but more likely to have bugs. Hardy 8.04.2 is coming out in Jan 09.

Depending on ur hardware, u may consider Xubuntu.
[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

---

### Post by ugm6hr on 2008-12-25
> **balaji_n said:**
> Can my laptop with 256 MB RAM support 8.X version of Ubuntu..?

Definitely Xubuntu 8.04.  I'd recommend it.

The LiveCD will work if you have swap partition and separate graphics card RAM.

If not, I'd suggest the AlternateCD.

---

### Post by balaji_n on 2008-12-26
Thanks for all the linux souls! I fixed it.My brother was of great help. I did the following in succession and i dont know what made it work.
1.Deleted iftab file from /etc and reboot the machine
2.sudo ifconfig eth0 192.168.1.1 up, then did ping 192.168.1.1 and it worked!
3.sudo ifconfig eth0 up
4.sudo ifconfig eth0 192.168.1.5 (192.168.1.5 is the ip i assigned to my machine)
5.Now pinged 192.168.1.1, 192.168.1.2(my brother's laptop in the same network), ping [www.google.com](www.google.com) - all worked successfully and i am writing this post from Ubuntu. 
Hooray!
Happy New Year!

Regards,
Balaji N

---

### Post by ugm6hr on 2008-12-26
That's great.

But remember that 7.04 is still not supported.

---

