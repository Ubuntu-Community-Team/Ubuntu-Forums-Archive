---
title: "Shocker - Ubuntu problem unsolveable! (Please read)"
date: 2009-05-24
forum: General Help
---

### Post by DJB1609 on 2009-05-24
Before you write this off as a rant, know that I care and want to use Linux. Read on if you care.

Why is it that just the easy, obvious problems get solved?

Where are all the experts? Please bear with me, as I want you to know *I have* tried to solve this; including reinstalling and recently buying a new ADSL modem. I'm just pi**ing in the wind.

I have used Linux for over a year. I want to keep using it, but despite hundreds of reads of my posts, there are no answers or, more importantly, no hints or suggestions of things to try.

I am not a complete computer novice, and in fact I remember the old Amiga CLI.

[http://ubuntuforums.org/showthread.php?p=7335996](http://ubuntuforums.org/showthread.php?p=7335996)

[http://ubuntuforums.org/showthread.php?t=1154975](http://ubuntuforums.org/showthread.php?t=1154975)

[http://ubuntuforums.org/showthread.php?p=7129802](http://ubuntuforums.org/showthread.php?p=7129802)

Where are the "Post the log of this", run this "sniffer" and post the log, "Look at this".... posts I see for other problems?

I remember when people would doggedly try and fix a problem, especially when it looked like the person was trying. Look at the language in one of the links - I am not the only one with a similar problem, and frustrations.

As for logging a bug report - I see this problem unsolved and almost dismissed in other bug reports. It seems if it's isolated, then it's not valid. 

So, if I go back to XP, it's because Linux just doesn't work with *my* setup. OK. Fine I'll come back in a year, maybe.

DavidJ.

---

### Post by SkyNet2029 on 2009-05-24
David,
           Are you intentionally being vague? What exactly is the issue you feel is unsolvable. Your links point to even more vague posts (rants , really) and don't help to clarify the issue at hand. What is it which you are expecting to accomplish? What flavor of ubuntu are you running? What are your hardware specs?
Specifically:

```
#dmesg tail | more
```

should barf up last bit of errors encountered. Post that log here on forum.

See, if you don't state what the issue is, of course it becomes unsolvable..too many variables. Your post is like trying to divide by zero. It is possible, but one must know variables first.
~James

---

### Post by mcduck on 2009-05-24
Perhaps you should post all the information about your problems in the first place, and not wait until somebody comes and asks you to do it.. ;)

If you don't tell what's your exact problem people are less likely to bother helping you.

---

### Post by lisati on 2009-05-24
I concur with the previous two posters: a summary of the particular problem you're experiencing would be useful. Are you having trouble accessing the internet?

---

### Post by cariboo on 2009-05-24
I would also suggest you not post your problem in the middle of someone elses thread, create a new thread with an informative title. 

> 8.1 and 9.04 crippled on two laptops Please Help! [Given up on Linux - Unsolved]

does not tell anybody what your problem is except that you are threatening to go back to windows. In most cases making threats just makes the people that may be able to answer your question move on to the next one, as you aren't going to be here for long.

---

### Post by DJB1609 on 2009-05-24
> **SkyNet2029 said:**
> David,
           Are you intentionally being vague? 
~James

Thanks James, I am not trying to be vague. I have posted information without response, and my links were to show that I had searched and tried to resolve this myself. Often posters are shot down for not searching or trying, and I cannot be accused of not trying. Being ignorant of Linux and groping in the dark perhaps, but try I have. :neutral:

> **mcduck said:**
> Perhaps you should post all the information about your problems in the first place, and not wait until somebody comes and asks you to do it.. ;)

If you don't tell what's your exact problem people are less likely to bother helping you.

My second link was, I thought, quite informative. That was my post, and the idea of the headline was to show it wasn't a single hardware/OS problem, and perhaps worthy of a look.

> **cariboo907 said:**
> I would also suggest you not post your problem in the middle of someone elses thread, create a new thread with an informative title. 

In most cases making threats just makes the people that may be able to answer your question move on to the next one, as you aren't going to be here for long.

I thought it was informative. 

All of you, thank you for responding. I am not making "threats" and I don't want to come across as a windows fan. If this is how it is seen, then I apologise. 

I dislike windows for many reasons. I am impressed and have converted people (in the UK) to Linux before coming to China. I like open source, and intend to go fully and properly open source as soon as I can.

I am just at my wits end here, unable to do a simple thing like posting. I will post the output in the next message for clarity, and leave this post as a thank you for responding, and for any help to resolve this.

If I wasn't so passionate about Linux, I wouldn't have come back again, so please forgive me and bear with me. :)

