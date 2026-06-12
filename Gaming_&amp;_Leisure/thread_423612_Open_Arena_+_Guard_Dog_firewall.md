---
title: "Open Arena + Guard Dog firewall"
date: 2007-04-26
forum: Gaming &amp; Leisure
---

### Post by Neo Tom Bombadil on 2007-04-26
Hi I'm trying to figure out how I "poke" open arena through my Guard Dog firewall.

IP tables work fine 

There's no preset allow button under game and I tryed making a custom defined protocol @ port 27960 bydirectional UDP, but maby It seems I need to open more ports? 

So maby a list of ports I should have open would help, thanks.

---

### Post by mbradlcu on 2007-05-18
would 'netstat -upant' show you the ports you need?
                
udp        0      0 0.0.0.0:27666           0.0.0.0:*                          21390/doomded.x86
udp        0      0 0.0.0.0:8777            0.0.0.0:*                          11459/ucc-bin       
udp        0      0 0.0.0.0:57929           0.0.0.0:*                          1329/sdlquake2                     
udp        0      0 0.0.0.0:7777            0.0.0.0:*                          11459/ucc-bin       
udp        0      0 0.0.0.0:7778            0.0.0.0:*                          11459/ucc-bin       
udp        0      0 0.0.0.0:7779            0.0.0.0:*                          11459/ucc-bin       
udp        0      0 0.0.0.0:7780            0.0.0.0:*                          11459/ucc-bin

---

