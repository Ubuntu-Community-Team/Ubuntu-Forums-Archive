---
title: "Unreal Tournament won't reconnect"
date: 2005-10-13
forum: Gaming &amp; Leisure
---

### Post by BLTicklemonster on 2005-10-13
I can't get unreal tournament to reconnect to a server between maps. It just sits there. I will check the server logs and post later today.

First Breezy post!!!! woot woot

---

### Post by BLTicklemonster on 2005-10-13
If any of you are fluent in server admining, this is from our server log:

```
ScriptLog: [~] starting Server Advertisements version 101
DevNet: NotifyAcceptingConnection: Server MyLevel accept
NetComeGo: Open MyLevel 10/11/05 22:51:47 my IP address
DevNet: NotifyAcceptingChannel Control 0 server Level CTF-BL-1v1-JOUST-asc-TM.MyLevel: Accepted
DevNet: Level server received: HELLO REVISION=0 MINVER=432 VER=436
Log: Resolved unreal.epicgames.com (207.135.145.19)
ScriptLog: UdpServerUplink: Master Server is unreal.epicgames.com:27900
ScriptLog: UdpServerUplink: Port 7779 successfully bound.
Log: Resolved master0.gamespy.com (207.38.11.34)
ScriptLog: UdpServerUplink: Master Server is master0.gamespy.com:27900
ScriptLog: UdpServerUplink: Port 7779 successfully bound.
ScriptLog: >>SayLog>> 2005/10/11 22:51 (NewPlayer): Creating new Infraction Record 0 for Player  0
NetComeGo: Close TcpipConnection293 10/11/05 22:51:55
DevNet: Recovered from extra data received after socket close: my IP address
DevNet: Recovered from extra data received after socket close: my IP address
DevNet: Recovered from extra data received after socket close: my IP address
DevNet: Recovered from extra data received after socket close: my IP address
DevNet: Recovered from extra data received after socket close: my IP address
DevNet: Recovered from extra data received after socket close: my IP address
DevNet: Recovered from extra data received after socket close: my IP address
DevNet: Recovered from extra data received after socket close: my IP address
DevNet: Recovered from extra data received after socket close: my IP address
DevNet: Recovered from extra data received after socket close: my IP address
DevNet: Recovered from extra data received after socket close: my IP address
DevNet: Recovered from extra data received after socket close: my IP address
DevNet: Recovered from extra data received after socket close: my IP address
DevNet: Recovered from extra data received after socket close: my IP address
DevNet: Recovered from extra data received after socket close: my IP address
DevNet: Recovered from extra data received after socket close: my IP address
DevNet: Recovered from extra data received after socket close: my IP address
DevNet: Recovered from extra data received after socket close: my IP address
DevNet: Recovered from extra data received after socket close: my IP address
DevNet: Recovered from extra data received after socket close: my IP address
DevNet: Recovered from extra data received after socket close: my IP address
DevNet: Recovered from extra data received after socket close: my IP address
DevNet: Recovered from extra data received after socket close: my IP address
DevNet: Recovered from extra data received after socket close: my IP address
DevNet: Recovered from extra data received after socket close: my IP address
DevNet: Recovered from extra data received after socket close: my IP address
DevNet: NotifyAcceptingConnection: Server MyLevel accept
NetComeGo: Open MyLevel 10/11/05 22:52:00 my IP address
DevNet: NotifyAcceptingChannel Control 0 server Level CTF-BL-1v1-JOUST-asc-TM.MyLevel: Accepted
DevNet: Level server received: HELLO REVISION=0 MINVER=432 VER=436
NetComeGo: Close TcpipConnection294 10/11/05 22:52:10


```

At that point it just repeats itself over and over again until I log off. Now in the console of UT, I have no option to disconnect from the server, only reconnect, which does no good, also, going to open location and attempting to log back in that way does no good. It's like it won't let go of me. I'm sending something extra that our server just doesn't quite care to see. I wonder what that is?

---

### Post by KingBahamut on 2005-10-13
I think its the mods that would be causing this. Are you running UTPure or some other anti-cheat or purification mod on that server, assuming its yours? 