David.

---

### Post by DJB1609 on 2009-05-24
Hardware:
Toshiba A200 1DN Laptop with 2GB RAM.
Asus eee1000H with 2GB RAM.
Asus W530G v2 Wireless "Pocket" router.
D-Link 500+ ADSL 2 modem to CNC Broadband (N.E.CHina) ppoE.
(I even bought a new modem to try and stay with Linux:( )

Software:
Vista on Toshiba, Firefox, Thunderbird, AVG Free.
   Dual boot with Ubuntu 9.04 Jaunty, *upgraded* from 8.1.
XP on Asus_eee, Firefox, Thunderbird, Avira Free.
   Dual boot with Ubuntu 9.04 Netbook Remix *clean install*.

Also tried Jaunty desktop and PCLinuxOS on the Asus_eee - exact same problems.

The problem that is consistent is simply:
I cannot post to any forums using .php
I get either a timeout, or a "Open or Save xxxx.php" dialogue box.

Weirdly, I was getting success with Opera, but that is only on a clean reboot, and even then not always. Firefox doesn't ever work.

I am *now* thinking I must try turning off ipv6 in Ubuntu. I am told it is off by default in Windows, and not in Ubuntu. I'm not sure about PCLinuxOS. 

It couldn't hurt, as all the hardware here is a year or so at least behind the west, and my "new" modem from the ISP was stamped 2006:shock:

After following some ideas here - [https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4](https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4)

I still get this:-

daje@daje-1000H:~$ ip a | grep inet6
    inet6 ::1/128 scope host 
    inet6 fe80::215:afff:fee5:4c9d/64 scope link 

Attached is the output of the dmesg command you suggested.

Opera gave this error last time I tried to post:
________________________________________________
Internal Server Error

The server encountered an internal error or misconfiguration and was unable to complete your request.

Please contact the server administrator, [no address given] and inform them of the time the error occurred, and anything you might have done that may have caused the error.

More information about this error may be available in the server error log.
Apache/2.2.8 (Ubuntu) Server at ubuntuforums.org Port 80
________________________________________________

Firefox gave this error:
________________________
From Upload attachment:

Network Timeout

The server at ubuntuforums.org is taking too long to respond.

        
The requested site did not respond to a connection request and the browser has stopped waiting for a reply.

    * Could the server be experiencing high demand or a temporary outage?  Try again later.
    * Are you unable to browse other sites? Check the computer's network connection.
    * Is your computer or network protected by a firewall or proxy?  Incorrect settings can interfere with Web browsing.
    * Still having trouble? Consult your network administrator or Internet provider for assistance.
____________________________________

I hope we can resolve this, and I do appreciate it is your free time and goodwill.So, thank you.

DavidJ.

---

### Post by neighborlee on 2009-05-24
> **DJB1609 said:**
> Thanks James, I am not trying to be vague. I have posted information without response, and my links were to show that I had searched and tried to resolve this myself. Often posters are shot down for not searching or trying, and I cannot be accused of not trying. Being ignorant of Linux and groping in the dark perhaps, but try I have. :neutral:



My second link was, I thought, quite informative. That was my post, and the idea of the headline was to show it wasn't a single hardware/OS problem, and perhaps worthy of a look.



I thought it was informative. 

All of you, thank you for responding. I am not making "threats" and I don't want to come across as a windows fan. If this is how it is seen, then I apologise. 

I dislike windows for many reasons. I am impressed and have converted people (in the UK) to Linux before coming to China. I like open source, and intend to go fully and properly open source as soon as I can.

I am just at my wits end here, unable to do a simple thing like posting. I will post the output in the next message for clarity, and leave this post as a thank you for responding, and for any help to resolve this.

If I wasn't so passionate about Linux, I wouldn't have come back again, so please forgive me and bear with me. :)

