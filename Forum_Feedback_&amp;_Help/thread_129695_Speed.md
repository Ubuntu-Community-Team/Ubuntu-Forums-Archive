---
title: "Speed?"
date: 2006-02-14
forum: Forum Feedback &amp; Help
---

### Post by thermans on 2006-02-14
Are there any plans to move "ubuntuforums" to a faster server?

It takes an average of 30 seconds for each page to load.  And I'm not kidding!

I know it's not just me,  I've tried it from numerous places and on numerous machines.

Not complaining, you understand, just concerned. :)

---

### Post by Robgould on 2006-02-14
It does not take anywhere that long on my computer. It is actually quite snappy for me.
 
I use Firefox, IE, and Avant all in differnt places.

---

### Post by bonzodog on 2006-02-14
I have to say it, but it doesn't take anywhere near that long on mine either. I have however found that sometimes extended downloads of webpages means that you need to disable IPv6 in firefoxes own setup.

---

### Post by ubuntu-geek on 2006-02-14
Firefox 1.5 it loads in 2.2seconds.. Are you on dialup?

---

### Post by teet on 2006-02-14
It takes quite some time on my machine as well.  In both windows and linux with firefox 1.5.0.1 (ipv6 disabled, and pipelining turned on at like 6 requests).  Other pages load faster (e.g. [www.espn.com](www.espn.com) ).  I'm on my college's network...so it SHOULD load fairly quickly.

-teet

Holy cow....I think this is my first post.  I joined a long time ago but I guess I  was always able to find the answer to my problems by searching :)

---

### Post by dantheman on 2006-02-14
for me, it takes an average of over 20 seconds to look these pages.... (not fully, until they have become visible). It's not my connection, cause I can get other [non-cached] pages very quickly. What's going on with this server?

---

### Post by xequence on 2006-02-14
[QUOTE=ubuntu-geek]Firefox 1.5 it loads in 2.2seconds.. Are you on dialup?[/QUOTE]

In Opera, for me, it takes about that.

---

### Post by byen on 2006-02-14
> Are there any plans to move "ubuntuforums" to a faster server?
I think so.. there was some talk about the forums moving to a server provided by Canonical (please correct me if I am wrong)
Coming to your problem... thats too long..did you disable IPv6 as suggested above?

---

### Post by earobinson on 2006-02-15
never had it that bad!

---

### Post by Robgould on 2006-02-15
I tried again last night from my laptop running ubuntu and using firefox with the fasterfox extension.  Forum pages loaded in under 3 seconds on all attempts, usually under 2.5, and frequently under 2.

---

### Post by steve.horsley on 2006-02-19
As it happens, I've been wanting to complement the forum's operators on the improvement in speed. Until about a month ago, I was getting load times of 30-60 seconds, and was getting into the habit of repeatedly clicking the Go button to re-send the request. At this rate, the forums are almost unuseable. 

In the last month or so, things have got much better, and my page load times are consistently around 3 secs, and page timeouts are now very rare. I also notice there are generally many more users online so I guess others have seen an improvement too. 

I wonder if those still seeing poor performance are in any paricular geographic area - maybe there's a network problem somewhere?

---

### Post by thermans on 2006-02-20
It's all very strange.  

According to [GeoBytes]("http://www.geobytes.com/IpLocator.htm") the server for "ubuntuforums.org" (IP address 64.21.33.9) is located in New Jersey.  I am in Washington DC.  So it's not a physical thing.

I have the same response time with Firefox, Opera, IE on two different computers (one Linux one Windows), on three different networks (including one public wireless hotspot at Starbucks).

I tried turning off IPv6 on Firefox.  No difference.

The fact that others are getting good speed makes it even stranger.

I did an ethereal [trace]("http://www.hermans.net/ubforums.trace.dat").  I see the server coming back with an ACK after 0.018 seconds.  But the rest of the page does not show for another 20 seconds...

My traces show consistent 20 second response time.  This is better than the 30 seconds I saw when I first posted, but it still makes the forums hard to use...

---

### Post by majikstreet on 2006-02-20
geography doesn't make a difference on the internet period. the internet is redundant; there are multiple ways to get to places. your computer may not always take the fastest route to the server. it's just the way things are.
I live near DC too. also: your computer could go from DC to nebraska to alabama to wyoming to new jersey (the server)...
anyway, it took me 3.769seconds to load this page.

---

### Post by thermans on 2006-02-20
[QUOTE=majikstreet]geography doesn't make a difference on the internet period. the internet is redundant; there are multiple ways to get to places. your computer may not always take the fastest route to the server. it's just the way things are.[/QUOTE]

Not necessarily true.  Regardless of the route, your true bandwidth is limited by the slowest link along the way.  And if the server is in Hong Kong, you will definitely notice the latency from the US...  But I guess that's off-topic.

---

### Post by steve.horsley on 2006-02-21
[QUOTE=thermans]It's all very strange.  

According to [GeoBytes]("http://www.geobytes.com/IpLocator.htm") the server for "ubuntuforums.org" (IP address 64.21.33.9) is located in New Jersey.  I am in Washington DC.  So it's not a physical thing.

I have the same response time with Firefox, Opera, IE on two different computers (one Linux one Windows), on three different networks (including one public wireless hotspot at Starbucks).

I tried turning off IPv6 on Firefox.  No difference.

The fact that others are getting good speed makes it even stranger.

I did an ethereal [trace]("http://www.hermans.net/ubforums.trace.dat").  I see the server coming back with an ACK after 0.018 seconds.  But the rest of the page does not show for another 20 seconds...

My traces show consistent 20 second response time.  This is better than the 30 seconds I saw when I first posted, but it still makes the forums hard to use...[/QUOTE]

Yes, your TCP-level RTT is good. It doesn't look like lost packets. It look smore like an application delay. I notice that you are sending a login cookie as you connect, and I wonder if the server doesn't like your user-id for some reason. Maybe a database problem sending the server in circles. Try disabling cookies in Firefox and connect again, so you don't immediately log in.

Just a thought, and I could be wrong.

---

### Post by fuscia on 2006-02-21
it's instant on dillo, for me.

---

