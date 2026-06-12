---
title: "Fastest BitTorrent client on Ubuntu"
date: 2009-02-17
forum: General Help
---

### Post by super_czar on 2009-02-17
Been using Azureus for a while on my headless ubuntu server.
Had been on a crippled 448 kbps ADSL connection till now so speeds were never something to be worried aboutt since my connection would be the bottleneck and not the efficiency of the client application

Now that I am on a faster 2mbps line, I suspect (but am not sure) Transmission on my OS X machhine is giving me better download speeds than the Azureus install on my Ubuntu server

Would switching to Deluge / Tarnsmission/ any other client bring speed improvements?

The reason why I am asking this (instead of trying it out right away) is that my ubuntu server is a headless rig, and runs a bunch of other web apps apart from the azureus Web UI 

Configuring the Web UI to be accessible via Apache through a proxypass is a PITA and I'll do it only if I know that switching to Deluge/transmission/rtorrent/xyz will bring improvements
TIA :)

---

### Post by halovivek on 2009-02-17
Install utorrent under wine. you will get fast. i am doing that only.

---

### Post by konqueror7 on 2009-02-17
as i remember, azureus is written in java, so i think there is quite a performance issue there (experienced it myseld, but not saying that java is bad:o)...i'm using deluge, and its fast, just need to have a good setup of the settings i guess...

---

### Post by binbash on 2009-02-17
I always get max speed at deluge.Tried on 2 mbit and 20 mbit

---

