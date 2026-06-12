---
title: "Ubuntu Won't Save my DNS Nameservers"
date: 2006-02-01
forum: Desktop Environments
---

### Post by Ingla on 2006-02-01
Hello.

I have had Ubuntu working for several months on an old hard drive, which sounds like it isn't too healthy. Therefore, I decided to install it on a new hard disk. From then on, I've had nothing but trouble.

To make a long story short, I installed it using the original installation CD. I got connected and everything was OK. Then Automatic Update wanted to give me the newest stuff, as I had expected. I said OK and it installed 504 files. 

After that, Ubuntu would not save my DNS nameservers. Every time I rebooted or turned off the machine, the nameservers were gone when I came back in. I asked for help on the forum but no one replied.

I decided that, perhaps, something was wrong with the upgrade, so I downloaded  the latest ISO and installed Ubuntu again. The installation seemed fine. I could tell I had a later version because of the appearance of the Desktop and because the Terminal was in Accessories instead of System Tools.

 I activated the connection and edited the DNS nameservers and could move around the Internet OK.

BUT, once again, each time I go out, I have to re-edit the nameservers to get connected. I've tried the following:

System>Adminitration>Networking: The connection remains activated and configured, but the nameservers have been replaced by the IP of my router. I delete the entry and type in the correct server IP's.

sudo gedit /etc/resolv.conf:
Edited the nameservers AND SAVED THE FILE.

I did the same thing as root.

I've tried just turning of the machine and turning it off, while checking the option "Save Current Settings".

(On the old installation - after the upgrade - the system even changed my nameservers back IN THE MIDDLE OF THE SESSION, while I was writing a post here...I haven't stayed around long enough to see if that's happening now.)

This makes using Ubuntu very hard. I have to reconfigure it every time I boot in just to get connected.

Has anyone heard of such a problem? Can anyone tell me how to make Ubuntu save resolv.conf once and for all (or an other way to get the job done)?

Any help greatly appreciated.

Thanks.

---

### Post by awi on 2006-02-01
Are you using a DHCP Server for network configuration? Usually the dhcpclient overwrites the /etc/resolv.conf every time it gets the configuracion.

---

### Post by Ingla on 2006-02-01
Hello.

Thanks for the reply.

I'm afraid I'm pretty much a newbie, so I'm not sure what you mean by a DHCP server. Unless it's part of the system "out of the box", I'm not using anything.

I have an ethernet router which, under Windows, was using a dialup connection configured according to the instructions of my ISP. I never succeeded in getting it to connect under Ubuntu. So, I went into the router admin pages, using Firefox, and noticed it did not have my usual username and password that I used to connect via my USB modem. I entered the data and, since then, the dialup doesn't work on Windows...I'm automatically connected by the router. This happens under Ubuntu as well (the router admin shows I'm connected). The only problem is the disappearing nameservers.

Whatever is overwriting this is not a client I'm using, but part of the Ubuntu system (Idon't know what that uses to connect).

Any ideas?

Thanks very much

---

### Post by Ingla on 2006-02-01
Hi.

Since I wrote the previous post, I went into the router's admin with Firefox and looked around. I found that it IS using a DHCP server. I turned it off and rebooted into Windows a couple of times. Everything was fine...automatically connected as always.

Ubuntu was another story. While booting, it said configuring network interface "ok" BUT then switched to what looked like a console screen and said "Waiting for network interface to come up". It stayed like that a long time and finally said "fail".

When I got into Ubuntu, I couldn't access the router admin in Firefox. It looks like Ubuntu needs that server.

I also found that it deletes my nameservers in the middle of the session. I might be able to fix that in admin by looking for and disabling a "disconnect when idle" function or something like that. I haven't tried that yet.

Any ideas how I can stop it from overwriting /etc/resolv.conf at every disconnect?

Thanks.

---

### Post by Ramses de Norre on 2006-02-01
Is it still overwritten when DHCP is turned off? Your DHCP server is your router, it means that your router sends all the network settings to your computer so that he's configured automatically. Maybe your DHCP is configured wrong on your router (I experienced that myself) you could check it at the router page. Probably it has wrong DNS servers there (=nameservers). Other option is to turn off DHCP and give in the IP adres of your computer, the default gateway (IP of your router) and your DNS servers yourself on your computer, you need at least to set the gateway and your computer's IP to be able to connect to the router page when DHCP is turned off.

---

### Post by awi on 2006-02-01
Take a look at this post: 