David.

There is absolutely nothing TO forgive.

If people dont want to help , they should not do so, and those wanting to should help, not asking for anything in return other than the comfort that they helped their fellow person achieve success.

Oh and btw, you do NOT sound like a windows fan, you just sound like someone asking for help that, so unless someone has changed the meaning of certain english words, then not to worry , its the other people overreacting, its not you at all. It's not a sin to show frustration, as throughout I thought you were reasonably calm and very nice about all of it.

I feel bad you were having trouble, and hope you have since resolved it.  It's a shame linux falls short in some areas, whereas with all of vista's faults < god knows there are tons of them>, it looms seductive sometimes by comparison and that comes from years and years of practice as well; though as you I remain firm as well that FOSS is the goal and its absoltely worthy ;)

cheers and good luck friend!
nl

---

### Post by alphacrucis2 on 2009-05-24
> **DJB1609 said:**
> Hardware:
Toshiba A200 1DN Laptop with 2GB RAM.
Asus eee1000H with 2GB RAM.
Asus W530G v2 Wireless pocket router.
D-Link 500+ ADSL 2 modem to CNC Broadband (N.E.CHina) ppoE.
(I even bought a new modem to try and stay with Linux:(

Software:
Vista on Toshiba, Firefox, Thunderbird, AVG Free.
   Dual boot with Ubuntu 9.04 Jaunty, *upgraded* from 8.1.
XP on Asus_eee, Firefox, Thunderbird, Avira Free.
   Dual boot with Ubuntu 9.04 Netbook Remix *clean install*.

Also tried Jaunty desktop and PCLinuxOS on the Asus_eee - exact same problems.

The problem that is conistent is simply:
I cannot post to any forums using .php
I get either a timeout, or a "Open or Save xxxx.php" dialogue box.

Weirdly, I was getting success with Opera, but that is only on a clean reboot, and even then not always. Firefox doesn't ever work.

I am *now* thinking I must try turning off ipv6 in Ubuntu. I am told it is off by default in Windows, and not in Ubuntu. I'm not sure about PCLinuxOS. 

It couldn't hurt, as all the hardware here is a year or so at least behind the west, and my "new" modem from the ISP was stamped 2006:shock:

After following some ideas here - [https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4](https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4)

I still get this:-

daje@daje-1000H:~$ ip a | grep inet6
    inet6 ::1/128 scope host 
    inet6 fe80::215:afff:fee5:4c9d/64 scope link 

Attached is the output of the dmesg command you suggested.

Opera gave this error last time I tried to post:
________________________________________________
Internal Server Error

The server encountered an internal error or misconfiguration and was unable to complete your request.

Please contact the server administrator, [no address given] and inform them of the time the error occurred, and anything you might have done that may have caused the error.

More information about this error may be available in the server error log.
Apache/2.2.8 (Ubuntu) Server at ubuntuforums.org Port 80
________________________________________________

Firefox gave this error:
________________________
From Upload attachment:

Network Timeout

The server at ubuntuforums.org is taking too long to respond.

        
The requested site did not respond to a connection request and the browser has stopped waiting for a reply.

    * Could the server be experiencing high demand or a temporary outage?  Try again later.
    * Are you unable to browse other sites? Check the computer's network connection.
    * Is your computer or network protected by a firewall or proxy?  Incorrect settings can interfere with Web browsing.
    * Still having trouble? Consult your network administrator or Internet provider for assistance.
____________________________________

I hope we can resolve this, and I do appreciate it is your free time and goodwill. so thank you.

DavidJ.

Very odd. Almost seems like your browser is sending something to the web server that it doesn't like. Perhaps your wireless driver is corrupting transmission. Of more importance than the wireless router and modem you have is the wireless hardware on your laptop (I'm assuming that you are using wireless?). Therefore what is the output of:


```
lspci
```

---

### Post by DJB1609 on 2009-05-24
> **alphacrucis2 said:**
>  (I'm assuming that you are using wireless?). Therefore what is the output of:
```
lspci
```

Yes, it is wireless for both machines.


daje@daje-1000H:~$ lspci

00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)

00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)

