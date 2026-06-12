---
title: "The slowest computer in Britain :-("
date: 2009-05-14
forum: General Help
---

### Post by AmpersUK on 2009-05-14
[SIZE=3]**I have a major problem**[/SIZE]
 [SIZE=3]
[/SIZE] 
 [SIZE=3]I have asked everywhere until I am blue in the face. I am pretty sure it isn't really a Ubuntu problem as it has been with me since 8.04, through 8.10 to **9.04** but I am so desparate I thought I'd try here just on the off-chance that someone else has had the same problem[/SIZE]
 [SIZE=3]
[/SIZE] 
 [SIZE=3][COLOR=Blue]**EQUIPMENT**[/COLOR][/SIZE]
 [SIZE=3]A desktop ASUS PC with a third of the 1.5TB of hard disks used. Twin core fast Intel processor, 2GB memory, Ubuntu 9.04, Latest “Ubuntu serviced” Firefox. HP Network Printer C7280.[/SIZE]
 [SIZE=3]
[/SIZE] 
 [SIZE=3][COLOR=Blue]**PROBLEM**[/COLOR][/SIZE]
 [SIZE=3]When I access the Internet, it can take between a minute and three minutes to access just one new website, any website, and the same length of time to flip between pages. **But for an hour or so, sometimes a little longer, I get a lightning fast connection.**[/SIZE]
 [SIZE=3]
[/SIZE] 
 [SIZE=3][COLOR=Blue]**WHAT I HAVE DONE TO TRY TO REMEDY THE SITUATION**[/COLOR][/SIZE]
 
[LIST]
[*][SIZE=3]I have approached     BT, my ISP. I have a business connection so they put effort into it     but cannot find anything wrong.      [/SIZE]
[*][SIZE=3]I have changed my     aging Netgear DG834G for a new Netgear DG834N.      [/SIZE]
[*][SIZE=3]I have changed the     little dongle for the telephone that has to be put on when you use     broadband.[/SIZE]
[*][SIZE=3]I have changed all     the ethernet cables from the Router, including the one to my HP     network printer.[/SIZE]
[*][SIZE=3]I have put my fist     through three monitors and smashed five keyboards.[/SIZE]
[/LIST]
 [SIZE=3]
[/SIZE] 
 [SIZE=3]OK, I might not have carried out the last action but you get the general idea of my angst![/SIZE]
 [SIZE=3]
[/SIZE] 
 [SIZE=3]But I **am** going yellow with all the coffee I am drinking as when I click on a webpage link I often go and make a coffee to avoid my frustration – and this is a fact![/SIZE]
 [SIZE=3]
[/SIZE] 
 [SIZE=3]Has anyone got any ideas at all? The only solution I can think of is to move house to another area - preferably New Zealand -  and buy all new equipment. I am sure many of you will realise that this is not a viable option.[/SIZE]
 [SIZE=3]
[/SIZE] 
 [SIZE=3]However, a skilful Linux engineer might point me towards Parliament and supply me with an AK47![/SIZE]
 [SIZE=3]
[/SIZE] 
 [SIZE=3]Seriously, please help.[/SIZE]
 [SIZE=3]
[/SIZE] 
 [SIZE=3]Ampers[/SIZE]

---

### Post by skymera on 2009-05-14
I used to have slow internet when IPV6 was enabled.
This isn't a problem anymore in 9.04

