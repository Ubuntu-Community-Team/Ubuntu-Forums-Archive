---
title: "Hibernate cause internet disconnect on waking"
date: 2009-01-30
forum: General Help
---

### Post by Lunx on 2009-01-30
Hi folks, wondering if someone can help me with a hibernate problem? I have no problem using the feature, however when I wake computer up and log in to my desktop, I lose my internet connection and can't seem to reconnect unless I reboot without hibernating. Any suggestions gratefully accepted 'coz I'd really like to use it, and trying to solve this is doing my head in:???:

---

### Post by earthpigg on 2009-01-30
wired or wireless?

have you tried unchecking 'enable networking' and rechecking it in the network manager (little computer networkey icon thingie in the upper right by default)?

---

### Post by Lunx on 2009-01-30
> **earthpigg said:**
> wired or wireless?

have you tried unchecking 'enable networking' and rechecking it in the network manager (little computer networkey icon thingie in the upper right by default)?

Cheers earthpigg, I'm on wired connection. I'll give what you suggest a try and see how I get on.

---

### Post by Lunx on 2009-01-30
Nup, tried messing with network settings and still disconnects me with no way of reconnecting that I can work out apart from rebooting. That's no good 'coz it makes hibernation a waste of time. :confused:

---

### Post by Coder543 on 2009-01-30
Have you tried 'sleep' mode instead of 'hibernate'? It uses only a bare minimum power and resumes rather quickly. If that isn't really an option go ahead and reboot - connect to internet - hibernate - unhibernate - go to Applications -> Accessories -> Terminal then type 'ifconfig' into the terminal (without quotes, obviously). Post the resulting mumbo jumbo.

---

### Post by Lunx on 2009-01-30
> **Coder543 said:**
> Have you tried 'sleep' mode instead of 'hibernate'? It uses only a bare minimum power and resumes rather quickly. If that isn't really an option go ahead and reboot - connect to internet - hibernate - unhibernate - go to Applications -> Accessories -> Terminal then type 'ifconfig' into the terminal (without quotes, obviously). Post the resulting mumbo jumbo.

Here's the mumbo jumbo   :)

pete@pete-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1a:4d:72:f5:c7  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:221 