00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)

00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)

00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)

00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)

00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)

00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)

00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)

00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)

00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)

01:00.0 Network controller: RaLink RT2860

03:00.0 Ethernet controller: Attansic Technology Corp. L1e Gigabit Ethernet Adapter (rev b0)

daje@daje-1000H:~$ 
_________________________________-

The Toshiba is under control of my wife, watching a film as I speak, so will post that output if needed. Ubuntu found it's wireless on boot, just like this, and installed the driver without intervention from me.

I never thought of the drivers, as it is two machines. Remember, this started happening when I bought the Asus W530G - but I also moved to a new building as well. I have seen the routers/rack in a room when the engineer called. It handles the telephony as well, and possibly the cable TV. (All access boxes are together on the apartment wall, and all cables go to this room.)

However, this also happens ***wired*** from the Asus. (Haven't checked the Toshiba.)

Thanks for the input.

David.

ps. Thanks for the comments Neighborlee. Yes, I am frustrated that, unlike earlier, Linux has stopped working. It's not distro specific either, as PCLinuxOS had the same problem. I returned to Ubuntu as everything else just worked and PCLinuxOS needed tweaking to be useable. No matter how much I like Linux and want to use it, if it doesn't work I *must* go to the system that works. I also hate the idea of giving up ;)
pps. A three-minute to useable XP desktop is not funny - including 20secs for FF to load.

[Edit - I should say I have to boot into Ubuntu, then back into XP. This time, Opera timed out and FF offered to "Open or Save newreply.php".]

---

### Post by ddrichardson on 2009-05-24
Something you mentioned in one of your previous [posts]("http://ubuntuforums.org/showpost.php?p=7326100&postcount=47") - are you in China?

---

### Post by noelvh on 2009-05-24
Simple question for you, did you take the router out of the equation I mean did you do a direct connect to the modem? DSL suck and it gest worse when you put a router in the mix.

Noel

---

### Post by DJB1609 on 2009-05-24
> **ddrichardson said:**
> Something you mentioned in one of your previous [posts]("http://ubuntuforums.org/showpost.php?p=7326100&postcount=47") - are you in China?

Yes I am. I have it on good authority from the PCLinuxOS forum that it's not a Linux issue as it is in widespread use here, and particularly by a senior member of that forum living north of me. If you have any ideas or info, let me know.


> **noelvh said:**
> Simple question for you, did you take the router out of the equation I mean did you do a direct connect to the modem? DSL suck and it gest worse when you put a router in the mix.

Noel

Yes. The first thing I did was go DSL-wired with the wireless out of the equation. 

The DSL modem is in default mode, and the ppoE settings are set in the Asus wireless. The DSL settings are in Chinese, and D-Link were unhelpful in pointing me to English firmware, unlike Asus who were very hepful.

David.

---

### Post by oldtincup on 2009-05-29
DJB1609

Have you tried comparing packets between a working and non-working connection?  Wireshark should aid in this task and is available for both windows and linux.  I am certainly not an expert on this; but, I think this should give a direction to look.

---

