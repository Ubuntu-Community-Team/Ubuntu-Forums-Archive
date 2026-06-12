---
title: "Something odd....certain websites very slow"
date: 2009-05-31
forum: General Help
---

### Post by heitjer on 2009-05-31
I have experienced a problem with certain websites - especially forum sites like this one (i.e. [http://www.rv.net/forum/](http://www.rv.net/forum/)).

In ubuntu firefox 3.0.10 these websites are very slow while others are ligtning fast. On my wifes MAC this website is fast. Therefore I think it is not a DSL or router problem. 

To further investigate I tried the same website in ubuntu's VirtualBox running Windows XP and the same (actually slower) speed occurs. 

I read up on this and at first I thought this had something to do with the plugins and add ons in firefox (running just standard stuff plus shockwave). But if it would be firefox related it should not affect the VirtualBox - correct? 

So I am puzzled. Please provide me some pointers on where to look.....!

---

### Post by DeMus on 2009-05-31
> **heitjer said:**
> I have experienced a problem with certain websites - especially forum sites like this one (i.e. [http://www.rv.net/forum/](http://www.rv.net/forum/)).

In ubuntu firefox 3.0.10 these websites are very slow while others are ligtning fast. On my wifes MAC this website is fast. Therefore I think it is not a DSL or router problem. 

To further investigate I tried the same website in ubuntu's VirtualBox running Windows XP and the same (actually slower) speed occurs. 

I read up on this and at first I thought this had something to do with the plugins and add ons in firefox (running just standard stuff plus shockwave). But if it would be firefox related it should not affect the VirtualBox - correct? 

So I am puzzled. Please provide me some pointers on where to look.....!

Here with me the site is also extremely slow. I use Firefox 3.0.10 on Jaunty 9.04 with only one added plug-in. Other sites are normal, but this one is very slow.

---

### Post by steeleyuk on 2009-05-31
Its not a Firefox issue, i've just tried using Epiphany+Webkit and its the same.

---

### Post by whoop on 2009-05-31
I would say the server/bandwidth there sucks. It's even slow with a cli browser (295 bytes a second average , wow). Maybe it's fast on your mac because of some client side caching. It doesn't even respond to ping (could be blocked though).
It's seems to be running Microsoft IIS webserver 7.0.

---

### Post by heitjer on 2009-05-31
It does not respond to pings from my machine but from an internet website I got 81 ms. 

I am still puzzled that it works with the iMAC and I just tested it with my daughters Windows XP. I must say it is really fast from both. Pages are build within a blink of the eye.

---

### Post by heitjer on 2009-05-31
are you guys all running linux? is this a problem there?

---

### Post by whoop on 2009-05-31
> **heitjer said:**
> are you guys all running linux? is this a problem there?

Well, I run linux and it's slow... I asked a friend (who uses windows) to check it out and he claims fast.

It's really strange... <paranoia>Maybe the site is discriminating user-agents?</paranoia>

---

### Post by ajgreeny on 2009-05-31
Very slow here as well, even attempting to kid it into believing I'm using windows with the User Agent Switcher.

---

### Post by cariboo on 2009-05-31
I tried the site using Firefox on Karmic, and it was slow loading. Running XP in a vm, it loads faster using both firefox and IE 7, but it still takes a long time to load the full page until the popup loads. 

I would suggest some strange scripting is causing the problem.

---

### Post by lavinog on 2009-05-31
wow. very suspicious.
I noticed in the source there is a comment with my ip address listed:
```
<!-- 6FC-ENILNO 16 -->



		
		<!-- 
		
		---------------------------
		
		IP: XXX.XXX.XXX.XXX
		
		Server: ONLINE-CF6
		
		Execution Time: 16ms
		
		---------------------------
		
		-->
		
	
```

---

### Post by lavinog on 2009-05-31
sure enough, it works just fine in xp. It cant be a cache issue either.
Has anyone tried other flavors of linux?
Anyone know how to change the user agent in xp to be like ubuntu?

---

### Post by whoop on 2009-05-31
> **lavinog said:**
> sure enough, it works just fine in xp. It cant be a cache issue either.
Has anyone tried other flavors of linux?
Anyone know how to change the user agent in xp to be like ubuntu?

It's slow in Arch over here...

---

### Post by rudy.b on 2009-05-31
I tried [http://www.rv.net/forum/](http://www.rv.net/forum/) in both Opera 10 and Firefox 3.0.10 and each were fast to load the page (1-2 seconds).  I clicked some of the threads and they were somewhat slower, but they were also image-heavy.

EDIT: By the way, I'm running Jaunty.

---

### Post by lavinog on 2009-05-31
Rudy, do you have ipv6 enabled?

---

### Post by heitjer on 2009-05-31
According to [this website]("https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4") it is enabled on my machine:

```
ip a | grep inet6
```

I get:
```
    inet6 ::1/128 scope host 
    inet6 xxxx::xxx:xxxx:xxxx:xxxx/64 scope link 

```

But still I only get the 'mosaic' version here: [KAME Project]("http://www.kame.net/")

---

### Post by heitjer on 2009-05-31
I also tried this [(LINK)]("http://www.andreas-kraus.net/blog/fix-the-slow-firefox-when-using-localhost-with-visual-studio/") - it did not help:

> It turns out that the slowness is caused by an IPv6 issue with DNS and can easily be resolved by turning IPv6 support off in Firefox while doing localhost testing. To make the change, type about:config in the address bar, locate the network.dns.disableIPv6 setting and double-click on it to set it to true. This does the trick for the Firefox localhost issue on Vista and everything is running fast again.

---

### Post by rudy.b on 2009-06-03
> **lavinog said:**
> Rudy, do you have ipv6 enabled?

Ya, I got IPv6 enabled.  Although I should point out that I don't see any popup as mentioned by cariboo907:

> **cariboo907 said:**
> ... but it still takes a long time to load the full page until the popup loads. 


---

### Post by heitjer on 2009-06-04
All,
I am struggling further on this topic with my machine but enjoy high-speed to [www.rv.net](www.rv.net) on my wifes iMAC. 
My wife is now started making jokes about my "ubuntu machine" and "I told you to buy a MAC"....durr

In the meantime I also tested other browsers, Epiphany and the likes. 

I think this has to do with the way ubuntu handles these websites on the way into the machine. I thought the ipv6 was a great idea but apparently a dead end. 

So - can someone point me to other possible solutions?

---

### Post by heitjer on 2009-06-05
Its fast today - I have not changed a thing since yesterday! Can you guys check as well?

---

### Post by hyperdude111 on 2009-06-05
I tested it on Google Chrome Alpha - Loads Fast
Firefox 3 - Loads slow
Firefox 3.5b Loads fast

I think its an issue with that version of firefox.

---

### Post by TheForumTroll on 2009-06-05
Fast on Minefield (FF 3.6a1pre) too.

---

### Post by lavinog on 2009-06-07
runs fast for me now while it didn't in the past. Looks like they fixed a server side script, because nothing was changed on this machine since then.

---

### Post by heitjer on 2009-06-09
As I was enjoying fast speed for two days I am back to sluggish performance on my ubuntu machine. I have not changed a thing....

This must be their server side stuff but why is this only affecting my ubuntu machine either running linux or windows? It is/has been always fast on the other machines in my household.

---

### Post by lavinog on 2009-06-10
Taken from rv.net:
> TOP STORY:
RV.Net Launches new site design with interactive content.
Looks like they are still working out issues.
Why not send them a comment reguarding the issue.

---

### Post by heitjer on 2009-06-16
I did send them a not and referenced this thread. No reply yet. 

Still extremely slow on my side (only on ubuntu) - can you guys check again?

---

### Post by lavinog on 2009-06-17
It seems even slower now.

---

### Post by heitjer on 2009-06-17
I agree. 

Here are the stats as of this evening, all within a few minutes from the same network router:

Main Machine - see signature
[LIST]
[*]ubuntu with firefox -- 84 sec
[*]ubuntu with epiphany -- 112 sec
[*]Win XP Prof with ie6.0 on virtualbox in ubuntu -- 51 sec
[/LIST]

Other Machines in the house:
[LIST]
[*]iMac with safari -- 6 sec
[*]Win XP Prof with ie 6.0 -- 7 sec (Wireless Laptop)
[*]Win XP Home with ie 7.0 -- 6 sec 
[/LIST]

---

### Post by izizzle on 2009-06-17
I tried getting on, very slow with a 3.0 mbps connection and 350 kbps upload rate. Something to do with their servers...

---

### Post by lavinog on 2009-06-19
I tested it with wget and got ~ 1kbps with ubuntu and ~ 120kpbs with xp (same machine)
I also tried different user agent strings with no change in speed.

---

### Post by heitjer on 2009-06-19
> **lavinog said:**
> I tested it with wget and got ~ 1kbps with ubuntu and ~ 120kpbs with xp (same machine)

Do you dual boot into XP? That would explain the better results. My XP in Virtualbox in ubuntu is not really faster.

---

### Post by cknight on 2009-06-20
I see this issue too.  Has anyone raised a bug report for this?

---

### Post by heitjer on 2009-06-20
I am not sure where to raise a bug report, never did this before. All I did was an email to the RV.net webmaster. But no official reply yet.

---

### Post by cknight on 2009-06-21
Right, I seemed to have fixed this for me.  Went to raise a bug and found this [bug report]("https://bugs.launchpad.net/bugs/89160") on a similiar network issue.  [This site in particular]("http://inodes.org/blog/2006/09/06/tcp-window-scaling-and-kernel-2617/") was rather helpful in understanding what the heck was going on.  Running the following command showed a similiar pattern:
```
sudo tcpdump -i any port 80
```

Basically, it looks like my router is the issue and Linux valiantly requires it to hold true to the TCP spec for window-scaling which the router isn't dealing with particularly well with.

I'll struggle with layman's terms here, but what I think is happening is that the router is getting confused with the size of the network packets beging sent from [www.rv.net](www.rv.net) and basically shouts "Hey, that's to big, I don't know what to do with it", so the site retransmits at a smaller size (way to small in this instance).  

Anyway, enough background which you probably don't care about.  Here's what I did to fix it for me:
```
gksudo gedit /etc/sysctl.conf
```

...add the following two lines 
```
net.ipv4.tcp_wmem = 4096 16384 131072
net.ipv4.tcp_rmem = 4096 87380 174760
```

...then restart sysctl with
```
sysctl -p
```

which forces the network to start off with a smaller max packet communication so it won't do the drastic drop off we're experiencing.  I've probably totally butchered my explanations here, so sincere apologies to all network administrators/experts out there!

I'm curious about the side effects of doing the above and have opened [this thread]("http://ubuntuforums.org/showthread.php?t=1193579") to discuss/discover. Hope this helps someone.

---

### Post by heitjer on 2009-06-21
THANKS a bunch cknight!

This fixed it for me after a re-boot! Blazing fast!

---

### Post by cknight on 2009-06-21
> **heitjer said:**
> THANKS a bunch cknight!

This fixed it for me after a re-boot! Blazing fast!

No problem.  Glad it helped!  And in a way, your quest helped me. I finally found a workaround (in one of my referenced links) to a firefox/google issue I've had for years.

---

### Post by paperplate9 on 2009-06-21
Beat me to it. I once discovered this problem as well. Worked fine under Windows but not under Linux. Turns out Windows doesn't use window scaling. Disabled tcp_windowscaling and worked fine.

Another problem where it seems like my internet connection randomly gets lost....culprit was tcp_timestamps.

---

### Post by Dummy46032 on 2010-01-06
> **cknight said:**
> Right, I seemed to have fixed this for me.  Went to raise a bug and found this [bug report]("https://bugs.launchpad.net/bugs/89160") on a similiar network issue.  [This site in particular]("http://inodes.org/blog/2006/09/06/tcp-window-scaling-and-kernel-2617/") was rather helpful in understanding what the heck was going on.  Running the following command showed a similiar pattern:
```
sudo tcpdump -i any port 80
```Basically, it looks like my router is the issue and Linux valiantly requires it to hold true to the TCP spec for window-scaling which the router isn't dealing with particularly well with.

I'll struggle with layman's terms here, but what I think is happening is that the router is getting confused with the size of the network packets beging sent from [www.rv.net]("http://www.rv.net") and basically shouts "Hey, that's to big, I don't know what to do with it", so the site retransmits at a smaller size (way to small in this instance).  

Anyway, enough background which you probably don't care about.  Here's what I did to fix it for me:
```
gksudo gedit /etc/sysctl.conf
```...add the following two lines 
```
net.ipv4.tcp_wmem = 4096 16384 131072
net.ipv4.tcp_rmem = 4096 87380 174760
```...then restart sysctl with
```
sysctl -p
```which forces the network to start off with a smaller max packet communication so it won't do the drastic drop off we're experiencing.  I've probably totally butchered my explanations here, so sincere apologies to all network administrators/experts out there!

I'm curious about the side effects of doing the above and have opened [this thread]("http://ubuntuforums.org/showthread.php?t=1193579") to discuss/discover. Hope this helps someone.

I have been plagued with this bug for quite some time.  I read RV Net Open Road Forum quite a bit and always have this problem, except for PClinuxOS which is the only distro that ever worked fast with rv.net.  

Thanks so much for the fix, it works like a charm now...

Mike

---

### Post by pricetech on 2010-01-12
Same issue is occurring with Verizon's website.  There's a thread about it here:

[http://ubuntuforums.org/showthread.php?t=1377513](http://ubuntuforums.org/showthread.php?t=1377513)

---

