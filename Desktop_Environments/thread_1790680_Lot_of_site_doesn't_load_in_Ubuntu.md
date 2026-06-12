---
title: "Lot of site doesn't load in Ubuntu"
date: 2011-06-25
forum: Desktop Environments
---

### Post by tre4321 on 2011-06-25
First of all let me tell you all that I'm newbie to Linux, I have been using Windows for 5 years now but Ubuntu 10.04 LTS for about 3 days on my laptop. My problem is that some (should I say most?) sites such as myspace, yahoo mail tinypic and a lot of random sites aren't opening in Ubuntu. I can access few sites, in fact I'm posting this thread from the same laptop. At first I thought it was DNS problem , so I changed it to Google public DNS. When I wget myspace or other sites that I can't access it resolves correctly but gets stuck displaying **HTTP request sent, awaiting response...** after that I get an error message. I don't think it's ISP problem as I can access all sites using my Windows desktop. Analyzing the connection at [http://www.speedguide.net/analyzer.php](http://www.speedguide.net/analyzer.php) shows[COLOR=#228b22]
[/COLOR][PHP]Default TCP Receive Window (RWIN) = 5824 
                        RWIN Scaling (RFC1323) = 6 bits                          (scale factor: 2^6=64)                                                
                        Unscaled TCP Receive Window = 91 
                        
Under many Linux distributions, the Analyzer only shows the Current TCP Window.
RWIN seems to be set to a very small number. If you're on a broadband connection, consider using a larger value.
For optimum performance, consider changing RWIN to a multiple of MSS.
Other RWIN values that might work well with your current MTU/MSS: 
[/PHP]I think RWIN is the problem but don't know how to change it. I'm using firefox and chrome BTW.
Your help would be appriciated :)

---

### Post by tre4321 on 2011-06-25
Guys I'm extremely sorry for bumping this thread but it's been two hours, I can't open most of the sites, I really need yahoo to check my emails.

---

### Post by flemur13013 on 2011-06-25
FWIW, I get that same message (except my RWIN=5888   ) and have no internet problems, speed or otherwise.  I'm too dumb to give any more useful help.

---

### Post by tre4321 on 2011-06-25
Thanks for letting me know, I think there's something other than the RWIN is wrong then. I've been talking with my friend Google for hours without success but its hard to communicate with him when 90% of the links shown there ain't opening.

---

### Post by tre4321 on 2011-06-25
Still no luck guys,  Somebody help me out. I'll wait some more time and see if I get any help or I see a reformat in future :)

---

### Post by ibrrfarr on 2011-06-25
I'm running 11.04 and have no problems accessing anything.  Your numbers are way lower than mine; however if it's saying waiting or whatnot and then gives you an error, this sounds like you're not connecting via the ethernet.  I would call your ISP and ask them straightforward first as Ubuntu doesn't really *connect* you to a site, it is your browser that connects.  One of the few exceptions in problems with browsers is ActiveX which IE has control over.  I have to emulate it for the work I do and sometimes it works and sometimes it doesn't.  Now, as you may or may not know, if the site you go to *requires* IE then you can try Wine, Crossover, etc.

Good luck.

Thought I better add IE is proprietary software (copyright, blah, blah).  Thus, M*crosoft controls it.  Obviously, MS doesn't want to play nice with open source so they do not allow the packaging.  Firefox comes with Ubuntu and others as its open source(by-in-large).  Google crossover I think it is and get the trial edition and try it if your ISP has no clue.

---

