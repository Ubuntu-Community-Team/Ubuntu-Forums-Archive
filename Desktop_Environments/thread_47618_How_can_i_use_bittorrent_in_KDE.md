---
title: "How can i use bittorrent in KDE?"
date: 2005-07-09
forum: Desktop Environments
---

### Post by André on 2005-07-09
Hi everbody,

which KDE applications would be nice to handle bittorrent files?

A great thing would be if i can integrate that app in konqueror somehow so i just click the link and i am ready to go ;-)

Greetings
André

P.S.: I would like to try this page out [http://www.jamendo.com/](http://www.jamendo.com/)

Btw. when i click on listen to MP3 my kaffeine plugin starts and tells me that it can't handle that type. Is there a way to listen to MP3s via kaffeine??

---

### Post by t2kburl on 2005-07-09
sounds like you need to add a couple of packages...

sudo apt-get install azureus

sudo apt-get install lame

see [http://ubuntuguide.org/](http://ubuntuguide.org/) for more

---

### Post by jeremy on 2005-07-09
Azureus, here are instructions: [http://ubuntuguide.org/#azureus](http://ubuntuguide.org/#azureus)

---

### Post by dejitarob on 2005-07-09
If the torrents are still not opening up with Azureus, right click on one already downloaded, open with, other, internet, azureus.

---

### Post by ecadre on 2005-07-09
I installed Bittornado from the repositories and then associated torrent files with Bittornado.

Now, when I click on a link in Konqueror, or on a torrent file when Konqueror is being used as a file browser, the Bittornado client opens up and handles the file.

Simple  :)

---

### Post by André on 2005-07-09
Hehe,

thanks for all the quick answers. Seems like everbody (beside me!) knows how to do it :-)

Thanks again
André, who is trying your suggestions

---

### Post by André on 2005-07-10
Hi,

i am still trying to get the MP3 stream to work.

It opens kaffeine and says it can't find the right plugin. Any ideas?

Greetings
André

//edit: This is the error i get

xine: couldn't find demux for >http://www.jamendo.com/index.php?f=mp31&id=139&m=playlist&t=album<
input_http: content length = 524 bytes
xine: found input plugin : http input plugin
xine: cannot find input plugin for MRL []
xine: couldn't find demux for >http://www.jamendo.com/index.php?f=mp31&id=139&m=playlist&t=album<
input_http: content length = 524 bytes
xine: found input plugin : http input plugin

---

### Post by apokryphos on 2005-07-12
KTorrent is coming out soon (rc2 is currently out) which is planned to integrate with kget. It's pretty buggy at the moment, but works to an extent. Best off with azureus at the moment.

Qtorrent is also out there.

---

### Post by Jonathan2007 on 2005-07-13
What is the difference between Qtorrent and Bittornado? In Synaptic it says that Qtorrent uses Bittornado so I don't see the difference?

To get mp3's to play I believe you need the w32codecs package. Open a terminal and type sudo apt-get install w32codecs or you can open Synaptic and use it to install the w32codecs package.

EDIT: See [http://ubuntuguide.org/#codecs](http://ubuntuguide.org/#codecs)
You may also have to add some repositories to be able to find the w32codecs package.

---

### Post by SGC on 2005-07-13
[QUOTE=Jonathan2007]What is the difference between Qtorrent and Bittornado? In Synaptic it says that Qtorrent uses Bittornado so I don't see the difference?
[/QUOTE]
Qtorrent have a better interface than Bitornado since it uses QT widgets, and alllows you to have several torrents open at the same time from within the same program window.

**Also g3torrent is a nice bittorerent client, its available in the backports repositoy:**
sudo apt-get install g3torrent

---

### Post by bored2k on 2005-07-13
[QUOTE=SGC]Qtorrent have a better interface than Bitornado since it uses QT widgets, and alllows you to have several torrents open at the same time from within the same program window.

**Also g3torrent is a nice bittorerent client, its available in the backports repositoy:**
sudo apt-get install g3torrent[/QUOTE]
 If only g3 utilized the latest engine and had DHT tracker support..

---

### Post by Jonathan2007 on 2005-07-13
[QUOTE=bored2k]If only g3 utilized the latest engine and had DHT tracker support..[/QUOTE]
Does QTorrent have the latest engine and DHT tracker support? And I thought that G3Torrent has been banned from a lot of torrent sites because it allows too much leaching or something like that.  :?

---

### Post by bored2k on 2005-07-13
[QUOTE=Jonathan2007]Does QTorrent have the latest engine and DHT tracker support? And I thought that G3Torrent has been banned from a lot of torrent sites because it allows too much leaching or something like that.  :?[/QUOTE]
 I don't think so. Last version came out in 2k4 I think.

Banned g3? I believe so too.

---

### Post by Jonathan2007 on 2005-07-13
hey thanks for the super fast response. Do you know of any other Linux torrent programs? I have Azureus but I am not a huge fan of it. I would like something similar to BitComet on Windows. I loved that program. It was tons better than Azureus imo. I looked at ABC for Linux awhile ago and it didn't look too bad except their windows version was a lot newer. 

How do I open Gtorrent now. I installed it but it didn't get automatically entered into my Kmenu.

---

### Post by bored2k on 2005-07-13
[QUOTE=Jonathan2007]hey thanks for the super fast response. Do you know of any other Linux torrent programs? I have Azureus but I am not a huge fan of it. I would like something similar to BitComet on Windows. I loved that program. It was tons better than Azureus imo. I looked at ABC for Linux awhile ago and it didn't look too bad except their windows version was a lot newer. 

How do I open Gtorrent now. I installed it but it didn't get automatically entered into my Kmenu.[/QUOTE]
 Try running g3torrent from a terminal ?

Well, In Linux there are 3 mayor players: Azureus, Bittorrent official and Bittornado. I favor teh first two. Sadly, Azu is the most advanced or at least the most tweak friendly of the three.

---

### Post by Jonathan2007 on 2005-07-13
You like the original BT over Bittornado? The original doesn't even have a upload setting does it?

I tried your suggestion about running it throught run but you told me to run g3torrent and I had downloaded qtorrent so i put that in instead and it ran. But I don't really like it. I wish someone would port BitComet. I may look into ABC though as it looked pretty good.

---

### Post by bored2k on 2005-07-13
[QUOTE=Jonathan2007]You like the original BT over Bittornado? The original doesn't even have a upload setting does it?

I tried your suggestion about running it throught run but you told me to run g3torrent and I had downloaded qtorrent so i put that in instead and it ran. But I don't really like it. I wish someone would port BitComet. I may look into ABC though as it looked pretty good.[/QUOTE]
 Yes I like BT over Bittornado. Apparently you have not seen the latest version of BT. It's compiled on GTK2 and is arguably the most beautiful and the one that integrates the most with your themeing. And yes, It has UL settings and a few more. It is really nice.

[CENTER][[IMG]http://img192.echo.cx/img192/7272/official9wt.th.png[/IMG]](http://img192.echo.cx/my.php?image=official9wt.png)[/CENTER]

---

### Post by SGC on 2005-07-13
Board2k, did you know of any client other than Azureus that let you select which files you want to download from multi-file torrent.

---

### Post by bored2k on 2005-07-13
[QUOTE=SGC]Board2k, did you know of any client other than Azureus that let you select which files you want to download from multi-file torrent.[/QUOTE]
 Bitcomet. Bittornado. Me not knowing them all, those are the ones I've seen the possibility.

It's bored, not board.

---

### Post by SGC on 2005-07-13
[QUOTE=bored2k]Bitcomet. Bittornado. Me not knowing them all, those are the ones I've seen the possibility.

It's bored, not board.[/QUOTE]
 Sorry for misspelling your name. 

Does Bitcomet works on linux?

---

### Post by bored2k on 2005-07-13
[QUOTE=SGC]Sorry for misspelling your name. 

Does Bitcomet works on linux?[/QUOTE]
 Nope. If tried to get it running through Crossover Office Pro, but I keep getting errors about some packages from microsoft.com that need to be installed but don't want to install at all.

---

### Post by SGC on 2005-07-13
[QUOTE=bored2k]Nope. If tried to get it running through Crossover Office Pro, but I keep getting errors about some packages from microsoft.com that need to be installed but don't want to install at all.[/QUOTE]
 Thanks for your reply, I think I will stick with Azureus until ktorrent supports this feature.

---

### Post by bored2k on 2005-07-13
[QUOTE=SGC]Thanks for your reply, I think I will stick with Azureus until ktorrent supports this feature.[/QUOTE]
 Okie dokie.

Rock on.

---

### Post by pt123 on 2005-07-13
[QUOTE=SGC]Sorry for misspelling your name. 

Does Bitcomet works on linux?[/QUOTE]

I wish it did, so I currently use bit Tornado its a lot faster. It had a manager utility, so when I start it remembers the otrrents thats I was downlaoding.

Azerues is horrendous its a control freak it ruins all the part downloaded files, so that you cant use other torrent programs with them. I also get slow speeds with it.

---

### Post by bored2k on 2005-07-13
[QUOTE=pt123]I wish it did, so I currently use bit Tornado its a lot faster. It had a manager utility, so when I start it remembers the otrrents thats I was downlaoding.

Azerues is horrendous its a control freak it ruins all the part downloaded files, so that you cant use other torrent programs with them. I also get slow speeds with it.[/QUOTE]
 You can't really say azureus is horrendous. It's not my favorite, but it's good. It's advance and highly tweakble. I wish it was written in c++ like bitcomet or python, but heh, that's that. It's DHT tracker capabilities and the fact that it supports everything you throw at it gracefully (udp, azureus embedded trackers, etc) is just great.

---

### Post by pt123 on 2005-07-14
[QUOTE=bored2k]You can't really say azureus is horrendous. It's not my favorite, but it's good. It's advance and highly tweakble. I wish it was written in c++ like bitcomet or python, but heh, that's that. It's DHT tracker capabilities and the fact that it supports everything you throw at it gracefully (udp, azureus embedded trackers, etc) is just great.[/QUOTE]
 I hate programs that try to overtake your data files, reminds of M$ & itunes.

---

