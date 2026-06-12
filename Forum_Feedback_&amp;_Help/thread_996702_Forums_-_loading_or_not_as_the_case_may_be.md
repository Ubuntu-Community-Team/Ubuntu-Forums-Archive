---
title: "Forums - loading or not as the case may be"
date: 2008-11-29
forum: Forum Feedback &amp; Help
---

### Post by Elfy on 2008-11-29
Ok I can understand the forums being slow when it's overloaded but today with

Currently Active Users: 7340 (482 members and 6858 guests) 
 it's worse than it was when we had 20000 or more on here :(

I'm getting the proxy issue constantly as here [http://ubuntuforums.org/showthread.php?t=990831](http://ubuntuforums.org/showthread.php?t=990831)

Also the "maintenance/downtime" page

I know that we have a new server but it doesn;t really seem to be making a whole lot of difference.

I try and spend more time on here when America's sleeping but if it doesn't get better I'm going to have to resort to shouting at the screen soon and I already have a sore throat.

Is there at least some light at the end of the tunnel here?

:)

---

### Post by drubin on 2008-11-29
> **forestpixie said:**
> Is there at least some light at the end of the tunnel here?

:)

[http://ubuntuforums.org/showpost.php?p=6257036&postcount=15](http://ubuntuforums.org/showpost.php?p=6257036&postcount=15)

Maybe they will bring back the server.... (maybe a reason for it being less responsive with less users)

---

### Post by jpeddicord on 2008-11-29
"Server Load Averages  	4.58  3.99  3.67 | 12,216 Users Online"

This is calm for what it usually is, probably because these aren't peak hours. When that other server is brought back into the cloud (or has it been already? no idea) things will probably improve.

The linked cache issue means that the running web server crashed and that the squid cache in front of it couldn't find another server available. When two servers are online, you would (should) never see this unless both servers crash at the same time. Squid should be routing requests to the second server if they can't reach the first, but this may not be the case as I have no idea *how* it is actually configured.

---

### Post by Elfy on 2008-11-29
I haven't as such got a problem - just try to bring to the attention of those who know that I've had problems when the load is normally low - ie 9AM GMT sort of (ish)

I guess the expectation was that once the new server was around that the problem we've had for 6 months or so would diminish - which to a degree has happened, at least I can get on the forums in my evening - which is probably mid afternoon AMerican time.

Just really an observation - which can probably only be answered with any certainty by someone who knows where the new server si at the moment.

I know that ubuntu-geek was playing with it this/last week but who knows.

At the end of the day I'd probably still perservere if there was only one server and as an aside I tried shouting but it didn't help :)

---

