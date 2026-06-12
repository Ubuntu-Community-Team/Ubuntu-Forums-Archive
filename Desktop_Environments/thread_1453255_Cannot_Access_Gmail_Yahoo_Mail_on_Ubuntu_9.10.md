---
title: "Cannot Access Gmail Yahoo Mail on Ubuntu 9.10"
date: 2010-04-13
forum: Desktop Environments
---

### Post by FirstByté on 2010-04-13
For about 2weeks rolling now, I've not been able to check my GMail, Yahoo!Mail accounts [nor can I post messages on facebook.. yes I do facebook too ].

I noticed this about 2weeks ago. At first I thought it was just an issue with my ISP. Lately I discovered it's not from my ISP, since **[COLOR="Red"]I could access all these websites on the Vista environment[/COLOR]** [I dual-boot]. Even on a Virtual Win XP, I still can't access these pages.

**Symptoms:**
_GMail_
- When I key-in my log-in details... it just sits as white-screen and signals "[DONE!!]". It goes no further

_Yahoo!Mail_
- When I successfully my log-in into my 'My Yahoo!', once I go "Inbox", all I see is my email headers. If I click any email, it just stalls for a while and then says "'SESSION EXPIRED' pls login!"


**Prevalence**
- I tried using Opera, Galeon, Firefox... but all behaved the same.
- On Virtual Win XP the behavior is same with Firefox.

**Attempts**
- Upgraded to the Firefox Namoroka -- still no help.
- Deleted Firefox Profile -- still no good [it even freezes with shockwave flash]
- Cleared Firefox cache -- still no head-ways
- 'Deleted' Wifi/LAN network connections -- no help
- Reset my W-Router no good.


**** Please pardon me if this is an unnecessary 'spam'. I hate returning to Windowz after several months of enjoying GNU GNomez!*

---

### Post by FirstByté on 2010-04-14
Bump!!!

HELP REQUIRED

---

### Post by MooPi on 2010-04-14
Have you tried this with a Live CD? Very strange indeed.

---

### Post by lovinglinux on 2010-04-15
Try to reinstall xulrunner.

---

### Post by easy2bid on 2010-04-15
It's a new problem...

---

### Post by PRC09 on 2010-04-15
I believe all of the sites mentioned use Flash on the login so have you tried installing it......

---

### Post by FirstByté on 2010-04-16
> **MooPi said:**
> Have you tried this with a Live CD? Very strange indeed.

I tried this with LiveCD [9.10] too and got strangely the same result.

Can it be that my ISP route packets based on information from browser fingerprints? 'Cause it works on MS without issues. 