[http://ubuntuforums.org/showpost.php?p=685713&postcount=8](http://ubuntuforums.org/showpost.php?p=685713&postcount=8)

it maybe solve your problem

---

### Post by Ingla on 2006-02-06
Thanks very much for all the help.

Problem solved.

I couldn't get the router to stop disconnecting periodically and overwriting my nameservers. Also, of course they were gone on reboot.

So, I set Networking to use a static IP. That wouldn't work either, until I realized someone had installed a second ether card and the router was trying to run from eth1 instead of eth0. It still wouldn't connect until I finally deactivated the eth0 connection. That's all it took! Just took a long time to figure it out.

When I rebooted, eth0 had been activated again, but I'm fully connected anyway.

Now I have a new problem with multimedia streaming. If anyone knows how to make that work, I would very much appreciate it if you would answer my post at: [http://ubuntuforums.org/showthread.php?t=126493](http://ubuntuforums.org/showthread.php?t=126493)

Thanks again.

---

### Post by David L. on 2006-02-12
"Ubuntu would not save my DNS nameservers. Every time I rebooted or turned off the machine, the nameservers were gone when I came back in."

I have exactly the same problem and only one ethernet card in my system. Just like Ingla, I have to re-edit the nameservers (System > Administration > Networking) every time I boot up just to get connected. One consequence of this is that Ubuntu cannot synchronise the system clock with the ubuntulinux ntp server while it is booting up but the main problem is the inconvenience. I am doing the obvious thing of clicking on "Add" when I have changed the IPs on the DNS tab and also checking the option to "Save Current Settings" when shutting down but it doesn't make any difference. I only have to change one digit of each IP each time but still, it is a nuisance. My computer is connected to the internet via a router, sharing a broadband connection with a Windows XP user who needed to save the DNS IPs once and once only.

Anyone got a solution? I'm sure it must be very simple!

---

### Post by Ingla on 2006-02-12
Hi.

The way it worked for me was like this.

Awi pointed out (above in this thread) that the DHCP client overwrites the DNS nameservers in  /etc/resolv.conf every time (and, in my case, from time to time due to some sort of time out). I hadn't thought I was using a DHCP client...but I found that the router was...and needed it.

The solution was to set the connection for a static IP instead of DHCP.

First you have to know your router's IP. If you don't, type:
-------------------------------------------------------------
route -n
-------------------------------------------------------------
This will generate several columns and rows of information. You're looking for an IP address that has "UG" in the same row, under the column marked "flags". That's the router's IP.

Go to System>Administration>Networking. Select your connection and go to Properties. Of course, the "Enable this connection" box must be checked. In the "drop down" menu called "Configuration", select "Static IP" instead of "DHCP". 

Type your router's IP in the third field "Gateway address". The first field, "IP Address" is an IP YOU assign to your adapter. It should be in the same series as your router's IP. For example, if the router's IP is, say, 10.2.1.1, make your IP 10.2.1.2 ... or the like.

When I clicked on the middle field, "Subnet mask", it filled itself in. If it doesn't, try 255.0.0.0. Someone told me, in another thread, that he used 255.255.255.0. One of those should work.

When you've done all that, click "OK" and then "OK" again.

You can also type your router's IP in your browser's address bar. That should take you into admin. You might need to call your ISP or the provider of your router to get a password (if you see a user name but no password, try typing the user name AS the password as well). 

Be careful about changing things in there...don't disable the DHCP client, for example, or the router probably won't work at all. You'd have to reboot the machine (at least) and possibly reset the router even to get back into admin!

However, you can see things like the proper subnet mask and various settings.

If I recall, I still had a little trouble until I rebooted. On boot, it took longer to bring up the network interface (still does) AND I noticed that, for the first time, it synchronized the clock on the way in.

As you say, it really isn't so hard...you just have to get the right numbers in there.

Good luck.

---

### Post by David L. on 2006-02-14
This solution worked really well for me, thanks Ingla and awi. Web pages are loading much faster than with DHCP, on boot up the clock synchronises with the ubuntulinux server and it doesn't appear to take any longer to bring up the network interface.

---

### Post by tomj on 2006-09-21
I'm having this problem as well. When i first installed ubuntu there were no problems when i setup static ip address's it remembered the DNS ip address fine. However i installed the KDE desktop so i could see what it was like. After deciding i preffered GNOME i unistalled it and now everytime i reboot it forgets the DNS server. It is set for static ip.

---

