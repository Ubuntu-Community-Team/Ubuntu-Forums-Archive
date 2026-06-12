---
title: "PLEASE HELP - cannot only ONLY ONE WEBSITE, works in windows."
date: 2009-05-27
forum: General Help
---

### Post by Arrowx7 on 2009-05-27
Hi,
My university website does not open in ubuntu.
I tried 

```

ss@laptop:~$ host www.mcmaster.ca
www.mcmaster.ca is an alias for wwwmac.cis.mcmaster.ca.
wwwmac.cis.mcmaster.ca has address 130.113.64.65
ss@laptop:~$ nslookup www.mcmaster.ca
Server:		192.168.0.1
Address:	192.168.0.1#53

Non-authoritative answer:
www.mcmaster.ca	canonical name = wwwmac.cis.mcmaster.ca.
Name:	wwwmac.cis.mcmaster.ca
Address: 130.113.64.65


```

So it resolves fine.   DNS seems ok.  But then I ping it:
```

ss@laptop:~$ ping www.mcmaster.ca
PING wwwmac.cis.mcmaster.ca (130.113.64.65) 56(84) bytes of data.
From laptop.local (130.113.155.52) icmp_seq=1 Destination Host Unreachable
From laptop.local (130.113.155.52) icmp_seq=2 Destination Host Unreachable

```

Only that website does not work.  Nothing that has mcmaster.ca in it's name works in firefox (i.e. all subdomains fail to load).  I get this message in FF 3.0.10:
--------------
Failed to Connect

Firefox can't establish a connection to the server at mcmaster.ca.

Though the site seems valid, the browser was unable to establish a connection.

    * Could the site be temporarily unavailable? Try again later.
    * Are you unable to browse other sites?  Check the computer's network connection.
    * Is your computer or network protected by a firewall or proxy? Incorrect settings can interfere with Web browsing.
-----------------


There is nothing wrong with firefox (all websites work perfectly, plus I tried clearing cache etc..).  There is nothing wrong with that website, I have another linux box that access it fine, windows on this same laptop access it fine.  It seems like something wrong with ubuntu.
I tried deleting the connection and reconnecting to the wireless network and still same problem.

---