Change your DNS to OpenDNS (Makes my internet browsingmuch faster)
Google for Ubuntu broadband tweaks, i done it for you :D
[http://ubuntuforums.org/showthread.php?t=251509](http://ubuntuforums.org/showthread.php?t=251509)
Also change Firefox settings to allow pipelining and disable IPv6. ( A Google with reveal all)

---

### Post by matthewbpt on 2009-05-14
Like the user above suggested, try to disable ipv6, which is supposed to only be enabled only if there is a ipv6 router present but sometimes incorrectly enables it anyway. Googling I found this link on disabling it [http://www.ubuntu-inside.me/2009/04/howto-disable-ipv6-at-ubuntu-jaunty.html](http://www.ubuntu-inside.me/2009/04/howto-disable-ipv6-at-ubuntu-jaunty.html) also try googling to disable ipv6 in firefox. Is this a problem just with firefox or with any program that accesses the internet, for example is the update manager very slow when downloading updates. Try using the command line to wget a file and see if that is slow too (type 'wget url.to.file.you.want.to.download').

---

### Post by coffeecat on 2009-05-14
I'd agree with the others that you need to exclude IPv6 as the issue although in 2009 and with a brand new modem-router (of a good make) I'd be surprised if that is the problem.

You don't say what, if any, other operating system you might be using and whether you get a decent internet experience with it. That would help to narrow the field down a bit. Do you use Windows or MacOS, and if Windows, which version? And, if so, do you get this problem?

> **AmpersUK said:**
> 
[LIST]
[*][SIZE=3]I have changed the     little dongle for the telephone that has to be put on when you use     broadband.[/SIZE]
[/LIST]


You also need a filter on each and every telephone point that has a piece of equipment attached, whether broadband or just a phone receiver. And you need to make sure it's a decent quality one. The one that came with the Netgear will be OK, but cheap ones are not worth using.

Last thought. It sounds as though you are confident that BT has taken you seriously, but not everyone is happy with their customer support. If you do decide to try another ISP, I happened to notice [this on the thinkbroadband website recently]("http://www.thinkbroadband.com/news/3914-aaisp-promises-to-fix-your-faulty-broadband-line.html"). I don't use AAISP myself and have no connection with them, but I do know they have a very good reputation. Moreover, [since their server runs on Linux]("http://toolbar.netcraft.com/site_report?url=http%3A%2F%2Faaisp.net.uk%2F"), they might be more geared up to your problem.

**Edit:** I've just noticed that [BT's server runs on Linux too.](http://toolbar.netcraft.com/site_report?url=http%3A%2F%2Fwww.bt.com%2F) Ho hum. :p

---

### Post by Bartender on 2009-05-14
It'd be funny if it weren't so annoying - I imagine most of the ISP's use Linux servers.  But if the customer at the far end of the line is using Linux they shrug and tell you you're on your own.

---

### Post by s.fox on 2009-05-14
> **Bartender said:**
> It'd be funny if it weren't so annoying - I imagine most of the ISP's use Linux servers.  But if the customer at the far end of the line is using Linux they shrug and tell you you're on your own.

That is sort of the same line when I was having difficulties setting up a router.  In the end I ended up purchasing a different model from another company.

---

### Post by AmpersUK on 2009-05-14
Skymera
Thanks for that, I went to the link you gave and completed the task. I then googled and turned the false into true with Firefox.

Won't know until tomorrow howthis sorts things, although the immediate effect is a slight improvement. In both cases I rebooted immediately after the fix to be on the safe side.

matthewbpt
No problems with Evolution, apart from the fact that it isn't perfect anyway. And Update manager, and downloading programs from Synaptic give no problems at any time.

coffeecat
1. I have a shotgun on the wall by the computer. This is in case a visitor comes in with anything "Windoze" on him :-) Same goes for the Mac, so if you have an iPhone or iPod, don't tell me :-) I hate people who sell you things at top prices and then try to lock you in. I'd buy Microsoft and Apple products happily if they were more open.

2. Would not having a filter for the other two telephone sockets really make any difference to the broadband which has one? I never bothered with the phones as they work perfectly without one.

3. Have to have BT Business. My wife does the books for a management consultancy and they choose and pay for the equipment. Her Windows machine <spit> is on the same router and has no speed problems - plenty of windows problems though :-) Her company won't let me install Linux on it as they use Outlook thoroughly for all outworkers logging on to their VPN network for bringing everyones diary up to date automatically. Not only don't I ever touch it, I don't even look at it :-)

I am a true convert

---

### Post by danwood76 on 2009-05-14
@ Ampers
I'm not going to slate BT, much, but they quite often shrug their shoulders and say its your fault when it isnt. (had this happen recently at the place where I work, oddly being our fault the internet was full speed again in 3 days without us doing anything ;))

How far is you business from the local telephone exchange?
Is it this slow in other OS's / PCs?
What speed does the router connect at? (normally available from the routers main page, displayed as xxxkbps)

---

### Post by coffeecat on 2009-05-14
> **Bartender said:**
> It'd be funny if it weren't so annoying - I imagine most of the ISP's use Linux servers.

I'm sure you're right, except that I managed to choose an ISP that uses Windows servers - which is not funny at all. :oops:

---

### Post by coffeecat on 2009-05-14
> **AmpersUK said:**
> coffeecat
1. I have a shotgun on the wall by the computer. This is in case a visitor comes in with anything "Windoze" on him :-) Same goes for the Mac, so if you have an iPhone or iPod, don't tell me :-) I hate people who sell you things at top prices and then try to lock you in. I'd buy Microsoft and Apple products happily if they were more open.

I wouldn't dream of walking into your house with an iPhone or an iPod. In fact I wouldn't dream of walking **anywhere** with either of them. £20-worth of Nokia does me fine. :p

> **AmpersUK said:**
> 2. Would not having a filter for the other two telephone sockets really make any difference to the broadband which has one? I never bothered with the phones as they work perfectly without one.

You're probably right. Having filters for the phones is more to stop the whistling you sometimes get when the BB hasn't been filtered out, but if you have spare filters it's worth plugging them in.

> **AmpersUK said:**
> 3. Have to have BT Business. My wife does the books for a management consultancy and they choose and pay for the equipment. Her Windows machine <spit> is on the same router and has no speed problems - plenty of windows problems though :-) Her company won't let me install Linux on it as they use Outlook thoroughly for all outworkers logging on to their VPN network for bringing everyones diary up to date automatically. Not only don't I ever touch it, I don't even look at it :-)

