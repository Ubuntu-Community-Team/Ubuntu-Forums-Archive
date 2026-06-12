---
title: "Why ubuntu can't take the stress?"
date: 2009-05-19
forum: General Help
---

### Post by Lockheed on 2009-05-19
This is what I had running at my 2GB ram/Turion X2 1.6GHz:
- totem playing a digital stream
- Breaser burning a 150mb ISO image
- VirtualBox with idling XP with TheBat and some IM
- Opera with 5 tabs and downloading a file at 200kb/s
- Tucan downloader downloading 4-6 files from rapidshare, each at ~200kb/s
- Utorrent under Wine
- CheckGmail opening FireFox with new email

and Ubuntu just lost it! Sound was totally chopped (a few seconds of sound, 5 seconds of silence), mouse was moving 1cm per 5 seconds.
I couldn't do anything, so I tried to close some apps. No luck, nothing happened.
Eventually, after 10 minutes of waiting for the system to unclog, I decided to hit the power button. That was not the first time something like that happened.

Why is it so easy to stall Ubuntu? When I do those things (and many more) in XP or 7, the computer is still very usable!

---

### Post by wsonar on 2009-05-19
I have sites or network lag sometimes really stall me out till I force quit firefox

could be a compiz issue tho

I usually alt f2 and xkill whatever is stalling

---

