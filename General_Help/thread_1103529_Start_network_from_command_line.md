---
title: "Start network from command line"
date: 2009-03-22
forum: General Help
---

### Post by millsy_c on 2009-03-22
Hi all, i've searched around to try and find a solution but unfortunately couldn't find one.
I'm having an issue getting gnome desktop manager installed on my ubuntu install.
I'm not really sure what I did (I'm still a huge ubuntu noob) but I rebooted and didn't get a gui, just the terminal.
So, I tried a few things for that that I saw on the net, and none of them worked. So, I uninstalled gnome and went to reinstall it, but when I do it says it doesn't have a network connection.
I know that my internet is currently working as I'm typing this from the same computer (I have a triple boot).
Is there a command to start network support? Or is something else up? I'd really like to get this going again and keep playing around with this great operating system :)
Thanks in advance

---

### Post by joseangelini on 2009-03-22
sudo /etc/init.d/networking start

---

### Post by millsy_c on 2009-03-22
> **joseangelini said:**
> sudo /etc/init.d/networking start

I'll give that a shot. Thanks heaps

---

### Post by millsy_c on 2009-03-22
Hey, I tried that but was still unable to connect. I checked with ifconfig and my computer was assigned an IP, but I cannot seem to connect to any online repositories.
I tried to ping my router, but it said something along the lines of no network connectivity or something like that.
Any ideas? I've changed the title of my original post to reflect the new issue.
*edit* Started a new, see [http://ubuntuforums.org/showthread.php?p=6940243#post6940243]("http://ubuntuforums.org/showthread.php?p=6940243#post6940243")

---

### Post by Prospero2006 on 2009-03-22
Here's how you handle it:
First, print the output of ifconfig here so we can see it.
Try to ping your router first:
 ```

ping ip_address_of_router

```

If you can't ping your router, I'd try configuring your netmask first:
 ```

sudo ifconfig eth0 netmask 255.255.255.0

```
This is assuming your card is recognized as eth0

You'll want to make sure your default gateway is correct as well:

```

route add default gw ip_address_of_gateway

```

Then try to ping the router.
Once you get the router ping up, it's time to ping Google.
If you can't ping Google, check /etc/resolv.conf and make
sure it has nameservers listed there.

Also, you can run this command
```

sudo dhclient eth0

```

That might bring things up on its own.

Hope that helps.

---

### Post by millsy_c on 2009-03-22
Okay, I'll see how it goes. My motherboard (x38 dq6) has 2 network ports, it might be going through the wrong one?
I'm surprised all this needs to happen, before i killed the gui it worked fine :(
I'll post back here with my results.

---

### Post by millsy_c on 2009-03-22
Okay, my ip settings are definitely wrong. I followed your instructions, but when I got to configuring the netmask, it wouldn't let me. It gave the following output:
```

SIOCSIFNETMASK: Cannot assign requested address

```

someone in another thread suggested /etc/resolv.conf , does that file contain these settings? If so, how do I edit them?

Currently it sets the ip as 127.0.0.1 and subnet as 255.0.0.0. I need it to be 10.0.0.x and 255.255.255.
I even tried sudo'ing bash because that's fixed an issue i had once with permissions but still no luck.
Is there perhaps another command I can use? Thanks heaps so far.

---

### Post by Prospero2006 on 2009-03-22
That 127.0.0.1 address is your loopback address.
Run this:
```

sudo ifconfig eth0 up
sudo ifconfig eth1 up
sudo ifconfig

```

Print results here.

---

### Post by millsy_c on 2009-03-22
Okay, it's a fair bit to post but here goes!

eth0  Link encasp: Ethernet HWaddr 00:1a:4d:5e:fd:d2
      UP Broadcast running multicast MTU:1500 Metric:1
      RX Packets:6 errors:0 dropped:0 overruns: 0 frame: 0
      TX 'same as above but all are 0'
      collisions 0 txqueuelen:1000
      RXBytes:552 (552.0B) TX Bytes: 0 (0.0B)
      Interrupt: 249 Base address: 0x6000

eth1 is the same but all values are 0 except the interrupt is 248, base address is 0xc00 and the HWaddr (is that the mac address?) is 00:1a:4d:5e:fd:d2

I hope this is of some use to you.

---

### Post by kevdog on 2009-03-23
Check out the thread in my signature about connecting from the command line!

---

### Post by Prospero2006 on 2009-03-23
sudo dhclient eth0

 ping [www.google.com](www.google.com)

sudo dhclient eth1 
   ping [www.google.com](www.google.com) 


?

---

### Post by millsy_c on 2009-03-23
> **kevdog said:**
> Check out the thread in my signature about connecting from the command line!

Thanks, i'll give it a shot after i've done some of this uni work :p

---

### Post by millsy_c on 2009-03-23
> **Prospero2006 said:**
> sudo dhclient eth0

 ping [www.google.com](www.google.com)

sudo dhclient eth1 
   ping [www.google.com](www.google.com) 


?

I figured seeing that if I didn't have an ip address it wouldn't work anyway?

---