### Post by jrusso2 on 2009-05-27
Works fine here.
 [http://wwwmac.cis.mcmaster.ca](http://wwwmac.cis.mcmaster.ca).

---

### Post by Arrowx7 on 2009-05-27
I know, that's the point.  It works on the same laptop running windows.  It works on other machines on my network router.

Here is another piece of info:  I used this laptop, connected to a different network, and it still won't load mcmaster.ca.  So it's something with ubuntu and networking that it does not want to load this site.

---

### Post by spcwingo on 2009-05-27
I would recommend backing up your bookmarks, etc then renaming your ~/.mozilla folder to ~/.mozilla.bak.  This will recreate a user profile.  After that try reopening Firefox and trying the link.  I'm almost certain it's something to do with your profile because it's working for me.  If for some reason that doesn't work just delete the ~/.mozilla folder and rename ~/.mozilla.bak back to ~/.mozilla.

---

### Post by utnubuuser on 2009-05-27
Checked your privacy settings?  Firefox>>Edit>>Preferences?
Is there a redirect limit/rule set in firefox or your firewall?

---

### Post by Arrowx7 on 2009-05-27
How can it be firefox if I can't ping it?  (see my first post)

And FYI this computer is used by a regular user that just uses the internet at work and home so it's not like I was trying to do something funny with kernels/drivers etc....

---

### Post by deadlockedgamer on 2009-05-27
I have ubuntu 9.04 and it works fine on my end sorry if this isn't helping. I am kind of lost seeing as i can't solve I problem that I can't reproduce:(

---

### Post by Cyberpenguin on 2009-05-28
Sorry you are having troubles.  Is there a firewall between your PC and the university network?  Could you post the output to these commands, please?:

/sbin/route -n
/sbin/ifconfig
cat /etc/resolv.conf
cat /etc/hosts

I'm just making sure your routing table and name resolver are OK.

Thanks.

---

### Post by Arrowx7 on 2009-05-28
Hi Cyberpenguin,
Sorry I don't have the laptop with me, i'll post the output for those commands tomorrow.

Thanks a lot!

---

### Post by Arrowx7 on 2009-05-28
Hello,

thanks for your help.

Here is the output from those commands...


ss@ss-laptop:~$ sudo /etc/sbin/route -n
[sudo] password for ss:
sudo: /etc/sbin/route: command not found
ss@ss-laptop:~$ sudo /sbin/route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0
130.113.0.0     0.0.0.0         255.255.0.0     U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 wlan0
0.0.0.0         130.113.155.5   0.0.0.0         UG    100    0        0 eth0
ss@ss-laptop:~$ sudo /sbin/ifconfig
eth0      Link encap:Ethernet  HWaddr 00:15:c5:68:b2:5a 
          inet addr:130.113.155.58  Bcast:130.113.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1432  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17

lo        Link encap:Local Loopback 
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:592 (592.0 B)  TX bytes:592 (592.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:16:cf:49:ba:6c 
          inet addr:192.168.0.101  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::216:cfff:fe49:ba6c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13163 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4178 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:5537916 (5.5 MB)  TX bytes:874899 (874.8 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-16-CF-49-BA-6C-61-36-00-00-00-00-00-00-00-00 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

ss@ss-laptop:~$ sudo /cat /etc/resolv.conf
sudo: /cat: command not found
ss@ss-laptop:~$ sudo /cat/etc/resolv.conf
sudo: /cat/etc/resolv.conf: command not found
ss@ss-laptop:~$ sudo cat /etc/resolv.conf
# Generated by NetworkManager
domain cgocable.net
search cgocable.net
nameserver 192.168.0.1
ss@ss-laptop:~$ sudo cat /etc/hosts
127.0.0.1 localhost
127.0.1.1 ss-laptop

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
ss@ss-laptop:~$

---

### Post by lisati on 2009-05-28
Just an observation: [http://www.mac.cis.mcmaster.ca/](http://www.mac.cis.mcmaster.ca/) results in a page load error on my machine, but [http://wwwmac.cis.mcmaster.ca/](http://wwwmac.cis.mcmaster.ca/) (without the "." after the www) loads fine.

---

### Post by Cyberpenguin on 2009-05-28
I noticed you are connected to a wireless connection and wired at the same time.  You are using the DNS from the wireless.  It looks like the wired is on the right network.  You might disable your wireless and try again.  It's usually best to use either the wireless or the wired, not both (there may be times it is useful, but rarely).  In this, I suspect the wireless one is causing problems.  I hope that helps.

---

### Post by Cyberpenguin on 2009-05-28
Oh, and you might need to refresh the dhcp to get the right DNS back.

---

### Post by Arrowx7 on 2009-05-28
well i'm using the wireless one only.  How do I disable the wired connection?  I went into the manager and removed all wired entries (only one was auto eth0) and it still wouldn't load.

Thanks.

---

### Post by Cyberpenguin on 2009-05-28
You can run:

/sbin/ifconfig eth0 down

to temporarily take it down until next reboot.  Unplugging the wired connection would actually be the best thing after that, if it isn't needed.

---

### Post by utnubuuser on 2009-05-29
[http://wwwmac.cis.mcmaster.ca/](http://wwwmac.cis.mcmaster.ca/) works, but not [http://www.mac.cis.mcmaster.ca/](http://www.mac.cis.mcmaster.ca/).  This is most likely an error in the server's-redirect, and has nothing at all to do with your machine. There is no such internet address as wwwmac..., but it works, and as far as I know, the only way that's possible is if that address has a re-direct enabled. As I said though, this is only 'as far as I know'.
Get in touch with the webmaster for the site and see if it's a spelling error.

---

### Post by lisati on 2009-05-29
> **utnubuuser said:**
> [http://wwwmac.cis.mcmaster.ca/](http://wwwmac.cis.mcmaster.ca/) works, but not [http://www.mac.cis.mcmaster.ca/](http://www.mac.cis.mcmaster.ca/).  This is most likely an error in the server's-redirect, and has nothing at all to do with your machine. There is no such internet address as wwwmac..., but it works, and as far as I know, the only way that's possible is if that address has a re-direct enabled. As I said though, this is only 'as far as I know'.
Get in touch with the webmaster for the site and see if it's a spelling error.

Thank you for confirming something I'd already spotted.

---

### Post by Cyberpenguin on 2009-05-29
> **utnubuuser said:**
> [http://wwwmac.cis.mcmaster.ca/](http://wwwmac.cis.mcmaster.ca/) works, but not [http://www.mac.cis.mcmaster.ca/](http://www.mac.cis.mcmaster.ca/).  This is most likely an error in the server's-redirect, and has nothing at all to do with your machine. There is no such internet address as wwwmac..., but it works, and as far as I know, the only way that's possible is if that address has a re-direct enabled. As I said though, this is only 'as far as I know'.
Get in touch with the webmaster for the site and see if it's a spelling error.

I'm a little confused.  Originally he stated "Nothing that has mcmaster.ca in it's name works in firefox (i.e. all subdomains fail to load)."  If that statement is true, then it isn't just server redirector error.  I was going off this assumption.

If it is just the one address that doesn't work than I concur.

---

### Post by utnubuuser on 2009-06-02
maybe he meant variations of [http://mcmaster](http://mcmaster)....  or [www.mcmasters.... or http://www.mcmasters....?](www.mcmasters.... or http://www.mcmasters....?)

---

