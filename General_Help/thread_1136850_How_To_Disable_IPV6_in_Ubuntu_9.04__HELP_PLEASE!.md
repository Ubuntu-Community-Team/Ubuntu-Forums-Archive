---
title: "How To Disable IPV6 in Ubuntu 9.04 ? HELP PLEASE!"
date: 2009-04-25
forum: General Help
---

### Post by TheExplorer on 2009-04-25
Please, help needed!

Network became slow due to the unsupported ipv6 protocol.

In the past I used to fix it in **/etc/modprobe.d/aliases**, but now it is built in the kernel. I don't like the idea to recompile it.

Anyway I've somehow found two ways:

1) Add to the **/etc/modprobe.d/blacklist.conf** the following:

blacklist net-pf-10
blacklist ipv6

2) Put "1" into **/proc/sys/net/ipv6/conf/all/disable_ipv6**

So I tried them both and nothing works actually [IMG]http://forum.ubuntu.ru/Smileys/webby/smiley.gif[/IMG]

To check if it is disabled you can in the console:

ip a | grep inet6

If it is disabled there will be no output.

I've also came across some bug reports concerning this issue (inability to switch off ipv6).
I urgently need help since it is unsupported in my country and networking is slower than it was under 8.10 (or in Windoze).

Thank you in advance!

Alexander.

---

### Post by kpkeerthi on 2009-04-25
[https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4]("https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4")

---

### Post by TheExplorer on 2009-04-25
Nope. Doesn't work. Seems that there is no way out really. Recompile will help... But I do not want to recompile actually :(

---

### Post by kpkeerthi on 2009-04-25
No. My internet is just fine. :)

---

### Post by pops-saito on 2009-04-26
Now why would we be unable to disable IPv6.  Linux and Ubuntu are bastions of freedom.  The end user is allowed, actually encouraged, to experiment and customize.

