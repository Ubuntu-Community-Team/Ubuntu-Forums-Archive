---
title: "These forums are really slow, even on a broadband connection."
date: 2007-08-26
forum: Forum Feedback &amp; Help
---

### Post by some_random_noob on 2007-08-26
I'm in New Zealand and I'm using a 256/128Kbps connection, and these forums are bloody slow compared to other sites. Does anyone else have this problem? I think it's either because...

(1) The server is overloaded with searches etc, and takes longer to render & respond.
(2) The bandwidth sucks.

Is it just because of my connection speed and location, or could more be done? What's your experience with these forums?

---

### Post by Chymera on 2007-08-26
I think the great number of users here has something to do with it... 

as you can see, search flood is also limited by a rather high timestep...

---

### Post by bapoumba on 2007-08-26
No being of much help, but it's fine here for me. Did you look at the ipv6 things, and may be your router config?
[URL="http://ubuntuforums.org/showthread.php?t=475299"]
http://ubuntuforums.org/showthread.php?t=475299[/URL]

---

### Post by Dark Star on 2007-08-26
Guys I mean Admin why don't you use IPB board I think its way stable @ more users :) What say I am also feeling it slow @ 256Kbps :(

---

### Post by popch on 2007-08-26
I can not detect any problems with the speed of this forum as compared with other resources on the internet.

The other day there was a problem with Firefox waiting in every transaction for a response from google.(something). But that was transient, and now I have quite reasonable response times again.

---

### Post by diffuze on 2007-08-26
Fast and snappy for me. 
I'm in Sweden on a 8 Mbps connection.
:guitar:

---

### Post by Dark Star on 2007-08-26
> **diffuze said:**
> Fast and snappy for me. 
I'm in Sweden on a 8 Mbps connection.
:guitar:
:o 8Mbps :o Awesome man ..

---

### Post by kerry_s on 2007-08-26
> **some_random_noob said:**
> I'm in New Zealand and I'm using a 256/128Kbps connection, and these forums are bloody slow compared to other sites. Does anyone else have this problem? I think it's either because...

(1) The server is overloaded with searches etc, and takes longer to render & respond.
(2) The bandwidth sucks.

Is it just because of my connection speed and location, or could more be done? What's your experience with these forums?

if you have adblock+ block google-analytics, just click add filter and put> *.google-analytics.* <that slows the forum down alot on some systems, on mine if i don't block it, it takes a extra 30sec's to load pages. damn that google spyware :lolflag:

i don't block much but i block that.my list>

```

[Adblock]
/\D\d{2,3}x\d{2,3}\D/
/[\W\d](double|fast)click[\W\d]/
/[\W\d_](top|bottom|left|right|)?banner(s|id=|\d|_)[\W\d]/
/[\W\d](onlineads?|ad(banner|click|-?flow|frame|ima?g(es?)?|_id|js|log|serv(er|e)?|stream|_string|s|trix|type|vertisements?|v|vert|xchange)?)[\W\d]/
*.atdmt.*
*/kokoku/*
*.google-analytics.*
*.googlesyndication.*
*.servedby.advertising.*


```

---

### Post by PriceChild on 2007-08-26
Works perfectly for me... although I'm in the same country as the servers...> **Dark Star said:**
> Guys I mean Admin why don't you use IPB board I think its way stable @ more users :) What say I am also feeling it slow @ 256Kbps :([http://ubuntuforums.org/showthread.php?t=176622](http://ubuntuforums.org/showthread.php?t=176622)

---

### Post by _simon_ on 2007-08-26
I'm here at various times of the day and never have a problem.

---

### Post by diffuze on 2007-08-26
> **Dark Star said:**
> :o 8Mbps :o Awesome man ..
Good for two things; online gaming and downloading of linux iso's. :popcorn:

---

### Post by mips on 2007-08-26
I'm in South Africa with a 384/128Kb/s adsl connection and the forums seem fast enough, no slower than any other sites.

---

### Post by some_random_noob on 2007-08-27
Hmmmmm this is an interesting observation. It could be the crappy internet speeds in New Zealand. It's so stupid - files only download at 30Kbps because NZ ISPs like to throttle stuff. It sucks having a monopoly in charge.

When I go into a section of these forums, such as the cafe - all threads appear one after the other. Instead of all of them appearing at once. It's very slow :( Man this sucks.

When I do a test at speedtest.net it says that I have a 200ms latency. The distance is between Christchurch and Auckland, which isn't far (New Zealand is a very small country). Is 200ms of latency normal when testing against a server which is in the same country? You can fly that distance in about an hour, so Auckland (The test servers location) is pretty close to me.

---

### Post by mips on 2007-08-27
200ms sounds a bit high. I got 135ms to a local server but I don't really trust the speedtest results.

Do a traceroute to ubuntuforums.org and post the output here.

Another suggestion is try an use other dns servers like OpenDNS instead of those assigned by your ISP.

Did you globally disable IPv6 ?

---

