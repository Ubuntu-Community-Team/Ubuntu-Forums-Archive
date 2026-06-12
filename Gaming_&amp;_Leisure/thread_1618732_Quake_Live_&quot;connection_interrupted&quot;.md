---
title: "Quake Live &quot;connection interrupted&quot;"
date: 2010-11-11
forum: Gaming &amp; Leisure
---

### Post by 1337-1 on 2010-11-11
A while back, I posted here about an issue I was having with online gaming on my ubuntu computer (my previous thread can be found [here]("http://ubuntuforums.org/showthread.php?p=8714800")).  I tried the prescribed solution, to no avail.  That was a while ago, and since then, the new QL has been released, and I'm still having the same issue.

In short, whenever I connect to a game of quake live, it complains about "connection interrupted", and after a few seconds, spams variants of the following message:
NET_SendPacket ERROR: Resource temporarily unavailable to 202.172.99.1:27048

I tried the solution in the above thread, and it simply changes the numbers written above.  Eventually, I gave up trying to account for all the number changes.

Can anyone come up with a solution?  I'm sure its probably simple, and my windows laptop, and multiple consoles are all able to connect to games without any issues.

---

### Post by darkhelmetchris on 2010-11-11
> **1337-1 said:**
> NET_SendPacket ERROR: Resource temporarily unavailable to 202.172.99.1:27048

I am a Quake enthusiast too.  I know this is basic, but, what happens if you turn off your Ubuntu firewall completely (just temporarily of course).  Do you still get disconnected?  It *might also be an interesting test to not only turn off the Ubuntu firewall, but also put your machine in your router's DMZ ... (bad I know, but it's just for a quick test).  What happens then?  Do you get dropped?

It seems to me that I remember reading somewhere that there is/are secondary port(s) that the server tries to talk back to you on, in order to test if you're "still there".  It has been a while since I read such things, so I am afraid that I can't give you any details off the top of my head, but, I do wonder what the result of "no firewall" is.

I am interested to know what your results are with that.

---

### Post by 1337-1 on 2010-11-11
I've got no idea on how to that without installing something like firestarter (I'm downloading that now anyway, just in case).  Not sure if I mentioned already, but I'm connected to the net via wifi (thus most of my efforts so far are via a router).  Will try firestarter when its finished

EDIT: Forgot I can't install stuff until I get around to updating to the next version of ubuntu.  Will do that friday, but until then :P

---

### Post by darkhelmetchris on 2010-11-11
> **1337-1 said:**
> I've got no idea on how to that without installing something like firestarter (I'm downloading that now anyway, just in case).  Not sure if I mentioned already, but I'm connected to the net via wifi (thus most of my efforts so far are via a router).  Will try firestarter when its finished

Alrighty, to disable your existing firewall, you can use this native command:
```
sudo ufw disable
```

Have you tested whether or not this happens when you are on a wired connection?  If you're on wifi, that could sometimes affect your connection, there can be brief interruptions when your router/adapter searches during auto-channel selection.  Some routers do this while you're running.  You wouldn't normally see any side effects with simple things like web browsing or downloads, but with gaming, you certainly can.

---

### Post by 1337-1 on 2010-11-12
Just tried it with the firewall off, no luck, nothing changes.  I'll be hard pressed to try and do a wired connection, but I'll try my best and post the results if I can manage (router is downstairs, and isn't easily accessed)

---

