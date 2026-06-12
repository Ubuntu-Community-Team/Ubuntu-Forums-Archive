---
title: "enemy territory: cant connect to server"
date: 2007-07-25
forum: Gaming &amp; Leisure
---

### Post by h2z on 2007-07-25
The previous posts went unanswered, I installed the game with no particular problems and even managed to get the sound working but I cant seem to connect to any server :/ It hangs up for a few seconds when trying to refresh the server list and it just goes into an infinite loop of "awaiting challenge #x". I'm behind a LAN network and I have no problems connecting from my other OS with no ports forwarded. Any ideas? :(

---

### Post by Gen2ly on 2007-07-26
This a normal problem.    Usually its because ET needs an updated Punkbuster client.  View this site to see more on that.

[http://gentoo-wiki.com/HOWTO_Quake_III_Arena_/_Enemy_Territory](http://gentoo-wiki.com/HOWTO_Quake_III_Arena_/_Enemy_Territory)

---

### Post by h2z on 2007-07-27
Updated punkbuster and I still get the same problem :S

---

### Post by asipi on 2007-07-28
could be that a firewall issue in ubuntu. look after if you have any active rules...
command: sudo iptables -L
I have no rules so the output on my system is the following:
```

Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

```

as you see it is empty. if you have rules that could be a reason.

---

### Post by h2z on 2007-07-28
Am I looking for anything specific there? I dont like the idea of exposing my whole settings on this board...

EDIT: I'm using firestarter, are there any options I should leave off?

EDIT2: flushed iptables and the problem is still there. Maybe it has something to do with me being behing a NAT router?

EDIT3: Installed XQF and added "rule" in firestarter, Game connects fine to servers now!

---

### Post by weblordpepe on 2007-07-28
If you ask me, and you didnt, my advice would be to uninstall Firestarter. There is no need for it. The desktop-firewall idea is for Windows-only, and even on that OS its an illogical concept.

---

### Post by asipi on 2007-07-30
agree. completely useless if you behind a nat router :)

---

### Post by weblordpepe on 2007-08-01
> **asipi said:**
> agree. completely useless if you behind a nat router :)Finally! Someone who sees the light. :) Ya got no idea how difficult it is to convince people of the basic principals behind why a desktop firewall is pants.

---

### Post by equity on 2008-06-28
> **weblordpepe said:**
> Finally! Someone who sees the light. :) Ya got no idea how difficult it is to convince people of the basic principals behind why a desktop firewall is pants.

Btw, removing or purging firestarter does not touch iptables.

---

### Post by lillypop on 2008-06-28
I have no firewall and no issues connecting to servers  so it could be your firewall.
Even when i was on windows i turned off my firewall to play ET as it can cause issues with PB and cause you to be kicked for all the normal pb Bulls*** kicks.
Plus it can make you lagg same as anivirus software that sometimes affects PB and causes Pb issues and kicks .
 If you know the server your playing on and trust teh server operators then theres no need for antivirus or firewall protection.
I run a 2.55 server and a 2.6b scrim server with my husband we have our own Clan we advise players who experience connection issues to turn off both firewall and antivirus.
If you really feel the need to use the firewall you must make sure all things related to Et and PB are allowed internet access.
Sometimes most issues are fixed by completely exiting ET rebooting your pc and trying again.
Normally the the most annoying and what seem complex problems have teh easiest fixes.

Try connecting to a server that isn't running PB if you connect with no issues then you have a PB issue go to evenbalance.com if you can't fix the Pb issue and place a support Ticket with them they take a few days to respond but them make the program so they are the best ones to fix some issues.

---

### Post by MepisReign on 2008-06-28
That is not a Router/Firewall problem, that's a Persmissions problem, try to start ET typing, *sudo ET* on a terminal and let us know what happens there...

Best Regards,

MepisReign

---