### Post by geirha on 2009-02-17
Transmission has a built-in http-server in newer versions (1.20-ish and higher I think), so starting transmission-daemon should also start that http-server listening on port 9091. If transmission on your system is too old, you can get the latest stable from this ppa [http://forum.transmissionbt.com/viewtopic.php?f=13&t=5604](http://forum.transmissionbt.com/viewtopic.php?f=13&t=5604)

---

### Post by TenPlus1 on 2009-02-17
Deluge (configured properly) is the fastest I've used to date on Ubuntu...

---

### Post by scouser73 on 2009-02-17
I agree with those who have mentioned Deluge, it's far better than Transmission and Azureus/Vuze.

---

### Post by mixmaster on 2009-02-17
In my admittedly limited experience the major performance issues with torrents lies upstream.  However, I suppose that it is different if you are taking something popular with a lot of seeds.  Generally I'm lucky to find more than one donor.

---

### Post by handy on 2009-02-17
I use Transmission on OSX, Arch, FreeNAS & Sabayon, it is great & is continually being updated; the Transmission team is always busy making it better.

---

### Post by simtaalo on 2009-02-17
KTorrent is what you need, never used anything faster.

---

### Post by Insane_Homer on 2009-02-17
I like the function of Deluge and interface is similar to Azureus.

Download speed don't seem any slower than anything else I've used.

---

### Post by Archmage on 2009-02-17
I simply can't understand, why no one suggested rtorrent. This runs perfect on a headless server, because it is a comando-line tool. Together with the tool screen you'll find out that it use nearly no recources, while giving you all the things you need.

Downside is, that you might read and congfigurate it a little.

---

### Post by gimcrack on 2009-02-17
Deluge and Transmission are great torrent clients. Both are fast, I'm using Transmission, it's faster with my machine setup. Try both, mess with the settings, find out which one is faster for you. My Transmission, was slow at first, but after a few downloads, It pick-up speed. So give both a try, with at least 4 downloads to see which one is faster with your set up.

---

### Post by rudy.elgato on 2009-02-17
so what exactly is fast?  

don't mean to sound so stupid or anything, but I'm pretty new to torrents and all that.  I'm using transmission simply because it came default with 8.04.1, and the few 700MB avi movies I've downloaded have taken between 3-4 hours.  Is this slow, fast, typical download time?  I know alot depends on seeds, peers, my connection, and all that, but 3 to 4 hours for a 700MB avi is what I regularly run.

Thanks...

---

### Post by lvleph on 2009-02-17
Any torrent client set up properly will (should) have the same speed. It is all about overhead and features.

To determine your max download rate I have found using the following formula helpful.
s = a/8 * 0.95
where is s is the speed in MB/s and a is the advertised speed in Mb/s.
So for me, I have a 20Mb/s line.
s = 20/8 * 0.95 = 2.375MB/s
I typically max out at 2.4 MB/s
for upload I do a similar calculation to determine max speed I should up at.
s = a/8*0.8
so again for my connection of 10Mb/s
s = 10/8*0.6 = 0.75MB/s or 768KB/s
I just round up to 800KB/s.

@rudy.elgato
I would say that is slow. I can get 700MB in about 5 mins.

---

### Post by handy on 2009-02-17
> **Archmage said:**
> I simply can't understand, why no one suggested rtorrent. This runs perfect on a headless server, because it is a comando-line tool. Together with the tool screen you'll find out that it use nearly no recources, while giving you all the things you need.

Downside is, that you might read and congfigurate it a little.

I agree, rtorrent is a great resource, most people don't want to play like that though.

Here is a great how-to for setting up an rtorrent slave:

*_[http://kmandla.wordpress.com/2008/08/04/case-in-point-an-rtorrent-slave-setup/](http://kmandla.wordpress.com/2008/08/04/case-in-point-an-rtorrent-slave-setup/)_*

---

### Post by Crafty Kisses on 2009-02-17
Transmission or Deluge.

---

### Post by handy on 2009-02-17
> **rudy.elgato said:**
> so what exactly is fast?  

don't mean to sound so stupid or anything, but I'm pretty new to torrents and all that.  I'm using transmission simply because it came default with 8.04.1, and the few 700MB avi movies I've downloaded have taken between 3-4 hours.  Is this slow, fast, typical download time?  I know alot depends on seeds, peers, my connection, and all that, but 3 to 4 hours for a 700MB avi is what I regularly run.

Thanks...

A BIG problem with torrents, is that they are so dynamic, there are ISP, server hops, the number of seeds, the speed that the seeds are seeding.  Because of these variables people get all in a fuss about which torrent client is the fastest, when in reality I don't think that these days there really is much between them at all.

Find one that you are comfortable with, that does everything you require & be patient: Sometimes it can take a week for something to completely download, another time the same thing will be in, in a couple of hours.  

Dynamism is like that. :p

---

### Post by rudy.elgato on 2009-02-18
@Ivleph - So you're able to download 700MB in 5 minutes???  Wow... That's crazy fast...


To the rest of you out there, just out of curiousity, how long does it typically take you to download something 700MB in size?  I'm using 700MB because that's the size of the couple of full length movies I've downloaded already.  


Totally understand the dynamism of using torrents, but after a few times, think 3-4 hours for a 700MB movie is what I get right now.

---

### Post by mister_p_1998 on 2009-02-18
I like Ktorrent for its scheduling & ipfilter options.

---

### Post by lukjad on 2009-02-18
I hear that rtorrent is one of the lightest torrent clients out there. I personally find that Ktorrent is the best for me.

---

### Post by handy on 2009-02-18
> **lukjad007 said:**
> I hear that rtorrent is one of the lightest torrent clients out there. I personally find that Ktorrent is the best for me.

I tried Ktorrent in the past but it was unstable, it kept crashing on me?

Hopefully they have fixed that problem.

---

### Post by lukjad on 2009-02-19
@handy  
I've had my issues with it. If you know of a better one, please share.

---

### Post by Yellow Pasque on 2009-02-19
> **Archmage said:**
> I simply can't understand why no one suggested rtorrent.
Probably because most people aren't using headless boxes.

---

### Post by simtaalo on 2009-02-19
Ktorrent has been the fastest torrent client i've ever used.

my net connection tested as this

[[IMG]http://www.speedtest.net/result/414275199.png[/IMG]](http://www.speedtest.net)

with good seeds on Ktorrent i can get a 700mb file in 20-30mins

---

### Post by mb_webguy on 2009-02-19
> **rudy.elgato said:**
> @Ivleph - So you're able to download 700MB in 5 minutes???  Wow... That's crazy fast...


To the rest of you out there, just out of curiousity, how long does it typically take you to download something 700MB in size?  I'm using 700MB because that's the size of the couple of full length movies I've downloaded already.  


Totally understand the dynamism of using torrents, but after a few times, think 3-4 hours for a 700MB movie is what I get right now.

I have Deluge set at 250 KiB/s download and 25 KiB/s upload (which is about 85% of my total bandwidth, so I don't have problems streaming video in my web browser while downloading torrents).  With good seeds, I can get a 700MB file in about 45 minutes, but on average it probably takes more like 2 hours.

---

### Post by abhilashm86 on 2009-02-19
i've been using transmission bit torrent untill now:) when seeders are more,there is no problem for me,now seeing people opinion i'm giving Delgue a try:)

---

### Post by handy on 2009-02-19
> **lukjad007 said:**
> @handy  
I've had my issues with it. If you know of a better one, please share.

I'm boring, as I'm quite happy with Transmission.  It does everything I want it to, & at times when all of the external variables are right it will max out my 1500/256 bandwidth (if I let it).

I have a [*_FreeNAS_*]("http://www.freenas.org/") box, & FreeNAS now supports Transmission .torrents as a service, & it is possible (though not easy) to even make FreeNAS a .torrent slave with a shared /watch folder which you access from your workstation/client, this enables you to be able to just drop *.torrent files into the shared /watch directory & FreeNAS will take control of the situation, to the point that you can shut down your workstation/client & FreeNAS will continue doing whatever it must with the .torrent(s) whilst you sleep.

I like it.

But I have only gone so far with the set up, which is quite tedious at this stage. ;)  Though everything else regarding the installation & set up of FreeNAS is first class & not time consuming or difficult at all.  & take it from me, I'm no Linux wiz'. lol

---

### Post by peakshysteria on 2009-02-20
**Vuze 4.1.0.0** is by far the fastest and most stable client on my system.

---

### Post by joey-elijah on 2009-02-20
> **rudy.elgato said:**
> @Ivleph - So you're able to download 700MB in 5 minutes???  Wow... That's crazy fast...


To the rest of you out there, just out of curiousity, how long does it typically take you to download something 700MB in size?  I'm using 700MB because that's the size of the couple of full length movies I've downloaded already.  


Totally understand the dynamism of using torrents, but after a few times, think 3-4 hours for a 700MB movie is what I get right now.

On Ubuntu a popular 700mb file will take around 3/4 hours, sometimes longer in deluge. Slower than that in Transmission. ktorrent is just ugly and gives me no noticable speed boost over transmission. 

In Windows using utorrent the same file will take just over an hour or so on a 2MB connection.

In OS X using transmission, again, something like 1/2 hours.

I've tweaked and poked etc to try and get better speeds in Ubuntu, but alas.

---

### Post by rudy.elgato on 2009-02-25
Great...  I went ahead installed Deluge, have used it a few times and the same ~700mb avi downloads that were taking between 3-4 hours using Transmission take just under 1 hour with Deluge.  I know, I know, things are different at different times, dynamism and all that, but this seems like a pretty significant difference.  And, since I've run into the same numbers several times, I'd say, at least in my environment, Deluge is much, MUCH faster then Transmission.

---

### Post by APNelson.L on 2009-02-25
> **lvleph said:**
> Any torrent client set up properly will (should) have the same speed. It is all about overhead and features. 

I agree with this and I am a big utorrent fan. It is fairly easy to set up with wine and works well. I have tried messing around with transmission and still use it a little but I think utorrent is one of the easiest and most friendly clients available. It is also a very small program that doesn't require a lot of resources to run.

---

### Post by handy on 2009-02-25
*_[http://ubuntuforums.org/showpost.php?p=6752761&postcount=18](http://ubuntuforums.org/showpost.php?p=6752761&postcount=18)_*

---

### Post by MedianMajik on 2009-02-25
If you want the best performance on your Ubuntu server use rTorrent.  It'll run even after your GUI crashes and is accepted on every tracker I've ever seen (only client I can say that about).  uTorrent under Wine works well, but uses more resources.  I've used Deluge for the last year and it has given me trouble (I'm currently dealing with it on another thread).  If you want stability/light use rTorrent or uTorrent

---

### Post by jarrah-95 on 2009-10-05
i have vuze and deluge and dont realy use them much but for the last ubuntu release i downloaded it with free download manager in windows (i no windows) but i did that (650mb) in about 30 mins

---

### Post by HiImTye on 2009-10-05
I use (and love) kTorrent. it's worked the best/fastest consistently so far of anything I've tried. 700ish MB movie takes 20-30 minutes to download, if I download a couple at once it's about an hour for two (it seems to only download two at a time, starting the next one as the first one finishes but continually scraping the other torrents)

---

### Post by suniyo on 2009-12-31
I've a strange problem related to bittorrent client and disk usage analyzer, can anyone help it out here? have a look at it: [http://ubuntuforums.org/showthread.php?t=1368711](http://ubuntuforums.org/showthread.php?t=1368711)

I don't have DVDs right now to burn the data and 1 GB can save me for this weekend. Anyone out there?

---

