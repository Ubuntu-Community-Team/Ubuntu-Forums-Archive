---
title: "Downloading Torrents.. want a faster way in linux?"
date: 2009-01-14
forum: General Help
---

### Post by sendblink23 on 2009-01-14
*I made this for users... who simply have really slow download issues in Torrents through Linux, knowing that through Windows they used to be able download way faster.*


Simple...  Install WINE in your Linux ...  and 
Install **uTorrent**: [http://www.utorrent.com](http://www.utorrent.com)  

Download the one in the Main Page "ver. 1.8.1(263kb) | Windows", afterwards just install it with WINE (right-click "Open with Windows Program Loader"), and guess what it works Faster than it does in Windows, through Linux. 

Hope this helps.. many users I've seen (reading through the forums) having issues of really slow downloads on Torrents using Linux based applications.

Laters

---

### Post by Hangwire on 2009-01-14
Um...

---

### Post by Titan8990 on 2009-01-14
The client usually makes little to no difference in download speed. Most of the time slow downloads are because of:

A) bad network configurations

B) ISPs throttle default torrent ports

---

### Post by sendblink23 on 2009-01-14
> **Titan8990 said:**
> The client usually makes little to no difference in download speed. Most of the time slow downloads are because of:

A) bad network configurations

B) ISPs throttle default torrent ports


I've already tested on many applications that Linux offers, They always went down, on starting downloads.. it was high then like time passes and it goes down. (This is not changing any settings inside your Torrent software, just running the program as-is)

Tested all the same *torrent (Adobe CS4 master Collection - you know its huge) 

On all it happens the same on linux ....  MAX download was 20kbs (Just in case it was all similar same seeders) it has over 200 seeders *Weird how can it be Max Kbs that slow

I was like ok... I guess its normal (if I don't make any changes in the settings)

Suddenly came on my mind.. why not install the same one I used before on Windows, WINE it... there I noticed, I never encountered any speed issues, Max speed 300kbs+   never went down 


Test it out you'll notice the difference - **The Point is not having to make any changes in settings, for faster downloads in linux.**

---

### Post by Titan8990 on 2009-01-14
Could it be possible that utorrent used uPnP and the other clients you attempted did not or you did not configure them to use uPnP?

---

### Post by sendblink23 on 2009-01-14
> **Titan8990 said:**
> Could it be possible that utorrent used uPnP and the other clients you attempted did not or you did not configure them to use uPnP?

I mentioned Using the Program AS-IS, not making any Changes inside the Settings of the program. What does that mean.. then my Fact is correct.

---

### Post by Zack McCool on 2009-01-14
The client software, generally, makes little to no difference.  I use ktorrent, and my average download speed is about 1800 KB/s.  I usually keep this throttled to about 1200 KB/s, and never have a problem.

Your most likely issue is not having the ports properly forwarded on your router.

---

### Post by Titan8990 on 2009-01-14
> I mentioned Using the Program AS-IS, not making any Changes inside the Settings of the program. What does that mean.. then my Fact is correct.

If we didn't want/like configuring our programs to work exactly how we would like them to work, we probably wouldn't be using Linux.

---

### Post by Yashiro on 2009-01-14
This is a funny thread.

---

### Post by sendblink23 on 2009-01-14
> **Zack McCool said:**
> The client software, generally, makes little to no difference.  I use ktorrent, and my average download speed is about 1800 KB/s.  I usually keep this throttled to about 1200 KB/s, and never have a problem.

Your most likely issue is not having the ports properly forwarded on your router.

Read the info... *not making any changes* and Also through my Windows (Dual boot), it runs the same exact Max Speed, of what my Router can pull out.

So what does that mean... it runs the same exact way how it does through windows, when I've already tested downloading many different things on Linux Applications for torrents, it always went down.. after time passes.

Tested: (All from install AS-IS not making any changes in Settings, for more than 3 days each)
Transmission BitTorrent Client
KTorrent
Deluge BitTorrent Client
BitTorrent Download Client
Bittornado Client
BitStormLite


By the way I tested uTorrent for over 3 days just to be certain (i did not make changes on settings, Using it AS-IS from install)

---

### Post by Titan8990 on 2009-01-14
You could have stopped here:

Transmission BitTorrent Client


spent 5min to configure it properly and wouldn't have had to waste the the time to try a handful of other clients.

Try googling something along the lines of "increase torrent speed" and you will see that the client makes no difference.

---

### Post by stefangr1 on 2009-01-14
I have also used different clients (now using Azureus with web-gui on a separate server), but experienced little difference.

It is my subjective estimate that less than 1 per 1'000'000 downloaders will have an average download speed of >= 1800kb/s regardless of the client/operating system used.

Typically, download speed can differ a lot. Even if there are a lot of seeders (like 200), there are often also a lot of downloaders, and speeds can be anywhere from 20kb/s to 500kb/s or (though very rarely) higher.

---

### Post by sendblink23 on 2009-01-14
Here is the thing.. you guys simply don't realize.


The point of installing any software.. its suppose to work as is from new (example out of the box) install as intended.

In other words not as a Programing or Linux *knowledge ... user

As for users who don't know how to configure these sort of programs.

What I did was testing out different programs to notice which ones work by its functionality, with no changes.

Then what I'm suggesting, its the reality, WINE a program is way faster & easier ... and installing uTorrent, you don't have to make any changes, and it works how its intended to be used for.


*I made this for users... who simply have really slow download issues in Torrents, knowing that through Windows they used to be able download way faster.

Think... what's better installing something, that works how its suppose to efficient, without any sort of changes nore anything..  or installing something you have to make changes to work properly how its suppose to?

---

### Post by Titan8990 on 2009-01-14
> 
Think... what's better installing something, that works how its suppose to efficient, without any sort of changes nore anything.. or installing something you have to make changes to work properly how its suppose to?


LOL my main OS is Gentoo. Tell ya anything?

---

### Post by sendblink23 on 2009-01-14
> **Titan8990 said:**
> LOL my main OS is Gentoo. Tell ya anything?

Good for you... this thread is not for you then.

I'm adding in the very beginning: 

*I made this for users... who simply have really slow download issues in Torrents through Linux, knowing that through Windows they used to be able download way faster.*

---

### Post by Buttink on 2009-01-14
Dont you have to compile the kernel yourself for Gentoo? (sorry for being off topic)

And I will say a properly set up router I feel is more importent then the client. But, I do like transmission. XP

---

### Post by Titan8990 on 2009-01-14
> Dont you have to compile the kernel yourself for Gentoo? (sorry for being off topic)

Yes, you do. The install is completely from scratch. You get a liveCD that allows you to download the a tar.bz2 that will become your main filesystem and another that contains the package manage system known as portage. From there, you chroot into your new filesystem, use portage to get a kernel and configure/compile it.

A typical Gentoo installation takes 3-8hrs but nothing beats the customization nor the speed.

---

### Post by jerome1232 on 2009-01-14
The point is your construing miss information, the client has very little to do with speeds, I get consistently high speeds across every torrent client I try with out-of-the-box configurations.

Transmission is probably the best client when it comes to out of the box, it has like three different options you can change! (over exaggeration I know)

---

### Post by TenPlus1 on 2009-01-14
My Deluge install is way faster than when I was using uTorrent...  You just gotta set things up properly and tweak the settings...

---

### Post by hyperdude111 on 2009-01-14
Torrents just seem slow in ubuntu because of the poor time estimation system in transmission, however the actual speed /kbps are not dependent on the client. 

It may intrest you to know that utorrnet and bittorrent are 100% the same EVEN the gui.

---

### Post by mathfreak123 on 2009-01-14
> **sendblink23 said:**
> Here is the thing.. you guys simply don't realize.


The point of installing any software.. its suppose to work as is from new (example out of the box) install as intended.

In other words not as a Programing or Linux *knowledge ... user

As for users who don't know how to configure these sort of programs.


I have rarely installed a program and used it as is without tweaking it at least a little bit. No software is installed and used "as-is", as not everyone has the same purpose for any software.

Also, I have tried a couple bittorrent clients myself, and I always wondered why every single one of them was so slow (including uTorrent). It turns out that I did not forward my ports on my router. Transmission has been just as fast as uTorrent when I had the ports forwarded properly.

---

### Post by adamlau on 2009-01-14
aria2. The one and only :) .