### Post by ubuntu-geek on 2007-08-27
Sometimes the server is slow for me in the US as well. I chalk it up to bandwidth and sometimes server loads.

---

### Post by stryder73 on 2008-02-16
It could also have something to do with your personal settings.  Your browser, firewall(s), and even possible virus/malware infection could really hinder the performance.  

The only problems I've ever come across normally break down to a few quick things to look for.
1) Ads; As mentioned before, when there are alot of them, it takes more time loading.
2) Browser Settings; Cookies, XML scripts, "helpers", etc are all loaded when you open the browser and some are totally un-needed.  Spending a little time stream-lining this area will help.
3) Tool-Bar add-ons; If there is anything streaming, turn it off.  The "convienience" is really more of a waste.  Having a seperate app running in the background for streaming music, etc is better use of the BW so it's not all bottlenecked to one app loading everything.  
4) Website Streams; Not something you can personally control, but in trying different things with my site, I have noticed that during large file transfers through FTP or when I used a streaming app to host an online radio station, it degrades the loading times for the members.  This was also with 100,000GB of BW / month from my hosting.
5) Firewalls/Modems/Routers; Checking the prefferences and setup of these devices is a good idea.  Depending on what level you have your settings at, you may want to include this site on the "white list" of trusted sites.
6) The last thing I've come across is connection.  If your broadband is from a cable-company, you may have slower response depending on the volume of users in your grid.  For both DSL and Cable, checking the wiring coming in from the terminal box to the modem is a good idea unless the ISP did a complete install for you and checked/replaced already.

Anything else I can think of has already been covered and I'm sure you probably have thought of all this already.  ;)

---

### Post by LukeCarrier on 2008-02-16
Well I think they're pretty fast, as long as the admins keep on top of tidying the databases and maintaining the servers I don't think there's a problem.

---

### Post by popch on 2008-02-16
Did you notice the age of this thread? If there was still an issue, I would think that there ought to be more recent posts. Speaking about sleeping dogs...

---

### Post by LukeCarrier on 2008-02-16
No I didn't actually, I'm away with the fairies today.....I'll go make myself useful somewhere else (in another thread).

---

### Post by stryder73 on 2008-02-16
Lol, sorry about that.  Did a search and didn't notice the age. 

On the other hand, keeping supportive info going isn't a useless task since someone else could just as easily have a simular problem currently or in the future.  As the thread shows, it seemed to be more of a reletive issue for the thread starter than that of these forums themselves.  It's also nicer to the DB if we update info as it comes up rather than having a bunch of simular threads all being sorted through.  :D

---

### Post by hhhhhx on 2008-02-16
im at work, useing a t1 cable
 
*starts dancing*

---

### Post by LaRoza on 2008-02-16
> **xhhux said:**
> im at work, useing a t1 cable
 
*starts dancing*

Could you send some cable my way?

---

