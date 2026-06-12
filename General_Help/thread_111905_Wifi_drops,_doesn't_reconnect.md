---
title: "Wifi drops, doesn't reconnect"
date: 2006-01-03
forum: General Help
---

### Post by kamagurka on 2006-01-03
When I first boot, I can connect to any wnet just fine (using wifi-radar), but after about 3 min. the connection drops and when I try to reconnect, wifi-radar just keeps telling me "connecting" for hours, if I let it. I only get another precious nugget of connectivity if I reboot. Now, before I **** around with the kernel and drivers (if you have any ideas in that area, go ahead and let me know anyway, eh?), I'd like to try an alternative to wifi-radar, preferrably a nice little text-based daemon. Thanks for your help.

---

### Post by sciurus on 2006-01-04
Look at the documentation for *iwconfig*.

---

### Post by Tal on 2006-01-04
what does ifconfig show?

And, when you do a 'iwlist <dev name> scanning' what do you get?
<dev name> = wlan0 or whatever your device is.

---

### Post by kamagurka on 2006-01-05
[QUOTE=sciurus]Look at the documentation for *iwconfig*.[/QUOTE]
Take your rtfm and shove it.

---

### Post by sciurus on 2006-01-06
[QUOTE=kamagurka]Take your rtfm and shove it.[/QUOTE]

It was just friendly advice. You asked for "an alternative to wifi-radar." You even specified "text-based." I've never gotten wifi-radar working myself. However, if you know the details of your own network (which I assume you do, I don't since you didn't post them) it's easy to read the iwconfig manpage, learn how to pass them to the command, and connect. If you have trouble, post again.

---

### Post by kamagurka on 2006-01-09
[QUOTE=sciurus]It was just friendly advice. You asked for "an alternative to wifi-radar." You even specified "text-based." I've never gotten wifi-radar working myself. However, if you know the details of your own network (which I assume you do, I don't since you didn't post them) it's easy to read the iwconfig manpage, learn how to pass them to the command, and connect. If you have trouble, post again.[/QUOTE]
No, you see, it wasn't "friendly advice". It wasn't even advice. An alternative to wifi-radar would be something that simplifies wlan config, especially with support for multiple wlans (since my lappy is, you know, mobile). Suggesting that I go read the fucking mess that is the manpage to the fucking mess that is iwconfig looks like little more than a poorly conceiled, very debianesque "**** you".
Sorry if I'm getting into a bit of a lather here, but I've gotten frustrated with iwconfig multiple times ("man iwconfig" - "iwconfig [interface] iwconfig interface [essid X] [nwid N] [mode M] [freq F] [channel C][sens S ][ap A ][nick NN ] [rate R] [rts RT] [frag FT] [txpower T] [enc E] [key K] [power P] [retry R] [commit] iwconfig --help iwconfig --version" "Yes, but how do I just scan, and then connect *cry*"). I dunno, maybe I'm just too dumb. Maybe getting wifi to run really *should* be harder than setting up OpenLDAP.
Bah, now this thread is *useless*. Useless, I tell you.

---

### Post by johna11en on 2006-01-09
Is this a new setup?

Did you recently switch from Windows or in a Windows dual boot?  Does it work in Windows?

Do you have any other computers that are on the wireless network and are they  experiencing the same problem?

Have you tried switching the channel it operates on?  Maybe it's a cordless phone or some other device interfering within the same spectrum.

---

### Post by funman on 2006-01-09
Hey, pretty much the same problem as me :???: 
I got told to ask my question in the networking forum (which I clearly see there is none of when I just went over the list...weird...) any way, I've never used anything such as iwconfig or anything at all...

I'm using a Netgear wireless PCI card, and it died, and if I try to plug in the ethernet cable I have for such times, it tells me ther eis no net, even connecting directly to the modem doesn't work. Also, mine dies completely, and I had to format the linux HDD to get back on and had internet for a whoel 30 minutes the last time. (I'm on the windows HDD now, and everything works perfectly as it always has on windows)

If anyone knows what I should do, please tell me...I can't stand windows :(

---

### Post by kamagurka on 2006-01-12
[QUOTE=johna11en]Is this a new setup?[/quote]
The lappy is new, the setup is not, works well enough with my other lappy...

[QUOTE=johna11en]Did you recently switch from Windows or in a Windows dual boot?  Does it work in Windows?[/quote]There's a windows install on that lappy (for work, damn them to hell), and everything works like a thing without flaws in there.

[QUOTE=johna11en]Do you have any other computers that are on the wireless network and are they  experiencing the same problem?[/quote]Yes, and no. Not even this computer is experiencing the problem, as long as I do it in windows.

[QUOTE=johna11en]Have you tried switching the channel it operates on?  Maybe it's a cordless phone or some other device interfering within the same spectrum.[/QUOTE]Nope, since I figure it must be fine, as everything works as long as I don't use it in linux. My guess is that either the driver isn't working right with my wlan card (Intel Centrino shit, damn them all to hell), or (this is what I hope) wifi-radar just ain't that great.

---