### Post by meeples on 2009-05-29
i used to have this problem in 8.10. sometimes when i click a .php link it would try to save it and others it would show it. dunno bout the internal server bit though.

but ye a my problem seemed to just go away, i never noticed when and i have doe a few clean installs of jaunty...

---

### Post by DJB1609 on 2009-05-29
> **oldtincup said:**
> DJB1609

Have you tried comparing packets between a working and non-working connection?  Wireshark should aid in this task and is available for both windows and linux.  I am certainly not an expert on this; but, I think this should give a direction to look.

Thanks - that's what I was looking for - tools to try and narrow it down.

[http://www.wireshark.org/](http://www.wireshark.org/)

I will try this weekend - if I can understand it all!

Thanks,

DavidJ.

---

### Post by DJB1609 on 2009-05-29
> **DJB1609 said:**
> Thanks - that's what I was looking for - tools to try and narrow it down.

[http://www.wireshark.org/](http://www.wireshark.org/)

I will try this weekend - if I can understand it all!

Thanks,

DavidJ.

OK. Wireshark doesn't capture anything in XP.

I have logs for Linux - four in total - and it captured the successful posts in Opera, but not in FF.

Is anyone an expert in looking at the logs? Their did seem to be red entries when trying Firefox.

I'm a bit hesitant to just post them, as they contain hackable IP and MAC addresses...

DavidJ.

---

### Post by TransitMan on 2009-05-30
After reading this thread, and digesting it, I am going to give my $0.02 worth.

You have stated you were previously in the UK and had no problem using the internet to make posts. Then you went to China, which is where you are now. 
Given that the Chinese are very very strict when it comes to what they allow online, is it not possible that you are being blocked in some way by the Great Firewall of China, whereby some web-sites are totally unreachable?
Is it also possible that due to the internet restrictions in China that certain web sites with a .php in the address is being blocked, thereby giving you the timeouts and unreachable destinations in either of the browsers?

Have you tried a traceroute from your location to the internet site you want to go to, just to see if it drops along the way, or is blocked at the border?

Lastly, I am going to surmise that I do not think Ubuntu or PCLinuxOS is the culprit, but the internet of China and how they operate there.
If you can check your setting in the Network Manager, the DSL modem (if possible) you might find that your DNS resolves to a server in China. And I do not know of a way around it except to make the suggestion of OpenDNS to help you out.

Either way it goes, good luck.

---

### Post by DJB1609 on 2009-05-30
> **TransitMan said:**
> After reading this thread, and digesting it, I am going to give my $0.02 worth.

You have stated you were previously in the UK and had no problem using the internet to make posts. Then you went to China, which is where you are now. 

<snip> except to make the suggestion of OpenDNS to help you out.

Either way it goes, good luck.

Thanks for the response.

I was all ok in China on Linux; sorry for the confusion. I moved buildings, which means a new supplier/servers in the building.

I am on OpenDNS, and no change.

I think it's a router/DSL conflict that Linux is rejecting, but XP/Vista tolerate.

DavidJ.

---

### Post by binary10 on 2009-05-30
> **DJB1609 said:**
> Thanks for the response.

I was all ok in China on Linux; sorry for the confusion. I moved buildings, which means a new supplier/servers in the building.

I am on OpenDNS, and no change.

I think it's a router/DSL conflict that Linux is rejecting, but XP/Vista tolerate.

DavidJ.

Could be there's a DSL conflict in the new building. Which as you say has some toleration to XP / Vista. 

Maybe some insanely small negotiated MTU values or badly set values something like that are getting set between the router and the dsl modem. 

More recently our service had to have a upgraded dsl equipment because the bonder had an upgraded service at their end. Getting the service ppl to agree that there was a problem was bad enough in the UK, so it may require all the tea in China to get it sorted.

Sorry if you mentioned this back somewhere in your posts.. have you tried running local web connections internally to the building ? Do you have enough PCs to do something like that?

---