While this my be just to pass some informatory message about such aberrant behavior, I might need time to try this system on various ISPs [at friend's location].
Hopefully tomorrow I should get come with updates.

> **lovinglinux said:**
> Try to reinstall xulrunner.
Do other browsers such as Chrome,Opera et. al. use xulrunner too? I discovered however that I can get to my Yahoo mail through the mobile link [[http://m.yahoo.com/]](http://m.yahoo.com/]). I know it's crazy but I'm puzzled. GMail checks F.Print even for [http://m.google.com](http://m.google.com) and 'forces' the [http://www.google.com](http://www.google.com) version.


And like **PRC09** said, I guess the issue is rather unique with Flash related sites. As mentioned above, I started noticing this about 28th of March [when I suspect some (experimental) Namoroka ports of were back-ported into Firefox 3.5.X], I might be wrong on this though.


***Thank you all for you speedy response. I'll keep trying till this is resolved.***

---

### Post by lovinglinux on 2010-04-16
> **FirstByté said:**
> Can it be that my ISP route packets based on information from browser fingerprints? 'Cause it works on MS without issues.

I don't think they would do that, but the site, probably.

> **FirstByté said:**
> Do other browsers such as Chrome,Opera et. al. use xulrunner too? 

There are other browsers that use xulrunner, but not those you have mentioned. Sorry, I missed that information on your first post. Reinstalling xulrunner won't help.

> **FirstByté said:**
> And like **PRC09** said, I guess the issue is rather unique with Flash related sites. As mentioned above, I started noticing this about 28th of March [when I suspect some (experimental) Namoroka ports of were back-ported into Firefox 3.5.X], I might be wrong on this though.

No, you are probably correct. There are lots of users with flash problems in Namoroka, because of recent updates. See quote below:

> **lovinglinux said:**
> **[SIZE="4"]Attention Firefox 3.6.4 [Namoroka] ubuntu-mozilla-daily users![/SIZE]**

It seems this is a bug affecting only Firefox 3.6.4 [Namoroka] installed using the *ubuntu-mozilla-daily* ppa. The browser crashes when viewing pages with flash content or content for other plugins.

This problem is due to a bad/old implementation of the new Lorentz technology that should prevent flash from crashing the browser. When opening a page with flash content using Namoroka 3.6.4, there is a new *firefox-bin* process loaded and the browser crashes. 

[Firefox 3.6.4 Lorentz from Mozilla](http://www.mozilla.com/en-US/firefox/lorentz/) doesn't behave like this and instead of loading a new *firefox-bin* process, it loads a *mozilla-runtime* process, which takes care of the flash content. It works like a charm and the browser doesn't crash or lock, even if you are viewing a messed up flash video.

So you have 3 options to fix your problem:

[LIST]
[*]disable *ubuntu-mozilla-daily* and reinstall Firefox to downgrade it to the default browser version
[*]temporarily turn off the flash process isolation following [these instructions](http://ubuntuforums.org/showpost.php?p=9104945&postcount=19)
[*]download [Firefox 3.6.4 Lorentz from Mozilla](http://www.mozilla.com/en-US/firefox/lorentz/) and follow [these instructions](http://lovinglinux.megabyet.net/?page_id=220##1---Manual-installation-of-fresh-final-releases-from-Mozilla-3) to install it.
[/LIST]

There are some considerations about using a ppa repository for Firefox that I would like to highlight:
[LIST]
[*]some ppa repositories like *ubuntu-mozilla-daily* update not only Firefox, but also other Mozilla applications, like Thunderbird.
[*]some ppa repositories like ubuntu-mozilla-daily install development versions of Firefox which does not have the official branding (logo and name). Although they use essentially the same source code, the browser could be called Shiretoko, Namoroka or something else.
[*] some repositories like *mozillateam/firefox-stable* doesn’t seem to be updated frequently, thus missing important security patches.
[*]some repositories like *ubuntu-mozilla-daily* upgrade Firefox with unstable releases, sometimes causing issues, like crashing the browser in specific conditions or preventing it from starting.
[/LIST]

Please Before adding a ppa repository for Firefox, please make sure you understand how the repository works, which version it will install and how often it will provide updates.[color="Sienna"][list]

[*]**Source:** [[color="DarkSlateGray"] Re: Firefox optimization and troubleshooting thread[/color]]("http://ubuntuforums.org/showpost.php?p=9112875")

[*]**Tags:** [[color="DarkSlateGray"]namoroka 3.6.4pre crash flash problem[/color]]("http://www.google.com/search?q=namoroka+3.6.4pre+crash+flash+problem+site:ubuntuforums.org")

[*]**Powered by: **[[color="DarkSlateGray"]QuoteMarks[/color]]("http://lovinglinux.megabyet.net/?page_id=555")[/list][/color]

---

### Post by FirstByté on 2010-04-18
Permit me all to apologize to Ubuntu for raising false flag. I guess it has a problem to do with my ISP and dynamic sites. To fix this, I'm changing my ISP in 2week's time. 

I took my system to another friend's network running 15Mbps and it loaded smoothly and perfectly. On my network, it resets on every attempt.

**Thanks to all who contributed to my case. You guys are wonderful.**
:P

I'll be marking this '**SOLVED**'!

---

### Post by FirstByté on 2010-04-18
> **lovinglinux said:**
> I don't think they would do that, but the site, probably.



There are other browsers that use xulrunner, but not those you have mentioned. Sorry, I missed that information on your first post. Reinstalling xulrunner won't help.



No, you are probably correct. There are lots of users with flash problems in Namoroka, because of recent updates. See quote below:

[color="Sienna"][list]


[*]**Source:** [[color="DarkSlateGray"] Re: Firefox optimization and troubleshooting thread[/color]]("http://ubuntuforums.org/showpost.php?p=9112875")

[*]**Tags:** [[color="DarkSlateGray"]namoroka 3.6.4pre crash flash problem[/color]]("http://www.google.com/search?q=namoroka+3.6.4pre+crash+flash+problem+site:ubuntuforums.org")

[*]**Powered by: **[[color="DarkSlateGray"]QuoteMarks[/color]]("http://lovinglinux.megabyet.net/?page_id=555")[/list][/color]


Awesome, many thanks on this input. I didn't see it before my post. In any case, I may still consider my problem an ISP issue, 'cause since I disabled 'shockwave_flash', the graying-outs on flash sites have stopped though, that meant I can't view flash stuff :(.

My problem was(/is) having a white screen after 'logging-in' into GMail or seeing the mail contents of my Yahoo Mail; even though when I make any other search in Google, it shows my email (see attachments).

Many thanks.

---

### Post by FirstByté on 2010-05-02
[UPDATES]...

I tested my (wireless) broadband modem in another location and all seem to work fine (accessing my mails from Yahoo/Gmail on Ubuntu platforms). However I still wasn't able to read my mails on Linux when I later tried it at my place. Suspecting a problem with TTL fields, I ran a couple ping tests ans traceroutes to know the number of hops in my link.



After much trials and attempts... I came up with this results:

```

firstbyte@P34CE:~$ ping 64.233.181.104
PING 64.233.181.104 (64.233.181.104) 56(84) bytes of data.
64 bytes from 64.233.181.104: icmp_seq=1 ttl=64 time=125 ms
64 bytes from 64.233.181.104: icmp_seq=2 ttl=64 time=118 ms
64 bytes from 64.233.181.104: icmp_seq=3 ttl=64 time=75.1 ms
64 bytes from 64.233.181.104: icmp_seq=4 ttl=64 time=87.9 ms
64 bytes from 64.233.181.104: icmp_seq=5 ttl=64 time=92.9 ms
64 bytes from 64.233.181.104: icmp_seq=6 ttl=64 time=189 ms
64 bytes from 64.233.181.104: icmp_seq=7 ttl=64 time=87.8 ms
64 bytes from 64.233.181.104: icmp_seq=8 ttl=64 time=99.1 ms
64 bytes from 64.233.181.104: icmp_seq=9 ttl=64 time=98.1 ms
64 bytes from 64.233.181.104: icmp_seq=10 ttl=64 time=88.8 ms
64 bytes from 64.233.181.104: icmp_seq=11 ttl=64 time=65.1 ms
^C
--- 64.233.181.104 ping statistics ---
11 packets transmitted, 11 received, 0% packet loss, time 10013ms
rtt min/avg/max/mdev = 65.127/102.648/189.871/32.052 ms

```
```

firstbyte@P34CE:~$ ping 67.195.13.129
PING 67.195.13.129 (67.195.13.129) 56(84) bytes of data.
64 bytes from 67.195.13.129: icmp_seq=1 ttl=64 time=386 ms
64 bytes from 67.195.13.129: icmp_seq=2 ttl=64 time=407 ms
64 bytes from 67.195.13.129: icmp_seq=3 ttl=64 time=328 ms
64 bytes from 67.195.13.129: icmp_seq=4 ttl=64 time=352 ms
64 bytes from 67.195.13.129: icmp_seq=5 ttl=64 time=374 ms
^C
--- 67.195.13.129 ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4006ms
rtt min/avg/max/mdev = 328.970/369.868/407.855/27.306 ms
firstbyte@P34CE:~$ 

```

and from wireshark (excerpt)

```
1	0.000000 |	69.147.100.227	| 192.168.0.104	| ICMP	Time-to-live exceeded (Fragment reassembly time exceeded)
13	32.289698 |	192.168.0.104 |	69.147.100.227 |	TCP	[TCP Retransmission] [TCP segment of a reassembled PDU]
14 |	33.792091 |	69.147.100.227 |	192.168.0.104 |	ICMP	Time-to-live exceeded (Fragment reassembly time exceeded)
660	206.644988 | 	64.233.181.83 |	192.168.0.104 |	ICMP	Time-to-live exceeded (Fragment reassembly time exceeded)
691	223.643504 |	64.233.181.83 |	192.168.0.104 |	ICMP	Time-to-live exceeded (Fragment reassembly time exceeded)
```


**It's an ISP problem, but what puzzles me is why on the same system, in Windows Vista I can check my mails with no hustles but do not enjoy the same on Ubuntu(9.10, 10.04)!** How I hate to know I need to switch to Windows to send/check mails... I have sending mail issues with Zimbra too, so, Zimbra option out :)

Maybe an advice on this can help solve another occurrence of such in the future.

- Firstbyte

---

### Post by FirstByté on 2010-05-03
BUMP
BUMP


Any help or advice appreciated.



It's killing to see how no issues of such appears in Windoz Vista, but must I keep going to Vista to check/send mails?



Help PLEASE!!

---

### Post by infamous-online on 2010-05-03
Did you check to see if your firewall is blocking access to these programs?

---

### Post by FirstByté on 2010-05-03
> **infamous-online said:**
> Did you check to see if your firewall is blocking access to these programs?

Thanks for coming to my rescue. I'm not sure if any firewall was on. I wish it has one that I can address.

One this in apparent though: Windows uses **TTL** @ **"128"**; Ubuntu (Linux) uses **TTL** set @ **"64"** hops.

I tried 
```
sudo iptables -t mangle -A PREROUTING -i eth1 -j TTL --ttl-set 128 

```
I don't think I was able to modify the TTL it was still showing "64"
```

firstbyte@P34CE:~$ ifconfig eth1
eth1      Link encap:Ethernet  HWaddr 00:22:5f:2a:b5:f0  
          **inet addr:192.168.0.104  Bcast:192.168.0.255**  Mask:255.255.255.0
          inet6 addr: fe80::222:5fff:fe2a:b5f0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:81832 errors:0 dropped:0 overruns:0 frame:125748
          TX packets:47659 errors:6 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:114083599 (114.0 MB)  TX bytes:4814206 (4.8 MB)
          Interrupt:16 Base address:0xc000 

firstbyte@P34CE:~$ sudo **iptables** -t mangle -A PREROUTING -i **eth1** -j TTL --ttl-set **128**

firstbyte@P34CE:~$ ping 192.168.0.104
PING 192.168.0.104 (192.168.0.104) 56(84) bytes of data.
64 bytes from 192.168.0.104: icmp_seq=1 **ttl=64** time=0.041 ms
64 bytes from 192.168.0.104: icmp_seq=2 **ttl=64** time=0.034 ms
64 bytes from 192.168.0.104: icmp_seq=3 **ttl=64** time=0.042 ms
^C
--- 192.168.0.104 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2000ms
rtt min/avg/max/mdev = 0.034/0.039/0.042/0.003 ms


```

Thanks for the head-up.

---

### Post by FirstByté on 2010-05-03
Bump!

Bump!!

---

### Post by nick4mony on 2010-05-03
I've had a similar issue on Yahoo (don't use Gmail) on *all* Firefox versions:
[list]
[*]Firefox 3.0.19 on Ubuntu Hardy
[*]Firefox 3.5.9 on Win XP sp2
[*]Firefox 1.5.0.5 on Ubuntu Breezy (just to try)
[/list]
but I tried IceWeasel 2.0.0.12 on Knoppix - this was OK.

I do not think it's flash related - I don't have it installed anywhere (and it's not on Knoppix). I think that Yahoo have done something, because my Ubuntu Breezy used to work OK on Yahoo.

People have reported similar problems on the Firefox support page - but unlike some of the others, I *can still browse in other tabs* while this is going on.

I think I'll give Chrome a go - presumably I can apt-get this into Hardy ...?

---

### Post by FirstByté on 2010-05-04
> **nick4mony said:**
> I've had a similar issue on Yahoo (don't use Gmail) on *all* Firefox versions:
[list]
[*]Firefox 3.0.19 on Ubuntu Hardy
[*]Firefox 3.5.9 on Win XP sp2
[*]Firefox 1.5.0.5 on Ubuntu Breezy (just to try)
[/list]
but I tried IceWeasel 2.0.0.12 on Knoppix - this was OK. 
What makes me confused it this is peculiar only to Win XP and Ubuntu [9.10 & 10.04] distro that I have tried. On windoz Vista/7, none of the aforementioned sites (Facebook,Yahoo Mail, GMail et al.) has issues, even on same system :confused:

> **nick4mony said:**
> I do not think it's flash related - I don't have it installed anywhere (and it's not on Knoppix). I think that Yahoo have done something, because my Ubuntu Breezy used to work OK on Yahoo.

I switched back to Firefox 3.5.X and enabled flash and I can report to you that I don't have obvious flash issues.
> **nick4mony said:**
> 
People have reported similar problems on the Firefox support page - but unlike some of the others, I *can still browse in other tabs* while this is going on.

I think I'll give Chrome a go - presumably I can apt-get this into Hardy ...?

Good for you. 

Does anyone think the ISPs could be behind this stuff??? I'm frustrated and tired. I'll start from the top, ROUGHEN-IT OUT with my ISP first. Too bad they only want to support WINDOZ!! They freak me of, asking which OS I run, just because they wanna carry out a ping test! Crazy [windoz] world



Thanks great Community!:popcorn:

---

### Post by jatanr on 2010-05-06
Hi FirstByté,

I am seeing the exact same problem with Gmail and Yahoo mail when using Firefox or Chrome in Ubuntu 10.04. Did you find any solution for  this? 

Appreciate any help.

Thanks!

---

### Post by FirstByté on 2010-05-06
> **jatanr said:**
> Hi FirstByté,

I am seeing the exact same problem with Gmail and Yahoo mail when using Firefox or Chrome in Ubuntu 10.04. Did you find any solution for  this? 

Appreciate any help.

Thanks!

Thanks for confirming this "bug" too! I can only tell if we share similar problems if on the same system [somehow] you have any Windoz OS accessing those Mailing site.

I tried modifying the time-to-leave (TTL) portion of Ubuntu 9.10 [trust me, it's a *simple* thing to do(conceptualize) but hard to 'hark' that value]

After trying 
```
sudo iptables -t mangle -A PREROUTING -i eht1 -j TTL --ttl-set 128


``` with no success, I dropped down to modify the file itself

> sudo nano /proc/sys/net/ipv4/ip_default_ttl doing that from the **boot-up recovery menu** since it's a file I guess left open and marked by 'root' so you can't save from GDM environment. 

However, changing that TTL value from 64 [default] to 128 like windows never solved the problem either.

I can still confirm these pages not opening in Ubuntu 9.10/10.04 but do in Windows Vista at least.


I'll keep trying but I doubt if I can handle this with my shallow knowledge of Ubuntu/kernel :mad: :(
Hang in there.
In the meantime for your mails, you might install Zimbra so as to view your mail. Sending mails from Zimbra could be frustrating at times [at least from me!]

Someone please help!!!!

---

### Post by jatanr on 2010-05-09
An update: I reinstaller ubuntu on my desktop just to make sure that no other installation done by me is indavertently affecting this. But right after installation when I opened firefox and logged into my gmail account, I was again not able to open any emails. It showed "Loading.." at the top and then an error popup saying there may be some problem with my internet account etc.

Ditto for Yahoo Mail. I can reach the inbox, but if I click on any email in the upper pane (I use the new version of yahoo mail) the message does not load in the bottom page. After a few seconds it prints some error message saying that message failed to load. If I switch to yahoo classic, I still have the same issue. I can see my emails in the inbox, but if I click on any email, I cannot see its contents.

Everything works on my Winxp laptop on the same network. 

Can this be something to do with the ubuntu network settings? I am using a router with DHCP enabled and thats how my desktop and laptop get their ip addresses.

---

### Post by jatanr on 2010-05-09
On a related note... I am not able to use twitter using gwibber. I am able to add my twitter account to gwibber, but do not see any tweets from people I follow. If I try to post a tweet from gwibber, it does not get posted on my twitter page. There are no errors. The main gwibber window just remains blank.

Sorry for hijacking the thread. I think the issues may be related (to some network issue)

---

### Post by FirstByté on 2010-05-09
> **jatanr said:**
> An update: I reinstaller ubuntu on my desktop just to make sure that no other installation done by me is indavertently affecting this. 
I tried live CDs (8.10, 9.04, 10.04) all produced same results.  
> **jatanr said:**
> 
Everything works on my Winxp laptop on the same network. 

Can this be something to do with the ubuntu network settings? 

This got me thinking it's got something to do with ISP refusing to sent some "sort" of packets needed to establish such communication in Ubuntu.
I know so, 'cause I examined packets from my Win Vista through Wireshark, I noticed some 

```
ICMP Errors
0.000000 |	69.147.100.227	| 192.168.0.104	| **[COLOR="Red"]ICMP	Time-to-live exceeded (Fragment reassembly time exceeded)[/COLOR]**

```
but nevertheless, Windows somehow manages to get around it. That initially got me thinking it's got something to do with the Linux' TTL set to 64. Changing it to 128 through hacking didn't solve the issue.


Inside my Ubuntu I virtualize WinXP and it follows the same problem with the mailboxes. Interestingly all my other search parameters shows my email name, suggesting a successful login [[here]("http://ubuntuforums.org/attachment.php?attachmentid=153675&d=1271614478")]. [IMG]http://ubuntuforums.org/attachment.php?attachmentid=156247&d=1273454869[/IMG]

I also suspect something on the ISP side too because when I relocated my modem (wireless Wimax) to another location, I don't have this issues. However the process (cost) of switching ISPs in this side of the globe can be daunting at times [crazy contracts contracts contracts.. ](*,) ]. After working 2year+ on Ubuntu I hate to know that I have to always switch back to Vista just to send an email!!! 

It's painfully crazy! :'(

Can any Linux kernel [or Canonical] guy feel our pains and come to our rescue? :mad:

I wish this can be solved soon
:-k #-o

---

### Post by FirstByté on 2010-05-09
> **jatanr said:**
> On a related note... I am not able to use twitter using gwibber. I am able to add my twitter account to gwibber, but do not see any tweets from people I follow. If I try to post a tweet from gwibber, it does not get posted on my twitter page. There are no errors. The main gwibber window just remains blank.

Sorry for hijacking the thread. I think the issues may be related (to some network issue)

Just to add, is your system portable [like laptops etc]? If so, why not try trying it on a different network and see if this situation persist as well.

---

### Post by jatanr on 2010-05-10
Unfortunately, I have installed Ubuntu on a desktop, so I cannot try it at a friend's place :(

I have a winXP laptop but I cannot put ubuntu on it because its work laptop :( 

Thanks for your investigations FirstByté.

---

### Post by FirstByté on 2010-05-10
> **jatanr said:**
> Unfortunately, I have installed Ubuntu on a desktop, so I cannot try it at a friend's place :(

I have a winXP laptop but I cannot put ubuntu on it because its work laptop :( 

Thanks for your investigations FirstByté.

Do you have a Live CD or LiveCD-usb [downloaded or something] that you can run on the laptop without installation? You should be able to test Firefox from it without installing.

I concur you might need a network cable to reach the internet on first attempt though (assuming your laptop comes with a proprietary wireless card like my Dell).

---

### Post by jatanr on 2010-05-11
Good Idea FirstByté. I will give it a try and let you know if things work.

---

### Post by dobbod on 2010-05-11
Hi, I've the same problem as you since I used Ubuntu 9.10. I updated Firefox to verison 3.6.3 and after that I can't logged in into Gmail and Yahoomail. I think by upgrading to version 10.04 will solve the issue, but it is not. By keeping /Home in a parttion, Firefox will keep on loading the same bookmarks, saved passwords and etc, as in 9.10.

But, I can logged in into those 2 mails a few days ago, everything seems okay. I do not know why suddenly I can check my mails as usual. Again today, the problem happens again, I can't access those 2 mails.

---

### Post by Sentinel83 on 2010-05-11
FirstByté,

I saw your ping and wireshark information, but could you also try a traceroute to the destination?  Specifically, you can set a TTL to test various TTL values.  So, you can try the default (30 hops) or continually increase to see if there is a value that works.

```
traceroute *destination*
```

or 

```
traceroute -m *TTLvalue destination*
```

Do they provide any useful results?

---

### Post by FirstByté on 2010-05-14
> **Sentinel83 said:**
> FirstByté,

I saw your ping and wireshark information, but could you also try a traceroute to the destination?  Specifically, you can set a TTL to test various TTL values.  So, you can try the default (30 hops) or continually increase to see if there is a value that works.

```
traceroute *destination*
```

or 

```
traceroute -m *TTLvalue destination*
```

Do they provide any useful results?

Hey guys,
I'm so sorry for my late response. Being very busy working on thesis. :)

My ISP called my up a couple days back to 'trace-route' my complained network path to "gmail.com". The engineer *somewhat* agreed that the problem could possibly be from their equipment. I suspected this because I had my friend try his Ubuntu 9.10 on the same system and also couldn't reach (see the content of) his Yahoo Mail, only subjects. And as for GMail, same result, it wouldn't even sign in.

One thing I'm battling in my mind is why the "ICMP	Time-to-live exceeded (Fragment reassembly time exceeded)" that I once saw on my Window Vista still allowed GMail, YahooMail and Facebook to work seamlessly but totally stalls it on Linux.

Like I mentioned, trying various LiveCDs suggested that it is primarily from the ISP side (whom I suspect could be FILTERING OFF Linux fingerprinted packets). How naive!! 

Funny enough, I've been very scared to tell my ISP I even us Linux, so as not to get the engineers confused. I recall an occasion earlier in this troubleshooting, the engineer asked me to ping and IP by "Pressing Start -> Run; type ping xx.xxx.xx.xxx", and I told him I have Linux system and would do that from my terminal. He just mumbled that I should grab a Win system than follow the command. How naive. PING is ping on whichever system. Imagine, I even used my Linux on this ISP without hustles for about 11months before relocating to a new site [which I suspect caused the issue (BASE STATION RELATED)]

It's great to be MS certified, but not a crime to be open to non-MS working platforms.


Thanks guys. I'll keep you updated if anything comes up. Right now, this frustration is making me a big fool waiting for a new ISP that only attends to your plea for subscription 3~4wks after application.--I guess they are way too rich to need me!

Crazy X world!

---

### Post by FirstByté on 2010-05-14
> **jatanr said:**
> Good Idea FirstByté. I will give it a try and let you know if things work.

Any updates from this attempt?

---

### Post by jatanr on 2010-05-15
> **FirstByté said:**
> Any updates from this attempt?

Sorry I haven't had a chance to do that. Been very busy at work and coming home late at night. Will update once I try it out.

This issue with Gmail and Yahoo Mail still exists.

Oh btw... I am not able to post this message either. I can write the message but when I click on "Submit Reply", it keeps thinking without any activity. I am posting this using my winxp laptop :(

---

### Post by dobbod on 2010-05-17
Problem solved !!

I can now check my emails on Gmail and YahooMail, and I can also logged in into Facebook. Just before all this things happened, I read somewhere, that someone suggested to disable all Firefox's addons installed, and then test to enable one by one those addons back. I really did it. I finished tested all those addons, all enabled as earlier, and the best thing is I can still check my emails. Emm... don't know what happened.

To confirm everything is okay, I restarted my PC, and still I can logged in happily to those 3 websites. :)

---

### Post by FirstByté on 2010-05-21
> **jatanr said:**
> Sorry I haven't had a chance to do that. Been very busy at work and coming home late at night. Will update once I try it out.

This issue with Gmail and Yahoo Mail still exists.

Oh btw... I am not able to post this message either. I can write the message but when I click on "Submit Reply", it keeps thinking without any activity. I am posting this using my winxp laptop :(
Sorry the issue still persist.

> **dobbod said:**
> Problem solved !!

I can now check my emails on Gmail and YahooMail, and I can also logged in into Facebook. Just before all this things happened, I read somewhere, that someone suggested to disable all Firefox's addons installed, and then test to enable one by one those addons back. I really did it. I finished tested all those addons, all enabled as earlier, and the best thing is I can still check my emails. Emm... don't know what happened.

To confirm everything is okay, I restarted my PC, and still I can logged in happily to those 3 websites. :)

Wonderful that you got this [*ISP*] error fixed. 

Reading your post made me rush to my old [wimax] broadband modem, then I disabled all Firefox extensions and plugin, but none still solved the issue. Too bad.
I already got another ISP [a dial-up] which apparently took just 28days to install (Crazy service providers!!). And I'm forced yet another 12months contract! :mad: :evil: [-( what a life!

The solution for me was A NEW ISP! 


Thanks guys. for the support. 

Conclusion, don't opt for ISPs that are platform specific; rather those that are OPEN minded to change and FREEDOM. I hate contracts too :)

---

### Post by jatanr on 2010-05-21
Ah... good for you that your problem is solved. Unfortunately, I cannot switch ISPs. I wish there was some other way. I tried to disable all the add-ons but still no luck.

---

### Post by Detonate on 2010-05-21
I use Thunderbird to access all of my email accounts.  This includes two gmail accounts and a yahoo account, a gmx account, and the account for my own domain.  Works great.  Setup for gmail and yahoo is automatic.

---

### Post by FirstByté on 2010-05-23
> **Detonate said:**
> I use Thunderbird to access all of my email accounts.  This includes two gmail accounts and a yahoo account, a gmx account, and the account for my own domain.  Works great.  Setup for gmail and yahoo is automatic.

Good to know you use ThunderBird. During the time of my destress, I once tried installing it since I had issues sending mails from Zimbra, but the new version of ThunderMail seems to get me confused whenever I'm setting up the GMail account so I let go of it.

I'll probably give it another shot someday soon. :razz:

---

### Post by cuf99 on 2010-06-04
So I had problems accessing yahoo, gmail, qwibber -- pretty much anything that required a log in gave me problems.  Disabling ufw made everything accessible again, but I'd like to have some kind of firewall in place.  I tried putting in various rules to allow http, https, imap -- a whole bunch of stuff -- but so long as ufw was enabled I could not access all those sites.  Anyone have any tips?

---

### Post by anagri on 2010-06-05
Please add me too in the problem list. 

I am from Bangalore and have Airtel as ISP. Jatanr which ISP do you use ?

I am getting similar problem accessing GMail and login to Twitter.

In the meantime, which email client are you using ? I have tried evolution but not having threaded conversation is really hurting.

Hope to have a quick resolution for this issue, can this issue be escalated to Ubuntu guys so that they can have a detail look and start working on a patch if necessary.

-Regards,
 Amiruddin Nagri

---

### Post by anagri on 2010-06-07
OK, so for past two days I didn't had anything to do but to make my GMail working.

I have zeroed down the problem to my wireless router. If I connect directly from modem, it loads up GMail and other things, but when I try to load up using wireless connection, it has the problem.

And it is not only for ubuntu but for all operating systems. My windows machine also shows same loading page error if I connect it using wireless. haven't tried connecting directly.


my wireless router is age old D-Link DI 524. The problem is happening on a security enabled device as well as unsecured device. Is there any setting that I am missing in the router ?

---

### Post by anagri on 2010-06-07
Yippy !!! I got it solved.

The issue was I am using really old routes DI-524, the MTL setting in the wireless router and the modem where mismatch, wireless router was having a larger value (I reset the router once, the factory setting was 1500) where as my beetel modem it was 1460.

Once they were fixed the issue got resolved. Thanks to Airtel for agressive and dedicated support here in India :).

Regards,

Amiruddin Nagri

---

### Post by dobbod on 2010-06-12
> **dobbod said:**
> Problem solved !!

I can now check my emails on Gmail and YahooMail, and I can also logged in into Facebook. Just before all this things happened, I read somewhere, that someone suggested to disable all Firefox's addons installed, and then test to enable one by one those addons back. I really did it. I finished tested all those addons, all enabled as earlier, and the best thing is I can still check my emails. Emm... don't know what happened.

To confirm everything is okay, I restarted my PC, and still I can logged in happily to those 3 websites. :)
I celebrated too early, I can't access those mail clients a few days after that. Recently, this problem really solved. After a few discussions (through calls and emails) my ISP ([P1]("http://p1.com.my/")), asked me to change the MTU number in the modem setting (configuration). Since then, it's confirmed that this problem really solved. Yeehaa !! :lolflag:

---

### Post by FirstByté on 2010-06-12
> **dobbod said:**
> I celebrated too early, I can't access those mail clients a few days after that. Recently, this problem really solved. After a few discussions (through calls and emails) my ISP ([P1]("http://p1.com.my/")), asked me to change the MTU number in the modem setting (configuration). Since then, it's confirmed that this problem really solved. Yeehaa !! :lolflag:

Thanks so much for the info. I knew it's got something to do with the quipment side.. But didn't just know where.

Too bad I switched to another [ISP]("http://www.tm.com.my/") contract......... Arggghhhhhhhh:mad::mad:

Glad it was solved though.

---

### Post by mister_p_1998 on 2010-06-15
I occasionally get this on Firefox & Yahoo mail & groups, try logging in with Konqueror or Opera, that works for me, (shame cos I love Firefox) it hasnt done it for a few months though.

---

### Post by jatanr on 2010-07-05
> **anagri said:**
> Yippy !!! I got it solved.

The issue was I am using really old routes DI-524, the MTL setting in the wireless router and the modem where mismatch, wireless router was having a larger value (I reset the router once, the factory setting was 1500) where as my beetel modem it was 1460.

Once they were fixed the issue got resolved. Thanks to Airtel for agressive and dedicated support here in India :).

Regards,

Amiruddin Nagri

Hi,

Sorry for replying so late. Good to know that your issue was resolved. I will try to see if I have the same issue. 

My ISP is BSNL.

Thanks for the tip. I will check it out.

Curiously, gmail and yahoo work in chrome when I am connected to my office vpn. They do not work when there is no vpn connection.

---

### Post by Hannakc on 2010-07-26
Congrats with solving the problem. I have the same problem in lucid (toshiba laptop) wireless connection
*no gmail, facebook message and my school mail (squirrelmail) + most stuff involving sending formulae (like this forum)
*both firefox and chromium
*transmission has normal speed

but the strange thing is that my Acer Aspire netbook, UNR 10.04 does all of these things fine (firefox) on the same network which makes me doubt that my ISP has a problem...

I tried the fixes i have found (ipv6 disable (firefox and grub), disable apps, set openDNS, more ...) and I am getting desperate...calling the ISP next.
/HANNE

---

### Post by razzbar on 2010-07-27
> **FirstByté said:**
> Permit me all to apologize to Ubuntu for raising false flag. I guess it has a problem to do with my ISP and dynamic sites. To fix this, I'm changing my ISP in 2week's time. 

I took my system to another friend's network running 15Mbps and it loaded smoothly and perfectly. On my network, it resets on every attempt.

**Thanks to all who contributed to my case. You guys are wonderful.**
:P

I'll be marking this '**SOLVED**'!

**:(Not solved.:(** Yes, it **is** an ISP related issue, but as has been pointed out by others, MS Windows works fine on connections were Ubuntu has "ISP" issues. 

Again, *some* ISPs present no problem for Ubuntu. At locations where Ubuntu has problems, Windows works OK. The behavior is identical regardless of browser (I've tried Firefox, Chromium and Opera).

We can't just go changing ISP just to get Ubuntu working, when Windows works fine with the ISP.

---

### Post by razzbar on 2010-07-30
I am having the exact same problem with Lucid. Some locations are OK, others are not. Same with any browser. Windows always works. 

[COLOR=Red]**This is serious impediment to getting real USE out of Ubuntu.  **[/COLOR]

---

### Post by razzbar on 2010-07-30
> **FirstByté said:**
> Just to add, is your system portable [like laptops etc]? If so, why not try trying it on a different network and see if this situation persist as well.

Yes, it's different at different locations. Some ISPs apparently don't like Ubuntu. E.g. Clearwire. I have no problems with  ATT and Qwest.

---

### Post by jax_cze on 2010-08-16
I have the same problem. I can not log in Gmail in Ubuntu (9.10, 10.04, virtualized WinXP) and web browsers (instead of lynx - there Gmail works) but in WinXP and Win7 it works.

---

### Post by dineshs on 2010-08-18
If the modem is in bridge mode you can change it to PPPoE mode and try if that works

---

### Post by jax_cze on 2010-08-31
Problem solved. I set MTU to 1000 and it works.

---

### Post by UbuPhysicist on 2010-09-02
So Sorry if I have jumped in a bit late on this thread but it seems to be the correct forum for my question.  I am having problems connecting to gmail through my clearwire network on Ubuntu 9.1.  I noticed that some of the reply's a while back suggested changing the MTU number on my router/modem.  Can someone explain how to do this and if this is the correct solution??  Thanks for everyone help and understanding.

---

