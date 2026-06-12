---
title: "WIFI? How complicated is that?"
date: 2005-12-12
forum: General Help
---

### Post by TmP on 2005-12-12
Hi!

I'm trying to set up a direct or ad hoc wireless connection between my centrino laptop and my desktop. Is it possible at all in Ubuntu?

1. My USB dongle always seemed to be an odd one. It worked under win98 with a funny ad-on software. It caused me a lot of problems under other systems. And its poorly designed too. 
Here's its info form ifconfig:

wlan0     Link encap:Ethernet  HWaddr 00:0D:2F:00:89:D4
          inet addr:192.168.1.1  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20d:2fff:fe00:89d4/64 Scope:Link
          UP BROADCAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

I don't know if its working or just pretending to.
It seems to be recognised. It shows fine to me in the device manager, BUT
When I try to activate it, sometimes it freezes the keybord. LoL. A ps2 keybord. And than Ubuntu won't turn off until I take it out of the usb. Funny ain't it?

2. I don't get this network setup menu
How should I know the rules about WEP key? I mean, how many digits and stuff.. Its useless. Would it be so damn hard to make a netowrk configuration wizard? 

3. So I've got 2 Pc's. And neither is a router. I want to connect the WAN cards. 

Should I set up some ip address manually? Or is there some software which lets me set one of the card as an acces point? Or at least to listen for network request?

In win I'd set up a ad-hoc connection. But I won't. Cause win pisses me off.
And Linux upsets me. Should I go buy a Mac or something?

HELP!!!

oh yeah, and the Ubuntu Wiki is extremely helpfull:


> 
Ubuntu shows a connection quality, but I can't do anything in the network (ping, etc)

Most probably this means your encryption key is wrong. Again: there's no way to tell if it's right and this is very annoying. 


---

### Post by Chris Tucker on 2005-12-12
ad-hoc is possible in ubuntu to my knowledge.. i have not tried it yet, but it should not be hard.. someone with experience will probably help you out, i myself am amazed your not asking how to get the dongle working in the first place .. that was where i nearly lost some hair...

---

### Post by carlosqueso on 2005-12-12
[QUOTE=TmP]Hi!

I'm trying to set up a direct or ad hoc wireless connection between my centrino laptop and my desktop. Is it possible at all in Ubuntu?

1. My USB dongle always seemed to be an odd one. It worked under win98 with a funny ad-on software. It caused me a lot of problems under other systems. And its poorly designed too. 
Here's its info form ifconfig:

wlan0     Link encap:Ethernet  HWaddr 00:0D:2F:00:89:D4
          inet addr:192.168.1.1  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20d:2fff:fe00:89d4/64 Scope:Link
          UP BROADCAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

I don't know if its working or just pretending to.
It seems to be recognised. It shows fine to me in the device manager, BUT
When I try to activate it, sometimes it freezes the keybord. LoL. A ps2 keybord. And than Ubuntu won't turn off until I take it out of the usb. Funny ain't it?[/QUOTE]

It appears to be working if it shows up.  I had a network card which froze the keyboard too, it may be a driver issue, I dunno.

[QUOTE=TmP]2. I don't get this network setup menu
How should I know the rules about WEP key? I mean, how many digits and stuff.. Its useless. Would it be so damn hard to make a netowrk configuration wizard? [/QUOTE]

If you don't know about the WEP key, then you probably don't have one.  Whoever administers your wireless network sets them to whatever they want.  Since you're in charge, just leave it blank.

[QUOTE=TmP]3. So I've got 2 Pc's. And neither is a router. I want to connect the WAN cards. 

Should I set up some ip address manually? Or is there some software which lets me set one of the card as an acces point? Or at least to listen for network request?[/QUOTE]

You should be able to set up an ad-hoc connection in the wireless setup window.  I think you just change "managed" to "ad-hoc" in that window.  I don't know what else you need to do, as I only own one computer and share a wireless router with my roommate.



[QUOTE=TmP]In win I'd set up a ad-hoc connection. But I won't. Cause win pisses me off.
And Linux upsets me. Should I go buy a Mac or something?

HELP!!!

oh yeah, and the Ubuntu Wiki is extremely helpfull:[/QUOTE]

Judging from the tone of this post, that may not be a bad idea.  If you use all mac hardware with your mac, it'll work flawlessly (and look better than any other OS IMO :-D), with very little work.   However, if you want a free and highly customizable OS, are willing to learn, and take a less sarcastic tone, then Ubuntu may be for you.  It really depends on the time and energy that you have to put in.

---

### Post by encompass on 2006-01-11
About setting your IP's I think you just need to make sure they don't have the same IP's... 192.168.1.1 and 192.168.1.2 try that... and it looks like it is getting an IP address too.. cause it shows one... what is the brand and model of your wireless?  Search the forums for that... it will help you alot more.

---

### Post by encompass on 2006-01-11
Bla Bla:razz:

---