### Post by paradigm2 on 2009-05-19
It may be okay in XP, but in Ubuntu you are using WINE for utorrent and then also using virtualbox with an instance of XP.  There's a big difference. You're almost running 2.3 (Ubuntu, XP, and wine -- the .3 as it isn't technically an OS though it is resource intensive somewhat) Operating systems there!

Next time you get this level of load, open a terminal and do 'top' and let us know what it says as far as cpu and memory use.

---

### Post by SentientFluid on 2009-05-19
How much RAM CPU did you assign your VirtualBox for XP? Even though XP may have been idling, whatever you assigned to the VM will not be available for Ubuntu.

---

### Post by zenithdave on 2009-05-19
I think your test is ridiculous !

---

### Post by Lockheed on 2009-05-19
> **paradigm2 said:**
> It may be okay in XP, but in Ubuntu you are using WINE for utorrent and then also using virtualbox with an instance of XP.  There's a big difference. You're almost running 2.3 (Ubuntu, XP, and wine -- the .3 as it isn't technically an OS though it is resource intensive somewhat) Operating systems there!

Next time you get this level of load, open a terminal and do 'top' and let us know what it says as far as cpu and memory use.

When the host is XP or Windows 7, I also run 1-2 virtual machines using VMware which is more heavy on the resources than VirtualBox.

Also, I cannot type 'top' in the terminal, cause I can click away on the icons (after a minute of torment placing the cursor) but nothing happens.

> How much RAM CPU did you assign your VirtualBox for XP? Even though XP may have been idling, whatever you assigned to the VM will not be available for Ubuntu.
200MB for XP. I am not aware of any CPU settings.


> I think your test is ridiculous !
That was not a test. That was everydays use of windows poweruser.

---

### Post by wsonar on 2009-05-19
why use utorrent when transmissionBittorrent is built in?

then you wouldn't need to use WINE

---

### Post by themusicalduck on 2009-05-19
Slight stab in the dark but maybe you could check if your swap space is working? I had a problem that sounds much like this when my swap wasn't being mounted properly and my computer died whenever I tried to open XP in a VM.

---

### Post by steveneddy on 2009-05-19
> **zenithdave said:**
> I think your test is ridiculous !

:)

---

### Post by Lockheed on 2009-05-19
> why use utorrent when transmissionBittorrent is built in?

Because contrary to what some linux guys like to say, there are some windows programs that have no worthy linux replacement. From the top of my head here's a few:
- uTorrent
- TheBat
- MirandaIM

> Slight stab in the dark but maybe you could check if your swap space is working? I had a problem that sounds much like this when my swap wasn't being mounted properly and my computer died whenever I tried to open XP in a VM.
I don't think that's the case. Taks Manager (or whatever it's called) can see the swap alright.

---

### Post by paradigm2 on 2009-05-19
> **Lockheed said:**
> When the host is XP or Windows 7, I also run 1-2 virtual machines using VMware which is more heavy on the resources than VirtualBox.

Also, I cannot type 'top' in the terminal, cause I can click away on the icons (after a minute of torment placing the cursor) but nothing happens.


200MB for XP. I am not aware of any CPU settings.



That was not a test. That was everydays use of windows poweruser.

The problem could be any one of these applications.  In order to answer your question we need more data.  I would try top again right before it gets that bad.  Before it hits the threshold.

---

### Post by NCLI on 2009-05-19
Is this the PC you do it with:
> Compaq 6065ea: Turion X2 1.6G, 4GB ram, GF go6150. 
Wow. O.o

---

### Post by Lockheed on 2009-05-19
Almost. I have 2GB RAM right now. I plan to upgrade to 4GB tomorrow.
In Windows 7 64bit this computer almost doesn't break a sweat under even heavier stress. I will try 'top' next time it happens.


By the way - what's wrong with Flash? I did quite a lot of trick I found here to enable sound in it and I succeded. 
However, most of the time, even when only the browser is running, the playback is extremely choppy (picture, not the sound) and half of the time there is no sound (for no visible reason).

---

### Post by evermooingcow on 2009-05-19
> **Lockheed said:**
> Because contrary to what some linux guys like to say, there are some windows programs that have no worthy linux replacement. From the top of my head here's a few:
- uTorrent
- TheBat
- MirandaIM


I don't think that's the case. Taks Manager (or whatever it's called) can see the swap alright.
Have you tried deluge for a torrent client? The UI is almost identical to utorrent. It has networking options that reflect a unix environment (e.g. uncapped half-open TCP connections) and also has added functionality to run as a daemon on a CLI server with remote a GUI frontend.

The one thing I still use wine for is foobar2000. I have yet to find a linux music player that can handle cue sheets *properly*.

Also I think your machine should be enough to handle what you're doing. Maybe there is something wrong with your install or config.

I sit around 800MB RAM used running:

2-3 instances of FF with multiple tabs open on each
XP VM with 256MB RAM allocation
foobar2K on wine
htop
ncmpcpp+mpd
mplayer 1920x1080 video
lots of urxvt

Surely 2GB is enough. The CPU though does see high load with the 1080 video playing.

---

### Post by Lockheed on 2009-05-19
Ah, yes, of course! I forgot foobar2000! Awesome app.
I haven't tried it on wine yet. Did you have any problems?

As for torrent - I did not try anything else but I read quite a lot threads on utorrent vs various linux clients and general conclusion was that wine+utorrent is by far the best torrent option.
Does any linux client have RSS downloads? This feature is crucial for me. Also, small footprint is always nice.


As for the load - is it still important to compile your own kernel? Few years back when I was trying RedHat, Slackware and some other distros, it always was no1 step so that the system can perform to it's best.

---

### Post by evermooingcow on 2009-05-19
Ah I see. AFAIK deluge doesn't do RSS - at least not up to v1.1.7 that I've tried. That is one thing I miss from utorrent.

I ran into one problem with foobar2000 and that was sample rate conflict. The default sampling rate for alsa playback on my box was 48KHz and foobar/wine was trying to play at 44.1KHz which resulted in noticeable distortion.

This was how I fixed the problem:
1. Set wine output to 48KHz
2. Activate resampler in foobar DSP and set the output to 48KHz.

You could also write up a .asoundrc config to specify 44.1KHz output (probably the cleaner solution) but that was too much pain for me.

---

### Post by kostkon on 2009-05-20
> **Lockheed said:**
> As for torrent - I did not try anything else but I read quite a lot threads on utorrent vs various linux clients and general conclusion was that wine+utorrent is by far the best torrent option.
Also, small footprint is always nice.
The best option is Deluge, I believe. I would recommend you to give it a try and download the latest [from its site]("http://deluge-torrent.org"), or you can even add [its PPA]("https://launchpad.net/~deluge-team/+archive/ppa") and you'll get an automatic update every time there is a new version.
> **Lockheed said:**
> Does any linux client have RSS downloads? This feature is crucial for me.
> **evermooingcow said:**
> Ah I see. AFAIK deluge doesn't do RSS - at least not up to v1.1.7 that I've tried. That is one thing I miss from utorrent.
It does, you just need to download the plugin from [here]("http://dev.deluge-torrent.org/wiki/Plugins").

---

### Post by Lockheed on 2009-05-20
Alright, thanks for the heads-up on the torrent subject.

I think I found the culprit of the slowdown/crash - I was unpacking rarred movie with WinRar (NTFS partition), run thebat in VirtualBox XP (TheBat is on mounted shared drive - ntfs), utorrent (downloading files to NTFS partition) and some other smaller programs. Everything was fine until I saw new email notification in CheckGmail. I then clicked it and everything went to hell. 
Firefox (which I dislike anyway - I'm an opera guy) started to open but the outcome was identical as the previous time. I had to kill the computer after 15 minutes of waiting.

Before I did that, I somehow managed to 'top'. CheckGmail/FireFox had some serious proc usage but then it changed to VirtualBox using 70% of cpu amd ntfs-3g also in the top 3.

Now, what can we work out from this set of data? I know relaying so heavily on ntfs is slowing me down but I have to do it at least for some time until I can "fully" migrate. So, what can I use for gmail notification and what would be a light-weight browser I'd use just for this purpose? In windows, I loved Chrome for that, cause I could make it work as a separate gmail program (here: [http://www.google.com/support/chrome/bin/answer.py?answer=96824](http://www.google.com/support/chrome/bin/answer.py?answer=96824) ), not as a browser. Is there anything comparable under linux?

---

### Post by mb_webguy on 2009-05-20
> **kostkon said:**
> The best option is Deluge, I believe. I would recommend you to give it a try and download the latest [from its site]("http://deluge-torrent.org"), or you can even add [its PPA]("https://launchpad.net/~deluge-team/+archive/ppa") and you'll get an automatic update every time there is a new version.


It does, you just need to download the plugin from [here]("http://dev.deluge-torrent.org/wiki/Plugins").

Actually, you can download it [here]("http://forum.deluge-torrent.org/viewtopic.php?f=9&t=10185") if you're using a recent release of Deluge (which I much prefer in a Linux environment over uTorrent under Wine, though I'm a big fan of uTorrent on Windows).  The newer versions of Deluge are great, but because they've changed the scripting API for v1.0, plugins that were available for earlier releases haven't necessarily been ported to the new versions yet.

---

### Post by baseface on 2009-05-20
your little performance test whatever the hell u want to call it is retarded.
first of all, post the output of ```
ps aux
```
theres probably well over 100 processes already running and sucking up resources. learn how to configure your system and it will perform better.

---

### Post by Mirge on 2009-05-20
> **baseface said:**
> your little performance test whatever the hell u want to call it is retarded.
first of all, post the output of ```
ps aux
```theres probably well over 100 processes already running and sucking up resources. learn how to configure your system and it will perform better.

"Before I did that, I somehow managed to 'top'. CheckGmail/FireFox had some serious proc usage but then it changed to VirtualBox using 70% of cpu amd ntfs-3g also in the top 3."

He ran top and said what the resources hogs were. And no, it's not a "performance test", but he IS trying to learn how to configure his sytem and/or debug the problem... hence he's here asking. No need to be so rude, imo.

---

### Post by Lockheed on 2009-05-21
Thanks, Mirage. You beat me to it.

As for performance and configuration - is it still important to compile your own kernel? Few years back when I was trying RedHat, Slackware and some other distros, it always was no1 step so that the system can perform to its best.

---

### Post by Lockheed on 2009-05-24
How is it that every time I ask about kernel compilation, the thread dies? :)

---

### Post by DeMus on 2009-05-24
> **baseface said:**
> your little performance test whatever the hell u want to call it is retarded.
first of all, post the output of ```
ps aux
```
theres probably well over 100 processes already running and sucking up resources. learn how to configure your system and it will perform better.

Maybe you hadn't notice it yet, since you only joined this month, but this is a forum where people with problems ask questions on how to solve them. So if somebody has a problem and he/she thinks to do this or that to get more information about it, don't start yelling. Most people here are newbies to Linux and want to learn. Since Linux is not Windows (with which they grew up with) it is all different. So they ask questions. If you want to help, fine. If not, shut up.

---

### Post by niteshifter on 2009-05-24
Hi,

Ok, you've got swap turned on. But what kind of swap and how much? This is critical.

```
cat /proc/swaps
```
will reveal what kind of swap.

```
free
```
will reveal how big the swap space is.

Swap space can be a had from a file or a device (dedicated partition). Swap via file is slower than a dedicated partition. A swap file with "holes" (non-contiguous) is the absolute pits of performance.

Now the fun-to-discuss part: Swap size. Some folks manage to get by with no or an undersized swap - plenty of posting about that here in this forum. These folks are lightly tasking their machines. You are not. I'm a heavy user of virtualization. We need fast swap and plenty of it.

I can make this machine (see sig) perform as your's is: all I have to do is turn off swap. Performance with multiple apps goes right down the tubes. Virtual machines get cranky.

I run - with 2GB of physical RAM - a 4GB swap. I can have my XP VM (1GB RAM), my Solaris VM (another 1GB RAM) up and running, be listening to music (Audacious on the Host OS), have FF open (in the Host) etc. with a slight degradation in performance.

Throwing my FreeBSD VM (non-GUI, but also 1GB RAM) or Fedora (also 1GB) on top of the above ... that doesn't work so well. 

You indicate you are about to double on RAM. For 4GB and your usage pattern, consider setting your swap partition size to a minimum of 6GB, 8 would be better, 10GB may get you a tiny bit better performance over 8GB. More is just a waste of disk space.

---

### Post by Lockheed on 2009-05-26
Thanks for the suggestions. Here is the printout from the commands you recommended:
```
sudo cat /proc/swaps
Filename				Type		Size	Used	Priority
~$ free
             total       used       free     shared    buffers     cached
Mem:       3850908    3826692      24216          0     999684    1173724
-/+ buffers/cache:    1653284    2197624
Swap:            0          0          0

```

I don't know why it shows swap at 0 since it is 1GB and Process Manager also detects 1gb.

I do have 4GB RAM now but I am not a big fan of large swap files. In fact, on Windows I had it off with 2gb and surely would have it off with 4GB of ram.

Having said that, I need to point out that the problem seemed to have been elsewhere. Since I changed association of CheckGmail from FireFox (which btw I hate:-$) to Swiftfox, the problem never reocurred. Looks like I got one more reason for not using FF.

---

### Post by jmszr on 2009-05-26
Lockheed,

When you set up your swap did you give it it's own partition? In other words, do you have a "swap" or a "/swap" ? If you have a "/swap" this thread may be of help:[http://ubuntuforums.org/showthread.php?t=1146548](http://ubuntuforums.org/showthread.php?t=1146548) .

---

### Post by Lockheed on 2009-05-26
Yes, my swap is on separate partition which is 1GB of size.

---

### Post by jmszr on 2009-05-26
Lockheed,

You will need to remove the mount point "/" to allow the "swap" to be accessible. The thread in my previous post explains how to do that(I had set up my swap as "/swap" in it's own partition). If you have any questions I will attempt to help you, but you may well need the help of somebody who knows for sure what they're doing.

---

### Post by Lockheed on 2009-05-26
jmszr, thank you for your much-appreciated assistance. 

However, as I said, I have no problems that I can link to my swap nor do I have any premise suggesting the swap is malfunctioning.
The problem I was having was directly related to the combo of CheckGmail executing FireFox. Once I changed FF to something else, the problem never reoccurred. 

It is not to say my system is all good now, because every day I find some new annoyance or malfunction. Nevertheless, they are not linked to this thread&#8217;s theme. Should I ever run into troubles with my swap, I&#8217;ll be sure to use the solution you kindly provided. Still, for now I don&#8217;t think it is called for.

---

### Post by nr0mx on 2009-05-26
> **wsonar said:**
> why use utorrent when transmissionBittorrent is built in?

then you wouldn't need to use WINE

I think this is irrelevant, unless you have proof that wine + utorrent uses way more memory + cpu than transmission. I have used utorrent for a while now. I have had intermittent performance issues on my setup, but utorrent/wine has never been the cause. Just my observation.

---

### Post by Lockheed on 2009-05-26
> **nr0mx said:**
> I have had intermittent performance issues on my setup, but utorrent/wine has never been the cause. Just my observation.

I second that. Plus, uTorrent has RSS feeds which are essential to me. I tried adding RSS plugin to Deluge but failed. Not to mention further inperfections of Deluge in areas where uTorrent just does all I ask it for.

---

### Post by GuiGuy on 2009-05-26
> **zenithdave said:**
> I think your test is ridiculous !

The test may or may not be. The allegation is correct. It is just so easy to bring everything in Ubuntu to a halt. 

Smart hardware, SATA drives. Copy a large file between a couple of drives, watch the show stop.

Poorly written application that are not written to take advantage of multi or hyperthreading, whatever. Case in point, Pan.

Firefox; open a few tabs and again, everything stops. 

I could go on....

---