### Post by tre4321 on 2011-06-25
Thanks for the info, I only wish I could understand it. My problem is somewhat similar to this [http://ubuntuforums.org/showthread.php?t=1388546](http://ubuntuforums.org/showthread.php?t=1388546) My ISP doesn't even have a customer support number, let alone helping me. I'm sure as hell they won't have a clue what ubuntu is.

Below are my tracepath results, One for google.co.in which perfectly opens and the other is for tinypic which doesn't open.

[PHP]tracepath google.co.in
 1:  117.198.48.82 (117.198.48.XX)                          0.170ms pmtu 1492
 1:  117.198.48.1 (117.198.48.1)                           66.433ms 
 1:  117.198.48.1 (117.198.48.1)                           64.142ms 
 2:  218.248.168.198 (218.248.168.198)                     65.941ms 
 3:  59.163.206.181.static.chennai.vsnl.net.in (59.163.206.181) 358.670ms asymm 13 
 4:  no reply
 5:  no reply
 6:  no reply
 7:  no reply
 8:  no reply
 9:  no reply
10:  no reply
11:  no reply
12:  no reply
13:  no reply
14:  no reply
15:  no reply
16:  no reply
17:  no reply
18:  no reply
19:  no reply
20:  no reply
21:  no reply
22:  no reply
23:  no reply
24:  no reply
25:  no reply
26:  no reply
27:  no reply
28:  no reply
29:  no reply
30:  no reply
31:  no reply
     Too many hops: pmtu 1492
     Resume: pmtu 1492 
[/PHP]

[PHP]tracepath tinypic.com
 1:  117.198.48.82 (117.198.48.XX)                          0.178ms pmtu 1492
 1:  117.198.48.1 (117.198.48.1)                           64.486ms 
 1:  117.198.48.1 (117.198.48.1)                           63.869ms 
 2:  218.248.168.198 (218.248.168.198)                     66.386ms 
 3:  59.163.206.181.static.chennai.vsnl.net.in (59.163.206.181) 362.639ms asymm 13 
 4:  59.163.16.1.static.vsnl.net.in (59.163.16.1)         355.724ms asymm 14 
 5:  121.240.226.26.static-mumbai.vsnl.net.in (121.240.226.26) 367.912ms asymm 13 
 6:  if-15-1-0.core1.MLV-Mumbai.as6453.net (209.58.105.153) 357.874ms asymm 11 
 7:  if-2-1-0-0.tcore1.MLV-Mumbai.as6453.net (180.87.38.21) 351.898ms asymm 11 
 8:  if-3-2.tcore1.PYE-Paris.as6453.net (80.231.154.70)   365.880ms asymm 10 
 9:  no reply
10:  no reply
11:  ae-34-52.ebr2.Paris1.Level3.net (4.69.139.225)       338.730ms asymm  9 
12:  ae-44-44.ebr2.Washington1.Level3.net (4.69.137.62)   351.873ms asymm 10 
13:  ae-5-5.ebr2.Washington12.Level3.net (4.69.143.222)   353.873ms asymm 11 
14:  ae-6-6.ebr2.Chicago2.Level3.net (4.69.148.146)       357.927ms asymm 10 
15:  ae-1-100.ebr1.Chicago2.Level3.net (4.69.132.113)     359.893ms asymm 10 
16:  ae-3-3.ebr2.Denver1.Level3.net (4.69.132.61)         399.791ms asymm 13 
17:  ae-21-52.car1.Denver1.Level3.net (4.69.147.99)       397.896ms asymm 13 
18:  no reply
19:  no reply
20:  no reply
21:  no reply
22:  no reply
23:  no reply
24:  no reply
25:  no reply
26:  no reply
27:  no reply
28:  no reply
29:  no reply
30:  no reply
31:  no reply
     Too many hops: pmtu 1492
     Resume: pmtu 1492 
[/PHP]

Again, both sites work perfectly when using Windows XP from my desktop.

---

### Post by Geffers on 2011-06-26
> **tre4321 said:**
> First of all let me tell you all that I'm newbie to Linux, I have been using Windows for 5 years now but Ubuntu 10.04 LTS for about 3 days on my laptop. My problem is that some (should I say most?) sites such as myspace, yahoo mail tinypic and a lot of random sites aren't opening in Ubuntu. 

Welcome to the Linux world, I've been using Linux (Mainly Ubuntu) for some years and have not had any major problems.

What are the following like;

[www.bbc.co.uk](www.bbc.co.uk)
[www.itv.com](www.itv.com)
[www.sky.com](www.sky.com)
[www.ibm.com](www.ibm.com)
[www.bt.com](www.bt.com)

I assume you are using Firefox, you could try another popular Linux browser epiphany.

To install open a Terminal (application, accessories, terminal) and type 
```
sudo apt-get install epiphany-browser
```

It will ask you for your administrator password then it will install.

Stay with it, it can only be an unfortunate minor problem.

Geffers

---

### Post by Sylslay on 2011-06-26
MTU is to big and then web is not working try to change it

 in console 

ifconfig eth0 mtu 1412

were 1412 is size mtu. Range from 1400-1500 for Broband

Source:[http://en.wikipedia.org/wiki/Maximum_transmission_unit](http://en.wikipedia.org/wiki/Maximum_transmission_unit)

In computer networking, the maximum transmission unit (MTU) of a communications protocol of a layer is the size (in bytes) of the largest protocol data unit that the layer can pass onwards. MTU parameters usually appear in association with a communications interface (NIC, serial port, etc.). Standards (Ethernet, for example) can fix the size of an MTU; or systems (such as point-to-point serial links) may decide MTU at connect time.

[http://www.dslreports.com/faq/695](http://www.dslreports.com/faq/695)  Max MTU: How do I find mine?

---

### Post by tre4321 on 2011-06-26
All the site opens but doesn't load completely, I see at the bottom of  firefox something like "waiting for bbc.112.2o7.net" in case of sky.com  it's "waiting for metrics.sky.com" for ITV it's "waiting for  tweetriver.com" seriously guys, all of them opens correctly from  windows.
I tried it on Chrome too, same problem.

@sylslay ifconfig eth0 mtu 1412 took my wired connection down. Had to change it to 1492 to make it work again. I tried following [http://www.dslreports.com/faq/695](http://www.dslreports.com/faq/695) as you mentioned but whatever MTU value I try I never get the "packet needs to be fragmented" error message. Also whatever value I try I never get the 0% packet loss. Below result of pinging tinypic.com at 1412 MTU

[PHP]PING tinypic.com (209.17.70.143) 1412(1440) bytes of data.
1420 bytes from 209.17.70.143: icmp_seq=2 ttl=243 time=412 ms
1420 bytes from 209.17.70.143: icmp_seq=3 ttl=243 time=413 ms
1420 bytes from 209.17.70.143: icmp_seq=4 ttl=243 time=408 ms
1420 bytes from 209.17.70.143: icmp_seq=5 ttl=243 time=406 ms
1420 bytes from 209.17.70.143: icmp_seq=6 ttl=243 time=410 ms
1420 bytes from 209.17.70.143: icmp_seq=7 ttl=243 time=405 ms
1420 bytes from 209.17.70.143: icmp_seq=8 ttl=243 time=408 ms
1420 bytes from 209.17.70.143: icmp_seq=9 ttl=243 time=404 ms
1420 bytes from 209.17.70.143: icmp_seq=10 ttl=243 time=406 ms
1420 bytes from 209.17.70.143: icmp_seq=11 ttl=243 time=412 ms
1420 bytes from 209.17.70.143: icmp_seq=13 ttl=243 time=416 ms
1420 bytes from 209.17.70.143: icmp_seq=14 ttl=243 time=408 ms
1420 bytes from 209.17.70.143: icmp_seq=16 ttl=243 time=413 ms
^C1420 bytes from 209.17.70.143: icmp_seq=17 ttl=243 time=408 ms

--- tinypic.com ping statistics ---
17 packets transmitted, 14 received, 17% packet loss, time 120088ms
rtt min/avg/max/mdev = 404.429/409.696/416.476/3.442 ms
[/PHP]Also I should have mentioned earlier that I'm connected in PPPoE mode. My bandwidth limit is 512kbps till I reach 6GB then the speed goes down to 256kbps for the rest of the month. Currently it's 256kbps.

---

### Post by SeijiSensei on 2011-06-26
Are you running AdBlockPlus or some other ad-blocking software?  The site 2o7.net, for instance, is an advertising service that's routinely blocked by AdBlockPlus.

If you're not running AdBlockPlus, try [installing]("https://addons.mozilla.org/en-US/firefox/addon/adblock-plus/") it and see if it helps.  You can tell it to ignore problematic sites like 2o7.net if they're not already blocked by one of the ABP rulesets like EasyList.

Got any blocks in your /etc/hosts file?  Using the same DNS provider in Ubuntu as in Windows?

---

### Post by tre4321 on 2011-06-27
My etc/hosts file has no entries added to it so I think nothing is blocked in there. I have adblock plus. I tried with abblock plus and tried uninstalling it too. I don't think adblock  plus is causing problem as Chrome has problem opening those sites too.

Actually tinypic.com loads but static.tinypic.com doesn't load.

Heres the wget output of tinypic.com and static.tinypic.com

[PHP]wget tinypic.com
--2011-06-27 11:06:09--  http://tinypic.com/
Resolving tinypic.com... 209.17.70.143
Connecting to tinypic.com|209.17.70.143|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]
Saving to: `index.html'

    [    <=>                                ] 19,111      12.8K/s   in 1.5s   

2011-06-27 11:06:13 (12.8 KB/s) - `index.html' saved [19111]
[/PHP]

[PHP]wget static.tinypic.com
--2011-06-27 11:07:17--  http://static.tinypic.com/
Resolving static.tinypic.com... 68.232.44.19
Connecting to static.tinypic.com|68.232.44.19|:80... connected.
HTTP request sent, awaiting response...
[/PHP]
It just shows awaiting response... after 5 minute I got bored and hit Ctrl+C

---

### Post by Borts on 2011-06-27
You might wanna try this:  sudo sysctl net.ipv4.tcp_mtu_probing=2  Worked for me once, maybe it will work for you too. By any chance, are you using 3G or GPRS connection?

---

### Post by Borts on 2011-06-27
Also you can try this:
```
sudo sysctl net.ipv4.tcp_timestamps=0
```Do you have any problems accessing flash-based or https websites? Since it's all working good in Win, there should be little fix for Ubuntu.
Hmm.. looks like yahoo mail uses https too. I had problems with gmails (https), changing MTU value solved that issue, so give it a try.
 
Although, it worked for me when I had 10.10, after clean install of 11.04 none of https websites are opening, even after sudo "sysctl net.ipv4.tcp_mtu_probing=2" >_>

Also, after executing those 2 commands you should try it without (!!) restarting the system. To set these values permanently, you need to modify sysctl.conf. So just execute them and try yahoo mail.

---

### Post by tre4321 on 2011-06-27
It didn't work for me, Connection is same as it was. Nah, I'm on DSL (Guys this is what gets sold as broadband here)
I can access some of SSL sites but not all. I tried wget [https://static.tinypic.com](https://static.tinypic.com) but got a weird output. Also wget [https://google.co.in](https://google.co.in) shows weird result saying certificate is invalid.
[PHP]--2011-06-28 02:35:42--  https://google.co.in/
Resolving google.co.in... 74.125.236.80, 74.125.236.84, 74.125.236.83, ...
Connecting to google.co.in|74.125.236.80|:443... connected.
ERROR: certificate common name `www.google.com' doesn't match requested host name `google.co.in'.
To connect to google.co.in insecurely, use `--no-check-certificate'.
[/PHP]
When I visit [https://google.co.in](https://google.co.in) my browser automatically redirects me to [http://google.co.in](http://google.co.in)
[PHP]https://static.tinypic.com
--2011-06-28 02:21:40--  https://static.tinypic.com/
Resolving static.tinypic.com... 68.232.44.19
Connecting to static.tinypic.com|68.232.44.19|:443... connected.
ERROR: certificate common name `gp1.wac.edgecastcdn.net' doesn't match requested host name `static.tinypic.com'.
To connect to static.tinypic.com insecurely, use `--no-check-certificate'.[/PHP]
[PHP]wget https://static.tinypic.com --no-check-certificate
--2011-06-28 02:22:27--  https://static.tinypic.com/
Resolving static.tinypic.com... 68.232.44.19
Connecting to static.tinypic.com|68.232.44.19|:443... connected.
WARNING: certificate common name `gp1.wac.edgecastcdn.net' doesn't match requested host name `static.tinypic.com'.
HTTP request sent, awaiting response... 404 Not Found
2011-06-28 02:22:30 ERROR 404: Not Found.
[/PHP]


Now I have a strong feeling that my ISP is somehow related to this. Maybe somehow I'm infected, I'm scared as I used the modified Ubuntu DVD that came with my laptop to install Ubuntu. BTW when I visit edgecastcdn.net I get a 404 error.

---

### Post by Hulkiedulkie on 2011-06-27
I'm wondering: have you thougth of a hardware issue?
 
Is this the same pc that you used to have windows on? Did it work fine before you installed Ubuntu?
 
Are you working wired or wireless? Try both. 
Have you tried a different cable or different port on your router/switch?

---

### Post by tre4321 on 2011-06-27
My connection is extremely simple. A modem which has no wireless support and has just 1 LAN port. Before installing Ubuntu the same laptop perfectly opened the sites. Also I'm using the same modem and LAN cable with Windows so I think there's no hardware problem. BTW do you guys know any free or trail VPN which works which works with Ubuntu, so I can check if I could access those sites with VPN.

---

### Post by jerrrys on 2011-06-27
really don't know if this has anything to due with your problem, but have you downloaded "ubuntu restricted extras" and plugins?  if not, they are in the software center

---

### Post by Borts on 2011-06-28
I'm almost 100% sure that there is nothing wrong with hardware.
The best thing you can do, as for VPN or proxy, is to install Tor:
[https://www.torproject.org/](https://www.torproject.org/)
Not hard to configure, and stable pretty much, just follow steps on FAQ page, but website is https, so... I'm not sure that it will even open.
Also, there is USA IP VPN:
[http://www.usaip.eu/](http://www.usaip.eu/)
Which is easier, you just get free VPN, which disconnects every 7 minute, but it's enough to try and see that it's working. There is HOW-TO for Ubuntu configuration.
And if you have enough time, you can install both Win and Ubuntu on dual boot, then you can check if connection is working on Win.
I had exactly same problem before (it was working fine on Win and didn't work on Ubuntu), now I have similar problem, with https websites, so I prefer using Tor. Stable, secure, fast.
Good luck with problem solving.

---

### Post by Sylslay on 2011-06-28
Post Yours nerwork interface hrere:
Are You usie cable or wi-fi?

> ifconfig wlan0 mtu 1492 

or other wi-fi card.

---

### Post by Hulkiedulkie on 2011-06-28
> **Borts said:**
> I'm almost 100% sure that there is nothing wrong with hardware.
The best thing you can do, as for VPN or proxy, is to install Tor:
[https://www.torproject.org/](https://www.torproject.org/)
Not hard to configure, and stable pretty much, just follow steps on FAQ page, but website is https, so... I'm not sure that it will even open.
Also, there is USA IP VPN:
[http://www.usaip.eu/](http://www.usaip.eu/)
Which is easier, you just get free VPN, which disconnects every 7 minute, but it's enough to try and see that it's working. There is HOW-TO for Ubuntu configuration.
And if you have enough time, you can install both Win and Ubuntu on dual boot, then you can check if connection is working on Win.
I had exactly same problem before (it was working fine on Win and didn't work on Ubuntu), now I have similar problem, with https websites, so I prefer using Tor. Stable, secure, fast.
Good luck with problem solving.
 
I'd advise to NOT use TOR.
Your connection will be abused and this will get your ip-address blacklisted, sometimes with no way to turn it back. Your ISP may even disconnect you from the internet. 
I work at an ISP and people who use TOR are usually blacklisted within a day because of hundreds of abuse complaints (spamming, portscans, botnets, ddos).
 
I haven't heard about the VPN option but that seems pretty insecure also.

---

### Post by tre4321 on 2011-06-28
@jerrrys if you are talking about the flash or other softwares bundled in the same package, I have that.

@Borts I haven't tried tor as it'll take ages for me to download a 24MB file. I tried the VPN but Ubuntu doesn't like to connect to it. I tried 2 VPN service provider but Ubuntu has problem with both of them. **At first it gave me The VPN connection 'XXXXX' faild to start because the VPN service failed to start.** I managed to fix it by unchecking the Available to all users checkbox but then a second problem appears, now it says **The VPN connection 'XXXXX' failed to start.** These continuous error after error is driving me crazy, now it makes me think that contrary to popular belief Linux is more buggy than Windows. (pun intended)

@Sylslay I'm connected via cable to modem using PPPoE mode. Don't know how to check the network interface.

@Hulkiedulkie I'm on DCHP and most of the IP I get is already blacklisted from various site due to abuse by other users :( I don't have to worry about getting banned by ISP as my ISP isn't advanced to do such things. Also to someone to complain they'll need a customer support of the ISP whic mine doesn't have xD. I still don't understand how VPNs can be insecure though.

EDIT: https:// stopped working too in most of the sites. Also a site [http://indiansforguns.com](http://indiansforguns.com) which was opening fine even after installing Ubuntu, just stopped opening. All I see is **Waiting for indiansforguns....** I'm getting really tired of this guys. Is there any other distro you recommend which doesn't have these bugs.

---

### Post by tre4321 on 2011-06-28
Bump!

---

### Post by AmirM on 2011-06-29
Hi!
mmm...as u mentioned I had a nearly same problem 2 times(i just asked for help for first time).
I donno if this helps u , but my problem was solved automatically both times!
-----------
Someone in another forum told me that he solved it by changing MTU , did u try that? 
(I didnt change MTU and problem was fixed automatically)

---

### Post by tre4321 on 2011-06-29
In my case it's not getting fixed automatically. How long did it take you to get it fixed automatically? I tried to set MTU value but couldn't find the appropriate value as I never get the "packet needs to be fragmented" error message.

---

### Post by Borts on 2011-06-29
> **Hulkiedulkie said:**
> I'd advise to NOT use TOR.
Your connection will be abused and this will get your ip-address blacklisted, sometimes with no way to turn it back. Your ISP may even disconnect you from the internet. 
I work at an ISP and people who use TOR are usually blacklisted within a day because of hundreds of abuse complaints (spamming, portscans, botnets, ddos).
 
I haven't heard about the VPN option but that seems pretty insecure also.

IP would get blacklisted if you set yourself as an exit node. Otherwise, you are just a user, connected to VPN network. It's not necessary to set up your system as a relay for other users. Your ISP is lucky that they have you and you know what Tor is. USA IP VPN is free, so you can't really expect much from it. Too bad it didn't work, but I can't remember any other free VPN which is easy to set up. @tre4321 It doesn't &quot;fix automatically&quot;, probably, AmirM run updates on system, which fixed the issue. You might update yours, or just get yourself another copy, as 11.04. Or install Win on your laptop AND Ubuntu inside. It's not hard at all, there is something called Wubi which will help you a lot. Also, you can connect your system to another connection, if you have an opportunity to do that. Then you will see if it's not working only on your particular connection or there is something wrong with distro.  Btw, you can use many anonymous websites. Our ISP restricts loads of websites, so I use all what I've mentioned myself. [http://bind2.com/](http://bind2.com/) It isn't secure that much for such things as email and such, but I still use, since I have no other choice (except Tor). But it will unblock most of the websites, at least you can surf easily, give it a try.

---

### Post by Borts on 2011-07-09
GODS! I had this problem, almost the same, for a month or so. And I was looking for a solution. I got adapted to slow speed and that half of websites are not opening, although, I still wanted it to work fine. SO:
```
ifconfig eth0 mtu 587
```You should change **eth0 **to your interface, of course. I changed value of MTU to LOWER one, http analyzer was totally cursing me, saying that I need to increase MTU value, but when I tried websites that didn't open (gmail, other https) and services that didn't work (Pidgin accounts with XXMP protocol)- it worked. Plus, faster than it did before.
Try it, hope it works. Btw, it's way to set MTU only temporary, if it works- then you should set it permanently.
Hope you solved this problem or you still looking for a solution.
That a point about Linux or Ubuntu- you don't give up on it. :)
CAUSE IT WORKS!
Also, I have dual boot Ubuntu with Win7, AND it doesn't work on Win. So Ubuntu is the best.

---