So, what are our choices for disabling IPv6 in Ubuntu 9.04?  We only have one choice - recompile the kernel.

    [http://ubuntuforums.org/showthread.php?t=1114211](http://ubuntuforums.org/showthread.php?t=1114211)  

However, the majority of us do not want to recompile the kernel.  We just want our freedom back, to disable IPv6 via a simple config file.

Was this just an oversight.  There has been a bug (with a known fix) open for this in the linux kernel for over a month ([http://kerneltrap.org/mailarchive/linux-netdev/2009/3/5/5101864/thread](http://kerneltrap.org/mailarchive/linux-netdev/2009/3/5/5101864/thread)).  Perhaps it was just an oversight that this "bug" did not get fixed before 9.04 was released?  Or perhaps there wasn't enough time to get a new kernel into the 9.04 release?  

Hopefully someone didn't decided it was "for our own good" to remove some of our freedom and not provide a way to disable IPv6!?!?  That we should be forced to face IPv6 and be left with no other choice but to "fix" any issues we may encounter.  To manipulate us into directing our rage against the applications that don't work with IPv6.  For the good of the "all".

If our loss of freedom was intentional, it is probably time to look at other operating systems (NetBSD, FreeBSD, OpenBSD)?  If it was an oversight, I hope that someone (on high) speaks up and provides a simple fix for this folly.

If you want to understand IPv6, where it is today and likely to be tomorrow, then visit - [http://www.civil-tongue.net/6and4/](http://www.civil-tongue.net/6and4/)

Beware of the IPv6 fan-boys!

---

### Post by HammerheadNC on 2009-05-22
I found this command in another forum and it worked for me:

echo 1 | sudo tee /proc/sys/net/ipv6/conf/all/disable_ipv6

the output is the number 1 

I rebooted and the internet is fast again!

Hope this helps someone!

Hammerhead

---

### Post by HammerheadNC on 2009-05-22
> **HammerheadNC said:**
> I found this command in another forum and it worked for me:

echo 1 | sudo tee /proc/sys/net/ipv6/conf/all/disable_ipv6

the output is the number 1 

I rebooted and the internet is fast again!

Hope this helps someone!

Hammerhead

This actually did not work - it just appeared to the first time I checked the speed - sorry!

---

### Post by Brandon Williams on 2009-05-22
> **HammerheadNC said:**
> I found this command in another forum and it worked for me:

echo 1 | sudo tee /proc/sys/net/ipv6/conf/all/disable_ipv6

the output is the number 1 
I rebooted and the internet is fast again!
Hope this helps someone!

Hammerhead


I don't mean to be contrary, but if that appeared to help, then your problem was not related to ipv6. All you did was set the disable_ipv6 flag in the current session. After the reboot, your change was no longer in effect. In fact, I'm not convinced that changing that setting does anything meaningful in the current Jaunty kernel, since many people have reported that it does not prevent their machines from attempting to perform IPv6 lookups, which is the real problem.

---

### Post by cyberscribe on 2009-05-22
I ran the command "*echo 1 | sudo tee /proc/sys/net/ipv6/conf/all/disable_ipv6*" and then re-ran the command "*ip a | grep inet6*" and the output is exactly the same, both before and after (and the output is not "1").

I've got to second what "pops-saito" said...this should be easier to disable.

---

### Post by Yellow Pasque on 2009-05-22
There's a bug report in launchpad on this. Basically, IPv6 is compiled into the Jaunty kernel, whereas in the past, it was configured as a seperate module (which could easily be blacklisted).

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/351656](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/351656)

---

### Post by Brandon Williams on 2009-05-23
I am curious about what types of problems people actually experience due to IPv6 being enabled, and what they are doing to verify that the problems are really IPv6 related. There are quite a number of forum posting, blog posting, etc. that tell people to blame slow internet performance on IPv6, but I haven't seen much that tells people how to verify that the problem really is related to IPv6. I have tried quite a number of things to get my Jaunty systems to attempt to transmit either IPv6 nameserver requests (the usual culprit) or IPv6 packets, but to no avail, which leads me to believe that IPv6 might not actually be the problem for most users.

I do know, based on previous feedback, that some specific applications, like Opera, have "less than optimal" internal implementations of IPv6 support that circumvent the changes that were made to the standard library name lookup routines. For users looking to run these specific applications, disabling IPv6 at the system level used to be the only way to get decent address lookup performance, and the change in Jaunty has made those apps virtually unusable. So, I recognize that there are perfectly valid application-specific reasons why a user might want to disable IPv6 at the system level.

Is everyone who wants to disable IPv6 experiencing such application-specific problems? Or do the problems appear to be system-wide? If they are application-specific, are the problematic apps ones that are part of the standard Ubuntu install? And if the problems are system-wide, what did you do to verify that the performance problem really is an IPv6 issue? I'm just trying to get a better understanding of the problem.

---

### Post by unutbu on 2009-05-23
Hi Brandon Williams, 
Maybe this will help:

[http://ubuntuforums.org/showpost.php?p=478267&postcount=8](http://ubuntuforums.org/showpost.php?p=478267&postcount=8)

---

### Post by fillintheblanks on 2009-05-23
to speed up my internet I added OpenDNS to my internet settings under 'IPv4 Settings' tab

> DNS Servers: 208.67.222.222, 208.67.220.220

I use Opera and its considerably faster no need to disable IPv6

---

### Post by Brandon Williams on 2009-05-23
> **unutbu said:**
> Hi Brandon Williams, 
Maybe this will help:

[http://ubuntuforums.org/showpost.php?p=478267&postcount=8](http://ubuntuforums.org/showpost.php?p=478267&postcount=8)

Thanks for the link. It doesn't really answer my question, though.

I agree entirely with the post that you linked to when it says that there should be no problems associated with IPv6 if you have not misconfigured your network, but there are plenty of people who appear to think that the only solution to their network woes is to disable IPv6, which they can't do. I'm interested to know what's making people think that it's ultra-important to be able to disable IPv6. 

As the link you referenced indicates, just because you got better performance by disabling IPv6, that doesn't mean the core problem was actually IPv6. Disabling IPv6 might just be a work-around for some other issue, and it would be nice to figure out what that other issue is.

---

### Post by cybrsaylr on 2009-05-23
> **fillintheblanks said:**
> to speed up my internet I added OpenDNS to my internet settings under 'IPv4 Settings' tab



I use Opera and its considerably faster no need to disable IPv6

I tried doing that with no effect. Opera is still slow.



The reason I figured it was an IPv6 issue is going back to Hardy every version upgrade ran Opera slow until I disabled IPv6. Once that was disabled Opera took off flying again faster than Firefox on both my desktop and laptop. 

Of course Jaunty changed things making it impossible to change IPv6 as it was easily done in earlier versions. 

One thing I discovered is it may be related to wireless, at least for me.
On wireless my laptop runs Opera 9.64 buggy on 64bit Jaunty.
When I hardwire the laptop Opera flys again faster than Firefox, as it did on earlier Ubuntu versions. Then when going back to wireless Opera runs buggy again.

I even replaced default 'network manager' with 'WICD manager' but Opera still runs buggy on wireless. There was no change in performance.

My desktop runs 32bit Jaunty wired and Opera runs fine at full speed as it did running 32bit Intrepid before.

---

### Post by pcjunkie on 2009-05-27
Dear conical please don't do this.

My internet is an 8mb connection and I am downloading at 53kb/s.

---

### Post by wermeulen on 2009-06-10
Deleted post; thought wlan0 device looking for IPv6 router was taking 30% of my bootup time based on kern.log. Just found syslog and the real culprit of slowdown is Network Manager looking for DHCP. Oops ;)

---

### Post by Brandon Williams on 2009-06-10
What leads you to the belief that the 10 second delay there is actually slowing down your boot time?

I run the lpia kernel on my Dell mini, which allows me to disable IPv6 because it's built as a module. I see the same 'no IPv6 routers present' message in kern.log, with the same apparent 10-second delay. If I disable the IPv6 module, the log line no longer shows up, but there is no perceivable difference in either boot time or the time required for my wireless card to acquire an address. 

Is there something specific that you are looking at to determine that this 10-second gap in kern.log directly corresponds to delay in boot time? What is giving you that indication that nothing else is happening during that period?

---

### Post by tquinn on 2009-06-19
> **Brandon Williams said:**
> I am curious about what types of problems people actually experience due to IPv6 being enabled, and what they are doing to verify that the problems are really IPv6 related. There are quite a number of forum posting, blog posting, etc. that tell people to blame slow internet performance on IPv6, but I haven't seen much that tells people how to verify that the problem really is related to IPv6. I have tried quite a number of things to get my Jaunty systems to attempt to transmit either IPv6 nameserver requests (the usual culprit) or IPv6 packets, but to no avail, which leads me to believe that IPv6 might not actually be the problem for most users.

I do know, based on previous feedback, that some specific applications, like Opera, have "less than optimal" internal implementations of IPv6 support that circumvent the changes that were made to the standard library name lookup routines. For users looking to run these specific applications, disabling IPv6 at the system level used to be the only way to get decent address lookup performance, and the change in Jaunty has made those apps virtually unusable. So, I recognize that there are perfectly valid application-specific reasons why a user might want to disable IPv6 at the system level.

Is everyone who wants to disable IPv6 experiencing such application-specific problems? Or do the problems appear to be system-wide? If they are application-specific, are the problematic apps ones that are part of the standard Ubuntu install? And if the problems are system-wide, what did you do to verify that the performance problem really is an IPv6 issue? I'm just trying to get a better understanding of the problem.

I am developing an application in java using legacy messaging (Mantaray JMS). It balks with ipv6. I am looking for a good alternative peer to peer alternative, but have not found anything compelling, considering it seems like Mantaray may reappear, and maybe address this problem.

I love Ubuntu and will continue to use it. But, likewise to your motivations, I would like to understand why is disabling ipv6 a problem for Ubuntu? It seems like a lot of installations are on older equipment and would be prone to ipv6 problems. I am curious to the benefits that were gained.

---

### Post by ws.venkateswaran on 2009-06-24
how to disable ipv6 in firefox.. does it solve the problem

---

### Post by RobOrr on 2009-06-24
disabling in firefox is straightforward enough - this thread appears to be mostly about disabling ipv6 at the system level though. To do it  in Firefox,

1. Go to the web address "about:config"
This is where you can really configure the innards of firefox. Be wary of some of these settings though, you can mess firefox up by changing certain of these options.

2.find the Preference Name network.dns.disableIPv6
You can do this either by scrolling through the list or typing IPv6 into the filter.

3. Change the boolean value to true.
You do this by double-clicking the line. If it's already true, then firefox already has IPv6 disabled.

---

### Post by Jupp3 on 2009-06-24
> **RobOrr said:**
> disabling in firefox is straightforward enough - this thread appears to be mostly about disabling ipv6 at the system level though. To do it  in Firefox,

1. Go to the web address "about:config"
This is where you can really configure the innards of firefox. Be wary of some of these settings though, you can mess firefox up by changing certain of these options.

2.find the Preference Name network.dns.disableIPv6
You can do this either by scrolling through the list or typing IPv6 into the filter.

3. Change the boolean value to false.
You do this by double-clicking the line. If it's already false, then firefox already has IPv6 disabled.

Doesn't setting network.dns.**disable**IPv6 to **false** actually enable it instead?

---

### Post by 3rdalbum on 2009-06-24
> **pcjunkie said:**
> Dear conical please don't do this.

My internet is an 8mb connection and I am downloading at 53kb/s.

I don't think this has any relevance to IPv6. If the site you are downloading from does not support IPv6 at all, it will take some time (a few seconds) for timeout to occur, and then IPv4 communication will be used.

So, it could have been a few seconds for your download to begin, but once it has begun it would be working at IPv4 only and thus unhindered by speed issues.

So far everyone's skirting around the biggest issue, which is perhaps why IPv6 is mandatory rather than optional: It's estimated that some time next year we will run out of IPv4 addresses. I take all figures with a grain of salt, but I figure we've only got maybe two years until EVERYTHING has to be compatible. And everything has got to start with something.

I haven't disabled IPv6 on my netbook and home server and I don't see any degraded performance; are there real performance issues?

---

### Post by vaikz on 2009-06-26
Hi guys,

I installed Jaunty and I´ve been searching the internet how to speed up my internet connection w/o success, it only gives me half of the speed I subscribed. I already done disabling the IPV6 in modprobe.d I think. But no success.

Until recently, I reinstalled Jaunty on my extra HD and I came accross on how to disable IPV6. Sorry I forgot the link but It really works. Here&#347; what I did:
1. I upgrade to new kernel 2.6.3
2. I just add ¨ipv6.disable=1¨ on the grub menu list like this:
    kernel        /boot/vmlinuz-2.6.30-020630-generic root=UUID=e706a870-ff71-4bee-9016-cb4c6712ee3e ro quiet splash [COLOR=Red]ipv6.disable=1[/COLOR][COLOR=Black]
3. Reboot and that&#347; it.

Hope this will help others as it helps mine. Cheers.
[/COLOR]

---

### Post by Brandon Williams on 2009-06-26
Disabling ipv6 will not increase your throughput. The most that it can do is improve the time it takes to lookup an IP address and/or establish a connection. If you really are talking about throughput, then I doubt the solution was disabling ipv6. There's probably something else in the new kernel that led to the improvement.

---

### Post by vaikz on 2009-06-26
Correct me if I&#7743; wrong but by adding the ¨ipv6.disable=1¨ on the kernel boot option on the menu.lst on grub on my jaunty w/c has the 2.6.30 kernel and it improves a lot on my download speed. After I verify this, I used this setup on my intrepid w/c it had the 2.6.27-11 and using a wireless. Before I did the change, I&#7743; downloading only at 20kbps the most. Even on apt-get and wget. But after the changed, I&#7743; already downloading at an average of 45kbps.

just try the setup. If it doesnt work for you then you can always delete it. Cheers.

---

### Post by Yellow Pasque on 2009-06-26
vaikz, thank you for the workaround. I'm sure a lot of people will find it useful.

---

### Post by vaikz on 2009-06-26
glad to help.

---

### Post by hiltonr on 2009-06-27
> **vaikz said:**
> 

Here&#347; what I did:
1. I upgrade to new kernel 2.6.3
[/COLOR]

This is good except that my system now no longer recognizes my 4Gb of RAM. Previous kernel of 2.6.13-server sees the additional 1Gb.

Any ideas on this please?

Hilton

---

### Post by RobOrr on 2009-06-27
> **Jupp3 said:**
> Doesn't setting network.dns.**disable**IPv6 to **false** actually enable it instead?

haha yeah it does, clearly wasn't paying enough attention when I wrote that post...

---

### Post by d-man97 on 2009-07-01
> **vaikz said:**
> Hi guys,

I installed Jaunty and I´ve been searching the internet how to speed up my internet connection w/o success, it only gives me half of the speed I subscribed. I already done disabling the IPV6 in modprobe.d I think. But no success.

Until recently, I reinstalled Jaunty on my extra HD and I came accross on how to disable IPV6. Sorry I forgot the link but It really works. Here&#347; what I did:
1. I upgrade to new kernel 2.6.3
2. I just add ¨ipv6.disable=1¨ on the grub menu list like this:
    kernel        /boot/vmlinuz-2.6.30-020630-generic root=UUID=e706a870-ff71-4bee-9016-cb4c6712ee3e ro quiet splash [COLOR=Red]ipv6.disable=1[/COLOR][COLOR=Black]
3. Reboot and that&#347; it.

Hope this will help others as it helps mine. Cheers.
[/COLOR]

Clarification: You must have kernel 2.6.29.3 or higher for the ipv6.disable=1 option to work. If **cat /var/log/kern.log | grep "ipv6.disable=1"** returns **Unknown boot option `ipv6.disable=1': ignoring** then you need to update your kernel.

A better way would be to add it to the "# defoptions=" line in menu.lst and then run **sudu update-grub**. This way it gets added to all active kernels and will be preserved if a new kernel is installed (among other things).

---

### Post by MrObvious on 2009-07-02
So you have to have the updated kernel for this to work?

---

### Post by Arup on 2009-07-02
> **MrObvious said:**
> So you have to have the updated kernel for this to work?

Yep, sadly no other choice so far.

---

### Post by sockmoney on 2009-07-05
So how does one update their kernel to this new version?

Do you have to download it first?

I'm a bit of a Ubuntu noob... so any step-by-step advice would be appreciated!

As an aside, I actually followed someone else's tutorial on re-compiling the kernel to pull out the ipv6 module so it could be "blacklisted".  It seemed to work, since now when I run the command "ip a | grep inet6", I get nothing...

However my internet is still very slow... perhaps this newer kernel has some other bug fixes?  Looking forward to trying it if I can figure out how to upgrade my kernel!  ;-)

---

### Post by sockmoney on 2009-07-05
I ended up installing a program called "KernelCheck".  It seemed to do the trick for me for updating my kernel to the latest with minimal work on my part.  

I'm now on 2.6.30.1-candela and it still does not let me specify the disableIPv6=1 in the startup line of the menu.lst.

Though oddly, ipV6 seems to now be turned off by default???  When I run the "ip a | grep inet6" command I get nothing returned.

Anyone know if this latest kernel disables it by default now?

---

### Post by davidjmorin on 2009-07-08
where do i place the following patch? 

```
diff --git a/Documentation/networking/ip-sysctl.txt b/Documentation/networking/ip-sysctl.txt
index 7185e4c..ec5de02 100644
--- a/Documentation/networking/ip-sysctl.txt
+++ b/Documentation/networking/ip-sysctl.txt
@@ -1043,7 +1043,9 @@  max_addresses - INTEGER
     Default: 16
 
 disable_ipv6 - BOOLEAN
-    Disable IPv6 operation.
+    Disable IPv6 operation.  If accept_dad is set to 2, this value
+    will be dynamically set to TRUE if DAD fails for the link-local
+    address.
     Default: FALSE (enable IPv6 operation)
 
 accept_dad - INTEGER
diff --git a/net/ipv6/addrconf.c b/net/ipv6/addrconf.c
index e83852a..717584b 100644
--- a/net/ipv6/addrconf.c
+++ b/net/ipv6/addrconf.c
@@ -590,6 +590,7 @@  ipv6_add_addr(struct inet6_dev *idev, const struct in6_addr *addr, int pfxlen,
 {
     struct inet6_ifaddr *ifa = NULL;
     struct rt6_info *rt;
+    struct net *net = dev_net(idev->dev);
     int hash;
     int err = 0;
     int addr_type = ipv6_addr_type(addr);
@@ -606,6 +607,11 @@  ipv6_add_addr(struct inet6_dev *idev, const struct in6_addr *addr, int pfxlen,
         goto out2;
     }
 
+    if (idev->cnf.disable_ipv6 || net->ipv6.devconf_all->disable_ipv6) {
+        err = -EACCES;
+        goto out2;
+    }
+
     write_lock(&addrconf_hash_lock);
 
     /* Ignore adding duplicate addresses on an interface */
@@ -1433,6 +1439,11 @@  static void addrconf_dad_stop(struct inet6_ifaddr *ifp)
 void addrconf_dad_failure(struct inet6_ifaddr *ifp)
 {
     struct inet6_dev *idev = ifp->idev;
+
+    if (net_ratelimit())
+        printk(KERN_INFO "%s: IPv6 duplicate address detected!\n",
+            ifp->idev->dev->name);
+
     if (idev->cnf.accept_dad > 1 && !idev->cnf.disable_ipv6) {
         struct in6_addr addr;
 
@@ -1443,11 +1454,12 @@  void addrconf_dad_failure(struct inet6_ifaddr *ifp)
             ipv6_addr_equal(&ifp->addr, &addr)) {
             /* DAD failed for link-local based on MAC address */
             idev->cnf.disable_ipv6 = 1;
+
+            printk(KERN_INFO "%s: IPv6 being disabled!\n",
+                ifp->idev->dev->name);
         }
     }
 
-    if (net_ratelimit())
-        printk(KERN_INFO "%s: duplicate address detected!\n", ifp->idev->dev->name);
     addrconf_dad_stop(ifp);
 }
 
@@ -2823,11 +2835,6 @@  static void addrconf_dad_timer(unsigned long data)
         read_unlock_bh(&idev->lock);
         goto out;
     }
-    if (idev->cnf.accept_dad > 1 && idev->cnf.disable_ipv6) {
-        read_unlock_bh(&idev->lock);
-        addrconf_dad_failure(ifp);
-        return;
-    }
     spin_lock_bh(&ifp->lock);
     if (ifp->probes == 0) {
         /*

```

---

### Post by Yellow Pasque on 2009-07-09
^ In the top directory of the kernel source tree (wherever you have your kernel source).

---

### Post by gelsbern on 2009-08-27
I finally figured out how to turn it off for the interface.  I changed my /etc/rc.local as follows

```

#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

IFACE='eth0'
IPV6=`ifconfig $IFACE | gawk '/inet6/ {print $3}'`
ifconfig $IFACE inet6 del $IPV6

exit 0

```

---

### Post by cryptodan on 2009-12-02
WHy cant Linux Distro writers simply disable IPv6 and introduce a IPv6 enabled Kernel on their install medium?  I am sick and freaking tired of Linux Distro Writers shoving unnecessary bullcrap down our throats.  IPv6 is not suitable for any small home office network.  It is only suitable in major Wide Area Networks where IP distribution is costly.  

I HATE IPv6 WITH A PASSION.  It is more annoying then having your computer reboot after windows updates are completed.  I shouldn't have to recompile kernels to disable a feature that shouldn't be enabled by default.  Not everyone has IPv6 enabled routers.  Hell where I work we still use IPv4 on every network segment.

It is useless.

---

### Post by deece on 2009-12-28
thanks gelsbern :) worked for me. Still had to create a static IP but at least i can get into my router now, thanks again :)

cryptodan...i agree 100%

---

