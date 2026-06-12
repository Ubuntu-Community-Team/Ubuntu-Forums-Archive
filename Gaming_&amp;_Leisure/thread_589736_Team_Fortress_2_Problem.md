---
title: "Team Fortress 2 Problem"
date: 2007-10-24
forum: Gaming &amp; Leisure
---

### Post by brownmoocow on 2007-10-24
Hey everyone, first post finally after... almost a year of using Ubuntu? :P

Anyways, I'm having a slight problem with TF2 that I couldn't find anywhere else on the forums. I can start Steam, and Orange Box installed with absolutely no problems. However, when I check for servers in TF2 (where they just apply the 'Team Fortress 2' filter) I get nothing. 

I've left it up for ten minutes or so at a time, and not one server pops up. Traffic goes out according to bmon, and I can get all sorts of servers in CS:S, so my initial noob diagnosis has me thinking its not Steam or a net problem.

Are there just so few TF2 servers around this early in the release? Is anyone else having this same problem?

Thanks in advance for any help :)

---

### Post by snkmad on 2007-10-24
I know this wont fix your problem, but you can look for TF2 servers @ [www.game-monitor.com](www.game-monitor.com)
Hope this helps.

---

### Post by upbeat.linux on 2007-10-24
I had the same problem initially, but here are two things to check.

1. Stop the initial search for servers and wait a bit. Then start a new search. Whenever I launch TF2 or the server browser from Steam the initial search will stay pending indefinitely.

2. Make sure you don't have an outgoing firewall rule that is filtering connections. I know this shouldn't matter if CS:S is working, but you never know. Stranger things have happened.

FYI, there are over 2,000 TF2 servers available via Steam.

---

### Post by brownmoocow on 2007-10-24
Well, as an update, I got it to work. It's odd - I could see servers under the 'Servers' tab in Steam. If I tried to join one of those, then disconnected, I could refresh a server list inside of the game. 

On the topic of port forwarding though, it's been a while since I played a game online. I've had this router for years though, so some old ports that I remembered are still forwarded. I've got 7001 forwarded on both TCP and UDP for some reason, along with 6003 (same case.) 27005 and 27010 - 27015 are forwarded on UDP. I haven't double checked to see if this is correct, but I'll do some troubleshooting later to make sure the port ranges are right.

Oh, and thanks for the server list site. It doesn't fix the problem, but it definitely provides a work-around in case this happens elsewhere. :)

---