Well, that tells us something - Windows on the same network and through the same router has no problems, so it's either a problem with Ubuntu and/or your computer. I know you can't install Linux on your wife's machine, but what's to stop you trying an Ubuntu live CD on it (when she's out! :p )? If you get good internet speeds, you'll have narrowed the problem down to your machine, although I cannot think what the problem might be.

Having said that, it still has a smell of DNS resolution about it. Try an earlier poster's suggestion of openDNS, or try this:

In Ubuntu Network Manager (Edit Connections) under IPv4, change from DHCP to Manual. You'll have to choose an internal IP address and put in your gateway address and netmask. Also your DNS server address. You could try both the BT one and the openDNS.

I have no idea whether this will help, but it's worth trying.

---

### Post by AmpersUK on 2009-05-14
Just about to try the live CD

Tried it, and everything is lightening fast on her Windows XP Professional machine. I washed my hands afterwards ;-)

So it doesn't seem like the Router, BT's Internet, or the fact that I don't have the filter on the other two telephone sockets.

Ampers

---

### Post by coffeecat on 2009-05-14
Let me get this right. With the Ubuntu live CD on your wife's Windows machine, internet was fine? Which certainly does narrow it down, although it's still a mystery. :-k

But there's one thing I want to pick up in your first post...

> When I access the Internet, it can take between a minute and three minutes to access just one new website, any website, and the same length of time to flip between pages. **But for an hour or so, sometimes a little longer, I get a lightning fast connection.**... which is interesting. Sometimes you get good internet connection, lasting an hour or more. One question:

I notice that both your routers are wireless, but you mention ethernet cables. Are any of your machines connected wirelessly by any chance? If only yours was connected wirelessly, that might be the cause. Perhaps intermittent interference on the wireless channel you're using.

---

### Post by Bakerconspiracy on 2009-05-14
Doesn't this sound like a driver problem to anyone else?....

---

### Post by Kevbert on 2009-05-14
I'm using a Netgear DG834G both via wireless and ethernet with no problems. Have you tried changing your ADSL filter for another one ? How many devices have you got connected to the BT line (I believe the maximum number of devices is 3 as standard REN=3) including phone extensions, satellite TV etc ?  I'm at the end of an exchange (just outside London) and for years BT suggested I could not get broadband. Finally got 512kbps and then switched to Sky so that I could get up to 2Mbps, I then got a letter from BT saying that soon I could get up to 2Mbps !!!
The other thing you may want to try is when you get a slow connection, turn off the router for a minute and then turn it back on as it may be a dodgy switch in the telephone exchange.

---

### Post by bacardiandwatermelon on 2009-05-14
What happens when you try to boot from the live cd on your own machine. Still slow?

---

### Post by zika on 2009-05-14
would You please give us the output of **ifconfig** from Your Terminal window.

---

### Post by ugm6hr on 2009-05-14
> **bacardiandwatermelon said:**
> What happens when you try to boot from the live cd on your own machine. Still slow?

This sounds like a sensible diagnostic step.  It will at least differentiate between hardware and software issues.

---

### Post by jimv on 2009-05-14
I'm going to bet this is a Firefox issue...probably profile related.  rename your .mozilla folder to .mozilla.old and try Firefox again.  Here's a terminal command to do that:

mv ~/.mozilla ~/.mozilla.old

---

### Post by AmpersUK on 2009-06-04
[SIZE=4]**Update**[/SIZE]

I loaded Virtualbox on my computer and the WindowsXP and then Windows Firefox and that runs fast.

Since then (yesterday) I seem to be getting a fast speed on Linux as well.

Please don't reply, lets leave it for a few more days and I will report back.

It might be OK now, only time will tell.

If it slows down again, I will load all the same add-ons in Windows Firefox as I use in Linux Firefox. As a nagging feeling tells me there may be a confliction somewhere in that quarter.

Ampers.

---

### Post by dgoosens on 2009-06-05
sorry AmpersUK...

I decided I'd reply anyway... hope you won't mind...
maybe you could try with another web browser ??

Opera might be an idea:
[http://www.opera.com/download/?platform=Linux]("http://www.opera.com/download/?platform=Linux")

let us know !

---

### Post by AmpersUK on 2009-06-14
> **dgoosens said:**
> sorry AmpersUK...

I decided I'd reply anyway... hope you won't mind...
maybe you could try with another web browser ??

Opera might be an idea:
[http://www.opera.com/download/?platform=Linux]("http://www.opera.com/download/?platform=Linux")

let us know !

I have logged onto Opera for three days now, and have not had any problems. Other than Opera crashed once.

Considering I have reloaded Ubuntu a few times and have had the prolem consistantly, it is very strange and I can only think something must be conflicting with a hardware driver.

The problem is not solved as such, but Opera gives me a fast access.

Ampers

---