### Post by LukeCarrier on 2008-02-16
> **LaRoza said:**
> Could you send some cable my way?
Lol, I can only get 2MB =[

---

### Post by hyper_ch on 2008-02-17
> **diffuze said:**
> Fast and snappy for me. 
I'm in Sweden on a 8 Mbps connection.
:guitar:

I thought in sweden you get nowadays cable connections with 100mbit...

---

### Post by some_random_noob on 2008-02-19
Hey, my thread is back!

I think the reason for the slow speed of these forums is because my broadband connection is throttled (Both ways) to 30kbps (Which my ISP never told me about). Yes, sad I know... don't laugh or I'll stab you. I hate living in a technologically impaired country.

---

### Post by hyper_ch on 2008-02-20
Broadband at 30kbps? That's not broadband at all... that's normal modem speeds (even slower actually as it gets up to 56kbps)

---

### Post by mips on 2008-02-20
> **some_random_noob said:**
> Hey, my thread is back!

I think the reason for the slow speed of these forums is because my broadband connection is throttled (Both ways) to 30kbps (Which my ISP never told me about). Yes, sad I know... don't laugh or I'll stab you. I hate living in a technologically impaired country.

What ISP & Product do you use?

Don't you mean 30k**B**s?

---

### Post by some_random_noob on 2008-02-20
> **mips said:**
> What ISP & Product do you use?

Don't you mean 30k**B**s?
It's with Orcon - but they are only a wholesaler. The hardware and everything is regulated and controlled by Telecom New Zealand. Having throttled connections is the norm here. If I went back to dialup it wouldn't feel like much of a difference (Sad but true!).

Email and websites go at 256k/128k (up/down) but everything else (File sharing, downloads, OS patches) will be throttled to 30k. I don't know whether it's KiloBytes or KiloBits... but it doesn't really matter does it? Because it's so slow anyway. Dialup is 5k when downloading, and mine is 30k. Lol. With all the flash-content on pages these days it makes it even worse. Sometimes I have to sit and wait 5-12 seconds for a page to load :mad:

---

### Post by mips on 2008-02-21
> **some_random_noob said:**
> 
I don't know whether it's KiloBytes or KiloBits... but it doesn't really matter does it?

It makes a big difference. There are 8bits in a byte so things are 8x faster in 30kBytes vs 30kbits in theory (although in real life it is slightly less).

This website states the opposite to what you are claiming, [http://www.orcon.net.nz/faqs/residential_broadband_faq/do_you_restrict_bandwidth_or_throttle_peer_to_peer_p2p_traffic/](http://www.orcon.net.nz/faqs/residential_broadband_faq/do_you_restrict_bandwidth_or_throttle_peer_to_peer_p2p_traffic/)
Traffic is shaped but only when network loads are high.

---

### Post by some_random_noob on 2008-02-21
> **mips said:**
> 
This website states the opposite to what you are claiming, [http://www.orcon.net.nz/faqs/residential_broadband_faq/do_you_restrict_bandwidth_or_throttle_peer_to_peer_p2p_traffic/](http://www.orcon.net.nz/faqs/residential_broadband_faq/do_you_restrict_bandwidth_or_throttle_peer_to_peer_p2p_traffic/)
Traffic is shaped but only when network loads are high.

Yes, but:

> This means that **if the network is experiencing very high load** then quality of service is maintained for the types of traffic that need it the most. Peer to peer program users may notice a small reduction in the speeds obtainable for that period of peak traffic.

Note that this traffic management only applies to international traffic. We do not generally shape domestic traffic **unless there is threat to network stability**. 

There's fineprint in it. The network is ALWAYS overloaded and there is ALWAYS a threat to network stability. They haven't made any major upgrades to their exchanges in the last 8 years. I'm certain that they throttle 24-7. I have never downloaded a file at a faster speed than 30k.

---

### Post by mips on 2008-02-22
> **some_random_noob said:**
> The network is ALWAYS overloaded and there is ALWAYS a threat to network stability. They haven't made any major upgrades to their exchanges in the last 8 years. I'm certain that they throttle 24-7. I have never downloaded a file at a faster speed than 30k.

Then they have a crappy network or simply refuse to do proper capacity planning. Altetrnatively they could be sweating their assests and squeezing every penny out of it at the expense of their clients and it would be pretty safe to bet that this is the case. Would love to know their contention ratios.

---

### Post by some_random_noob on 2008-02-22
> **mips said:**
> Then they have a crappy network or simply refuse to do proper capacity planning. Altetrnatively they could be sweating their assests and squeezing every penny out of it at the expense of their clients and it would be pretty safe to bet that this is the case. Would love to know their contention ratios.
Yeah that's pretty much the case. As for the contention ratio, I think you'd have to obtain super-top-secret-leaked documents to find that out. I read a few years ago that it was 140:1 or something... and that the international standard is 60:1? Maybe I can't remember, or maybe I was wrong? I think I'll ring up some time with a recording device and try to pester them into telling me... then post the recording on the net :D

---

### Post by mips on 2008-02-22
Good luck, I don't think you are going to get much out of them. I personally think it should be a legal requirement for ISP/Telecom companies to publish their contention ratios so consumers at least know what service they can expect and what they are paying fo.

---

### Post by some_random_noob on 2008-02-22
> **mips said:**
> Good luck, I don't think you are going to get much out of them. I personally think it should be a legal requirement for ISP/Telecom companies to publish their contention ratios so consumers at least know what service they can expect and what they are paying fo.
I totally agree that people have a right to know - I could probably take this to the Commerce Commission and find out :)

But before I go ringing around, what exactly is line contention? It's the number of connections per "line" isn't it? Where they have a line coming from an exchange going down the street with more wires coming off the main line which go into houses?

(Exchange here)--------------(Main line here)-------------------------------------
.........................|.........................|.........................|
.........................v.........................v.........................v

(The main line is the dashs, and the 'v's are more lines which go to houses) So there would be ~140 lines coming off the main line, which makes the line contention ratio?

Is this diagram correct?

---

### Post by mips on 2008-02-22
It actually has nothing to do with subscriber lines but how they split up the available bandwidth from the internet 'pipe'. 

Example:
Say you have four adsl user on a DSLAM (hub) and each user gets 256kbs, so in theory to guarantee every user 256kbs you would need a 1Mbs pipe out of the DSLAM to the ISP and this applies throughout the whole network.

This however does not happen as it would be way to expensive to implement and is not really needed because:
1. Not all users are online at the same time
2. Network traffic is genrally bursty in nature and not constant.

The above lets a provider only provide a 512kbs pipe instead of a 1Mbs pipe and apply the same principal throughout their network, for both local and international traffic.

There is usually a sweet spot as to the how much bandwidth they allocate to users and from this is basically your contention ratio which is fine in most cases. QoS will help with certain traffic types that are sensitive to latency and other things (VoIP is a good example & email is a bad example).

However some providers increase the contention ratio to fit more users onto the same 512kbs pipe in order to make more money. This is where service and the customer suffers.

I hope what I wrote here makes sense. [http://en.wikipedia.org/wiki/Contention_ratio](http://en.wikipedia.org/wiki/Contention_ratio)
Or alternatively google contention ratio

---

