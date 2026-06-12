---
title: "How do I get connected??!?"
date: 2005-12-15
forum: Desktop Environments
---

### Post by Ingla on 2005-12-15
Hello.

I have Ubuntu on a hard drive which is failing. It connects fine using my USB modem. I installed Ubuntu on another HD, but it will not connect with the same modem driver, configuration, etc. Nobody seems to have a solution.

Therefore, I got an ether modem (Aztech DSL 600E). It's working fine on Windows.

However, I can't find any way to get in connected on Ubuntu! The help files are ridiculous (including the Unofficial Guide). They show me screenshots of networking tools which do not exist on my system. There is no way to configure anything! 

Nowhere does it say **how** to connect at all! All I see is that ether is activated (but not configured...and the configuration options don't seem relevant).

Getting connected is the most basic first step in getting Ubuntu going. How can there be such pathetically inadequate instructions??

Windows needed a driver (provided with the modem) and some minor configuration. And voila!

Can anyone give me a walk through on getting this going (newbie)?

Thanks very much.

---

### Post by 23meg on 2005-12-15
Did you know that [Linux is not Windows]("http://linux.oneandoneis2.org/LNW.htm")? If your device is detected by the kernel, it's most likely that you've been unable to configure it, so I suggest yo be calm and try focusing on solving your problem instead of bashing the documentation. 

In System / Administration / Networking do you see your eth device? If so, go into its properties and select DHCP in the configuration box. Then hit OK and in the Connection tab hit Activate, and choose your adapter as a default gateway in the combo box below. If DHCP isn't working, assign a static IP to your adapter in your router, and enter this IP after choosing "Static Ip Adress" in the Properties dialog. Enter 255.0.0.0 as Subnet Mask and your router's gateway adress (most likely 10.0.0.2 , try leaving blank as well) into the Default Gateway box.  That should be it.

---

### Post by Ingla on 2005-12-15
Hi.

Thank you for the reply.

Can you please elaborate?

1. I don't know what you mean by "choose your adapter as a default gateway". All I see is one option "eth0".

2. Also, how do I assign a static IP to my adapter in my router? I don't know what that means or what IP to assign or how to do it.

3. After doing all this, how do I connect? With the USB modem, I use the command line...which at least tells me something about what's going on. Using the drop down menu in Gnome to connect just creates icons on the Desktop which don't seem to do anything. If I double click or right-click>open, I just get a window which says "opening"...but never does.

The only way to find out if I'm connected is to open a browser and try a URL.

Can you enlighten me (in baby talk)?

Thanks very much.

---

### Post by tlc on 2005-12-15
In the properties section for your eth0 device, select DHCP. If you modem/router supports it, that's all you have to do. Fire up your browser and test. If you get an "unable to resolve www.whatever.com" type error then you need to tell your machine what DNS servers to use.

```
sudo nano /etc/resolv.conf
```

There should be two lines in this file:
```
nameserver x.x.x.x
nameserver x.x.x.x
```

The x's are the IP's of your DNS servers - your ISP should be able to tell you what the correct IP's are.

Then try browsing again. If it still doesn't work, go back to your eth0 properties and select "Use static IP" from the drop down box.

Then enter the IP you want to use for your computer in the top box, the subnet mask in the second (255.255.255.0 has always worked for me) and the IP of your modem/router in the bottom box. (10.0.0.2 or 192.168.0.1 or something - consult the instructions that came with it.) Your computer's IP should be in the same range as your modems - eg if your modem is 10.0.0.2, choose 10.0.0.3 or something as your IP.

When you've done all this, and hit Apply or Close or whatever button is at the bottom and try browsing again...

```
ifconfig -a
``` should tell you if your eth0 connection is alive or not.

---

### Post by Ingla on 2005-12-15
Hi.

Thanks for the reply.

Unfortunately, nothing has worked so far.

The documentation that came with the modem does not mention an IP. I tried the ones you suggested.

The DNS was wrong (I don't know where the listed one came from), but I entered the correct IP's.

I ran ifconfig -a

As I'm not connected on Linux, it's very hard to put up the output, which I don't understand. It was divided into three sections, eth0, something, and sit0. All showed no errors, etc.

The first two showed a number of bytes. sit0 showed 0.

I ran pppoeconf and got called away before I could finish. It said it found a DSL connector and asked if it should set it for this connection. I assume the answer is yes, but need to back up the current file first.

Also, I seem to recall that, during the Ubuntu installation, a message said that the system was unable to configure DHCP automatically, so that step was skipped. Do I need to configure it and , if so, how do I do it?

Thanks for the help.

Please try to explain the above (in baby talk).

Thanks

---

### Post by tlc on 2005-12-15
What happens if you start firefox and type, "http://192.168.1.1/" in the address bar?

From reading the Aztec site it looks like that's the default interface address for most of their routers.

---