---

### Post by azzamite on 2009-01-14
Azzureus works equally in windows, centos, ubuntu and debian (for me)

Someone was winning about something like that...
so I dissabled iptables and now he's happy.

---

### Post by Sabayon on 2009-01-14
I don't see any difference in the speed.

---

### Post by mwillams73 on 2009-01-15
Ok guys so how do you forward you routers ports? Ive been using transmission for a week now to download a 700 mb fileand I tweaked the settings , its still slower than Bittorrent, it takes 3 days to download the same file with the same peers so why am I still waiting with transmission? I used bitorrent in windows xp and it was consistent with very little configuration on my part, mostly setting where the downloads go, setting the upload speeds, randomizing the ports. thats it ! Now with transmission its been working on this file since the 4th of january and i still have 60 mbs to go, its frustrating when you guys say all you have to do is tweak the settings, I never had to really do anything with bittorrent so how do I get transmission to work right?

---

### Post by hyper_ch on 2009-01-15
> **stefangr1 said:**
> It is my subjective estimate that less than 1 per 1'000'000 downloaders will have an average download speed of >= 1800kb/s regardless of the client/operating system used.
It depends on what you download and what pipe you are on :)

> **sendblink23 said:**
> The point of installing any software.. its suppose to work as is from new (example out of the box) install as intended.
So you never ever changed the background of Windows? Or added additional button in the M$ Word bars?

> **mwillams73 said:**
> Ok guys so how do you forward you routers ports?
[http://portforward.com/routers.htm](http://portforward.com/routers.htm)

---

### Post by mwillams73 on 2009-01-23
I use Bittorrent 6.0.3 using wine and by far it surpasses any thing that linux uses for torrent downloading, Im getting the same results as if I am running it on windows xp, which tells me that its something to do with the torrent downloaders and not the clients, 3 days with bittorrent , 1 week with transmission, I dunno you tell me!!!

---

### Post by chronographer on 2009-01-23
Deluge is great IMHO. It has a webUI which is great if I find a torrent when I'm using my lappy, just open up the webUI and send it over. It also will turn off at 12am and on at 12pm (with a small python script and cron...)

It is very very fast for me, runs at my max speed almost all the time. I also encrypt everything (all settings are set to only accept encrypted stuff) so my ISP hasn't sent me a stop-downloading-torrents letter yet (they sent one to my brother in law recently!)

---

### Post by halovivek on 2009-01-23
i get low speed in ubuntu than windows

---

### Post by hyper_ch on 2009-01-23
I get great speeds on ubuntu using rtorrent

---

### Post by Archmage on 2009-01-23
> **sendblink23 said:**
> I mentioned Using the Program AS-IS, not making any Changes inside the Settings of the program. What does that mean.. then my Fact is correct.

Why are you than using Wine? Use utorrent AS IT IS and don't install addional software for it, if you only want to test the software as it is.

---