eth1      Link encap:Ethernet  HWaddr 00:01:27:05:16:f5  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::201:27ff:fe05:16f5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:17883 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11287 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:18549768 (18.5 MB)  TX bytes:956735 (956.7 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3078 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3078 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:754540 (754.5 KB)  TX bytes:754540 (754.5 KB)

---

### Post by neur0 on 2009-01-30
To diagnose exactly what's wrong with your net connection after Hibernate, please do the following and copy all the output to a text file (for posting it later):

1. reboot

on the terminal do
2.
```
ifconfig -a
```
3.
```
route -n
```
4.
```
cat /etc/resolv.conf
```
5. Then do hibernate
6. Then do steps 2,3,4 and compare it to the output of the same commands from before.
7. Post before and after output where there is a difference.

8. See if doing
```
sudo /etc/init.d/networking restart
```
solves the problem after hibernate.

---

### Post by Lunx on 2009-01-31
> **neur0 said:**
> To diagnose exactly what's wrong with your net connection after Hibernate, please do the following and copy all the output to a text file (for posting it later):


Thanks for helping with that info, sorry I didn't reply earlier. Very busy ATM, but will try that shortly and post outcome soon(ish)

---

### Post by Lunx on 2009-01-31
Tried again and here's a copy of what I found, I've highlighted blue and red the bits I see are different 

```

pete@pete-desktop:~$ ifconfig -a (first)
eth0      Link encap:Ethernet  HWaddr 00:1a:4d:72:f5:c7  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:221 

[COLOR="Blue"]eth1      Link encap:Ethernet  HWaddr 00:01:27:05:16:f5  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::201:27ff:fe05:16f5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:19059 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11270 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:24261923 (24.2 MB)  TX bytes:626927 (626.9 KB)[/COLOR]

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
       [COLOR="Blue"]   RX packets:20 errors:0[/COLOR] dropped:0 overruns:0 frame:0
          [COLOR="#0000ff"]TX packets:20 errors:0[/COLOR] dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1088 (1.0 KB)  TX bytes:1088 (1.0 KB)

pan0      Link encap:Ethernet  HWaddr 0a:2a:77:f9:65:42  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

pete@pete-desktop:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth1
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 eth1
[COLOR="#0000ff"]pete@pete-desktop:~$ cat /etc/resolv.conf
# Generated by NetworkManager
nameserver 192.168.1.254
pete@pete-desktop:~$ [/COLOR]

________________________________________________________


pete@pete-desktop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:1a:4d:72:f5:c7  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:221 

eth1   [COLOR="Red"]   Link encap:Ethernet  HWaddr 00:01:27:05:16:f5  
          inet6 addr: fe80::201:27ff:fe05:16f5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1233 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1262 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:828050 (828.0 KB)  TX bytes:237681 (237.6 KB)[/COLOR]

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
        [COLOR="#ff0000"]  RX packets:68 errors[/COLOR]:0 dropped:0 overruns:0 frame:0
          [COLOR="Red"]TX packets:68 errors[/COLOR]:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4912 (4.9 KB)  TX bytes:4912 (4.9 KB)

pan0      Link encap:Ethernet  HWaddr ca:ee:4d:b0:fb:78  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

pete@pete-desktop:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
[COLOR="#ff0000"]pete@pete-desktop:~$ cat /etc/resolve.conf
cat: /etc/resolve.conf: No such file or directory
pete@pete-desktop:~$ [/COLOR]


```

No idea where I go from here...

---

### Post by neur0 on 2009-01-31
What motherboard are you using?

did you try: 
```
sudo /etc/init.d/networking restart
```
?

Which version of Ubuntu are you using and is it updated?

Here is a link to a similar problem, but it seems to have got solved in updates.
[https://bugs.launchpad.net/ubuntu/+source/acpi/+bug/111282](https://bugs.launchpad.net/ubuntu/+source/acpi/+bug/111282)

---

### Post by Lunx on 2009-01-31
> **neur0 said:**
> What motherboard are you using?

did you try: 
```
sudo /etc/init.d/networking restart
```
?

Which version of Ubuntu are you using and is it updated?

Here is a link to a similar problem, but it seems to have got solved in updates.
[https://bugs.launchpad.net/ubuntu/+source/acpi/+bug/111282](https://bugs.launchpad.net/ubuntu/+source/acpi/+bug/111282)

Motherboard is Gigabyte S-series 945GM and I'm running 2x Intel(R) Pentium(R) Dual CPU E2180 @ 2.00GHz with 1GB RAM

I'm running Intrepid and it's all up to date as of this morning.

Did try
```
sudo /etc/init.d/networking restart
```

Not sure if I did it right though, do I hibernate and wake up, then run that command while 'puter is still disconnected? (sorry, still coming to terms with a lot of this new stuff)

---

### Post by Lunx on 2009-01-31
Also ran Hardware Testing and it all worked fine apart from question about internet connection. Said it couldn't detect connection even though I am. Sent report off to Lauchpad, but what happens with that now? Does it give me some sort of feed back on what problem is :confused:

---

### Post by neur0 on 2009-01-31
Well, it seems that some people are having the same problem (though it seems very rare)
like in
[http://ubuntuforums.org/showthread.php?t=491945](http://ubuntuforums.org/showthread.php?t=491945)

Yes, try

```
sudo /etc/init.d/networking restart
```
In the terminal after resume, it should ask you for a password, and then give you a few lines of output.

Also you can try
```
sudo ifdown eth1; sudo ifup eth1
```
after resume.

I believe your motherboard has only 1 Ethernet port, but your "ifconfig -a" output suggests you have 2 (eth0 and eth1) so, is the one you are using a PCI Ethernet card? Anyway, plug your cable in the other port on the back of your PC and see if it helps.

I don't know the final solution (if there is one), but we can probably find a workaround with a script or something so you don't have to reboot to get back online.

---

### Post by Lunx on 2009-02-03
> 
I believe your motherboard has only 1 Ethernet port, but your "ifconfig -a" output suggests you have 2 (eth0 and eth1) so, is the one you are using a PCI Ethernet card? Anyway, plug your cable in the other port on the back of your PC and see if it helps.

I don't know the final solution (if there is one), but we can probably find a workaround with a script or something so you don't have to reboot to get back online.


Sorry I haven't replied a bit sooner. Thanks for your help with this, I finally found the answer as to what problem is. Seems when I first got ADSL, I set up modem using USB cable instead of ethernet (I've never had any training in anything to do with 'puters, learn everything through trial and error, a lot of error). Connection worked fine under Windows, but no wonder poor ol' Tux got a bit confused by it all. I didn't twig to problem 'coz my user manual for modem says USB is for Widows OS, and ethernet for other platform independent OS's. The way I read the following had me thinking I must have had Ethernet, 'coz I took it as meaning USB is for Windows only, and this 'puter connected straight away when I first installed (I changed eth0 to eth1 in Firestarter and firewall was up and running too)

> Platform Support 

For Ethernet: 

- OS Independent 

For USB: 

- Windows 98SE/ME 

- Windows 2000/XP 

- Windows Vista

Feel such a goose for stuffing up like this, least problem is now identified and I'll pick up a cable in the morning and connect it properly (just got myself a new 'puter desk, so will be good timing to unplug everything and connect it all up on new desk at same time). 

Anyhow, thanks again for trying to help me out (no wonder you were confused by it all, my Ludditeness didn't help either :redface:

---

### Post by neur0 on 2009-02-03
Well, I'm just glad its not one of those rare weird hardware related bugs which, for me, are the hardest to solve in a desktop environment.

---

### Post by Lunx on 2009-02-03
> **neur0 said:**
> Well, I'm just glad its not one of those rare weird hardware related bugs which, for me, are the hardest to solve in a desktop environment.

Nup, it was like 99% of my 'puter troubles, user generated ;)

But I have discovered my first true bug and am about to check out Forum and  Launchpad to see if it's been mentioned. Yesterday I was messing about practicing managing files on command line and I created a few copies of docs, images etc and moved them around my system before sending them back to desktop. From there I did a bit of house keeping and used drag'n'drop to shift them to Trash before switching workspaces to do other stuff. On four or five seperate occasions I saw a faint, shadowy  image come out of trash and flash across screen in exact opposite direction and back to where I'd originally. First time I didn't know what it was, but next occasions I could make out the images of folder icons and package icons, although they were faint and fast moving. Each time it happened it was around a minute or two after I'd actually dragged the file to trash. (Obviously nothing actually comes out of Trash and goes back to whence it came, just the ghost images). Yesterday was first time I noticed this, no problems prior so I wonder if it had anything to do with last kernal update I installed yesterday morning? I realise this is wrong place for this, so will go start a post and mark this one solved.

Thanks again
Pete

This thread now **[COLOR="Blue"]SOLVED[/COLOR]**

---

### Post by Lunx on 2009-02-05
This thread even more solved!!! Scored Ethernet cable andd all problems sorted, hibernating now works fine too.

[COLOR="Blue"]**Solved even more**[/COLOR]

---

### Post by wkcchampion on 2011-01-08
Hello buddies,
I revive this thread because I'm encountering the same issue.

I have Ubuntu 10.10 Maverick Meerkat on a quite old desktop PC, up-to-date. The computer connect to the internet through a Netgear router, Ethernet port.

If I put the machine on stand-by or hibernation, the network won't reconnect at the wake up. Strange uh? i've read the previous posts. I'm no expert, but it doesn't seem I have that USB problem.

I have Ubuntu 10.10 Netbook edition on my Asus netbook and this doesn't happen there.

Any ideas?

Thank you
Marco

---

### Post by wkcchampion on 2011-01-16
> **wkcchampion said:**
> Hello buddies,
I revive this thread because I'm encountering the same issue.

I have Ubuntu 10.10 Maverick Meerkat on a quite old desktop PC, up-to-date. The computer connect to the internet through a Netgear router, Ethernet port.

If I put the machine on stand-by or hibernation, the network won't reconnect at the wake up. Strange uh? i've read the previous posts. I'm no expert, but it doesn't seem I have that USB problem.

I have Ubuntu 10.10 Netbook edition on my Asus netbook and this doesn't happen there.

Any ideas?

Thank you
Marco

bump

---

### Post by wkcchampion on 2011-01-23
bump. i still have the issue

---