DevNet: NotifyAcceptingChannel Control 0 server Level **CTF-BL-1v1-JOUST**-asc-TM.MyLevel: Accepted. 

Gah Joust.......I hate , I absolutely hate that map. Never play that map with like 15 people...its wrong, very very wrong.

---

### Post by xeta on 2005-10-13
Have you tried to adjust your netspeed from its default setting?

---

### Post by BLTicklemonster on 2005-10-13
[QUOTE=KingBahamut]I think its the mods that would be causing this. Are you running UTPure or some other anti-cheat or purification mod on that server, assuming its yours? 

DevNet: NotifyAcceptingChannel Control 0 server Level **CTF-BL-1v1-JOUST**-asc-TM.MyLevel: Accepted. 

Gah Joust.......I hate , I absolutely hate that map. Never play that map with like 15 people...its wrong, very very wrong.[/QUOTE]
???? Joust ???? 
Do you mean the one on 2k4 or the one on UT? 

(CTF-BL-1v1-JOUST-asc-TM is my map, took it from 2k4 and redid it in UT because I love it so much, lol. that's what the TM means, "TickleMonster" :) )

Oh, and if you ever played on the black legion Zark server for UT 67.19.84.40 I did the sniper rifle, too. Way more accurate than normal Zarks, and I have it so that it's WYSIWYH, WHAT YOU SEE IS WHAT YOU HIT, lol allll the way across a huge map. bam dead.

---

### Post by xeta on 2005-10-13
BLTickle, are you still having problems?

---

### Post by BLTicklemonster on 2005-10-13
Yeah, read above. But I think actually, it may be my router. I've got it set to allow me to set up a UT server (Beta-testing new game types for Bond Designs a while back) and I remember that once before I'd done that, and it kept me from going back into 2k4 servers. I'll kill the port tonight and see if that's the problem. (and then find another one, wait and see, lmao ) 

but thanks for asking! lol :rolleyes:

---

### Post by BLTicklemonster on 2005-10-15
Bah. I closed my ut port on my router, but it still won't let me reconnect between maps. This is frustrating because ut plays really really smooth on Ubuntu. I'm hooked as far as playing on it, if I can only get it to reconnect. I guess I'll go over the ini file with a fine toothed comb.

---

### Post by BLTicklemonster on 2005-10-16
Changed net speed, and it still had problems. I had it work one time, using ogl instead of sgl or whatever it defaults to. then it didn't do it again. 

Of course I've just attempted to install the latest nvidia drivers again, so yes, I'm on a fresh install of Breezy again, so I'll try with a fresh install and see what happens.

---

### Post by BLTicklemonster on 2005-10-18
New install of Breezy and UT. Same problem. (man ubuntu and UT go together really well except for that)

We've tried it without UTDC, same problem (it doesn't work with linux anyway). I haven't attempted to hit any other servers, so I can't say for sure that it's even me. (I used to be the sole admin, but we've had a fellow who declared that he was the new one, and I let him go at it, and since then, probably just a coincidence of course, but since then we've been having some really wierd problems. ZARK ARMS, all those really whacky weapons I modded, the zark flak cannon, the zark insta gib, zark redeemer, all that is off the server now because he wanted to try to solve some issues by changing mapvote. I'M GOING IN THERE TODAY AND PUTTING IT BACK OF COURSE, LOL)

So ah, I'll try some other servers tonight, and let you know)

---

### Post by BLTicklemonster on 2005-10-18
Okay, it's not the server. I went to another one and the same thing happened. It's like UT won't let go of the internet connection. When I close UT and try to open Firefox, it takes way long to come up.

I'm wondering if there's some way to monitor network activity while ut is up?

---

### Post by BLTicklemonster on 2005-10-19
Is there no one familiar with UT and or networking enough to answer this? 

Heck, just mentioning networking gave me an idea I should have tried already, and that is to try it without the router. 

See? Even I can come up with suggestions. 

Or are all of you afraid that I'm going to come to your server and pwn you?

---

