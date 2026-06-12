---
title: "Wireless problems - dissapearing connection on Vostro 1500"
date: 2007-12-13
forum: Dell  Ubuntu Support
---

### Post by mushroomcloudwarrior on 2007-12-13
Machine: Dell Vostro 1500 and running Kubuntu Gitsy 7.10 on it;


Well, i have got my wireless to work on my laptop, but this problem started a while ago..The wireless connection just dissapears out of nowhere, without warning. It still recognises the network, and shows the signal strength, but there is no connectivity. All i can do after that is use a wired connection and it works fine..i have sometimes been able to get the wireless on, after a lot of retries though.

I've tried shutting Knetwork manager, but i can't get it on again for some reason. Then the only option left is rebooting.

Most of the time, i reboot which takes care of the problem and internet seems to work normally. Also this happens when i switch the connections, i.e. when i go to university, its still sort of looking for my home network, a reboot sets it right though..strange.

Does anyone have any suggestions?

---

### Post by saru411 on 2007-12-13
i sometimes have a problem connecting to a wireless netowrk with my broadcom 1390 vostro 1500 also. what i do is click on the network manager and choose conntect to other wireless network. i make up a nework...something like none or unknown and let it try to connect for a few seconds. from there i then change back to the wireless network that i wish to connnect to and it works perfectly. ive run into this a few times and it always happens on particular networks i frequent. if it happens once i normally happens all the time with said network. other networks never give me issues. i hope that works for you

---

### Post by mushroomcloudwarrior on 2007-12-13
Well that's a pretty smart workaround man :P

Thanks for that.

Although fixes for the problem are still welcome..

---

### Post by rpotter28 on 2007-12-13
> **mushroomcloudwarrior said:**
> Machine: Dell Vostro 1500 and running Kubuntu Gitsy 7.10 on it;

I've tried shutting Knetwork manager, but i can't get it on again for some reason. Then the only option left is rebooting.

I have the same laptop, and have had no problems. I also use 3 different vpn's, and again no problems. I keep my wireless home vpn up for days, which is better than I could do with XP.

I am running gnome, while you mention Knetwork which is obviously KDE. Have you tried it under gnome?

Richard

---

### Post by mushroomcloudwarrior on 2007-12-14
I'm not a very computer savvy guy, didn't know about linux till about 6 months ago..

a computer enginner friend suggested i start with KDE because of its GUI and i've read multiple times that gnome will just be difficult with a newbie..

---

### Post by natehall on 2007-12-14
Well, i have got my wireless to work on my laptop, but this problem started a while ago..The wireless connection just dissapears out of nowhere, without warning. I..[/QUOTE] 

I've got a 1420N with Ubuntu preinstalled. The wireless does the same thing, signal still seen, but the  connection just goes away randomly. I go to network administrator and change to a setup I don't have (like modem attacted) and then back. As long as I get the network reconfig window poping up it resets the system and works fine for awhile. Today its been dropping out quite a bit.

---

### Post by mushroomcloudwarrior on 2007-12-14
Happened to me too, just today..

Lost connection, still showed that i was connected..but well i had to reboot (saru411's method didn't really work)

---

### Post by Paul S on 2007-12-14
have you tried opening a terminal and entering "sudo dhclient" when it drops out .. see if it helps.

---

### Post by mushroomcloudwarrior on 2007-12-15
Can you tell me what that is? i mean what am i doing when i enter that in a terminal..

Anyway, will try it the next time it goes off like that.

---

