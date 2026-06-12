---
title: "Bad Pulseaudio performance"
date: 2008-12-01
forum: Desktop Environments
---

### Post by Emanuele_Z on 2008-12-01
This post is about Pulseaudio and its *bad performance* with realtime application such as games.

In this case I report what I found out using WoW with wine.
Browsing the web it apperas that the following is valid for everyone playing WoW with wine on ***buntu 8.10.

Acutally I had to remove pulseaudio, because, as Stefan Dosigner pointed out ( [http://www.mail-archive.com/wine-devel@winehq.org/msg42322.html](http://www.mail-archive.com/wine-devel@winehq.org/msg42322.html) ), it is not able to provide direct hardware access, hence a huge FPS drop when the process (pulseaudio) is running.

For example I was running all MAX (but no AA and normal shadows) in Grizzly Hills* and my FPS were:
with PA process running: 18
without PA process running: 28
As you can easily notice the game isn't playable with 18 FPS but is with 28 FPS.

After that I tested it another time and everything was confirmed again.
So I just uninstalled PA.

Now the FPS is even slightly better than 8.04.

my hardware is:
nVidia 8600 GT Mobile 512
Intel Core Duo T7700
2GB RAM
my screen resolution is:
3600x1280 (got 2 screens)
my WoW window resolution is:
1920x1280 (full HD)
the graphics are maxed out but no AA and no fancy shadows.

Maybe my FPS loss is more noticeable than other configs because in my case the game suddenly became from playable to unplayable.
Other people with better hardware than me actually report FPS drop as well, but probably less noticeable because of better hardware and actually higher average FPS ( a drop from 50->40 or from 40->32 is less noticeable than 28->18 ).

What I'd like to point out is:
***Considering that a lot of people is switching to Ubuntu (Linux) because finally some games can be played on it, why was pulseaudio included by default with 8.10?***
I don't want to sound harsh but actually I think that those things should be taken into account when releasing a new version of Ubuntu. Given the particular timeframe I really would put an emphasis on this type of things, because, once gamers will be confident with Linux, this would dramatically increase the Linux base.

What do you think?

Regards,

* Grizzly Hills is a WoW area full of polygons where the hardware gets stressed a lot.

*note*
Would be kinda easy for the average Joe to disable/uninstall pulseaudio? Imho no. That's why I'm posting this.

---

### Post by fraterm on 2008-12-01
Probably better to recommend this: 

[http://ubuntuforums.org/showthread.php?t=866965](http://ubuntuforums.org/showthread.php?t=866965)

To see if that helps

I have similar problems with eve-online and wine interacting horribly with pulseaudio, so hopefully the Ibex gets it's horns polished some more soon.  There needs to be a better delivery of information for major functionality like sound services (and probably less jumping into a new sound server architecture before throrough testing) for ubuntu.  Yarr.

---

### Post by Emanuele_Z on 2008-12-02
> **fraterm said:**
> Probably better to recommend this: 

[http://ubuntuforums.org/showthread.php?t=866965](http://ubuntuforums.org/showthread.php?t=866965)

To see if that helps

I have similar problems with eve-online and wine interacting horribly with pulseaudio, so hopefully the Ibex gets it's horns polished some more soon.  There needs to be a better delivery of information for major functionality like sound services (and probably less jumping into a new sound server architecture before throrough testing) for ubuntu.  Yarr.

Actually, this is it. I was hoping for some answers like "*you're wrong, PA runs a treat*" but no no one answered.
I mean this is no troll and actually is a *real discussion* for the community.
Hoping for more feedback.

Regards,

---

### Post by GepettoBR on 2008-12-02
I'm not an expert, but I believe the issue with not having PulseAudio is that without it you cant' have more than one application accesing your sound card at a time. IMHO that's a biger problem than an FPS drop.

---

### Post by Emanuele_Z on 2008-12-02
> **GepettoBR said:**
> I'm not an expert, but I believe the issue with not having PulseAudio is that without it you cant' have more than one application accesing your sound card at a time. IMHO that's a biger problem than an FPS drop.

I'm sorry mate but ALSA is able (OSS instead allows one application on the soundcard only).
I'm able to do the following with ALSA:
- use WoW (out)
- use Ventrilo (in/out)
- use mplayer (out)
- use Skype (in/out) --usually when use Skype I don't use Ventrilo and viceversa
- use gaim/other apps

and all together on the same hardware device.
Probably Pulseaudio provides better control interface/more sound-candy utilities but at a huge expense: going from 28 to 18 FPS is what makes a game from playable to unplayable.
Just killing that pulseaudio process restored the right FPS.

Regards,

---

### Post by psyke83 on 2008-12-02
Emanuele_Z,
Can you provide the proper link to the mailing list post, please?

While I don't dispute your observations, I would suggest that you refrain from judging PulseAudio based on the incompatibility of a single application (i.e., WINE). 

It is well-known that WINE and PulseAudio do not perform well together (WINE's ALSA driver simple doesn't work properly, causing constant stuttering and performance degradation). 

Switching to the WINE OSS driver and using the "padsp" wrapper works a lot better. I suggest you give it a try before making blanket statements about PulseAudio.

GepettoBR, PulseAudio is not required for audio mixing, but it is an enhanced replacement for ALSA's software audio mixing device, "dmix". The drawback is that it only has ~70% compatibility with existing ALSA applications (for better or worse).

---

### Post by Emanuele_Z on 2008-12-02
Hi there, I've updated the link ([http://www.mail-archive.com/wine-devel@winehq.org/msg42322.html](http://www.mail-archive.com/wine-devel@winehq.org/msg42322.html)).

I didn't judge Pulseaudio *per-se*.
Apart that an application so widespread as WoW+wine should have been tested for correct sound...
But I'm not complaining for this. Using aoss and oss with wine the sounds were working 100%.
What I mean is that ***simply killing Pulseaudio increased the FPS of 50%***.
Now, given my *kinda old* videocard I felt this loss of performace, but generally speaking, you don't provide a new platform if this is so underperformant compared to the previous one. I mean, a FPS drop from 28->25 could be acceptable, but from 28->18 is not.
And I'm not talking of using the Pulseaudio proccessing, I'm saying that just the process up'n'running is so poorly(?) designed that is or locking or wasting resources intercepting the audio.
AFAIK everyone is having this issue with wine, and considering that wine is not an emulator (I don't want to sound *idiot* but wine usually has good performance because even the win32 syscalls are well implemented) it wouldn't be surprising that Pulseaudio would slow down other native 3d apps.

And my *dilemma* is the bold question in the first post. I don't think to be a *uber*user but I simply managed to uninstall Pulseaudio and restored the ol'good ALSA. But what about the average Joe?

Regards,

---

### Post by GepettoBR on 2008-12-02
50% would be a drop from 28 to 14 FPS. 28->18 is 35.7%, which is a huge difference from 50.

I myself have had problems with PulseAudio in Intrepid on one of my computers (the other worked fine OOTB) but it was merely a configuration issue and PulseAudio now works fine after some tweaking. NO, I shouldn't have had to tweak anything and YES my hardware is high-end. Stil, PulseAudio is listed by HTOP in 30th-35th place (for some reson it appears six times) among the processes runing in my system, below several other daemons, with only 0.0-0.4% CPU use and such a low memory us that it displays 0.0% on all but one instance, which is 0.2%.

I don't play WoW, but Civilization IV works fine with Pulse, faster even than Windows, though it can't display some of the texture animations, which might account for why it runs faster.

I'm very satisfied with PulseAudio, though it stil has some big flaws in how it was implemnted by Canonical for Intrepid. I think scrapping it is a poor choice. PulseAudio has at least one great feature that ESD and ALS's own mixer lack, which is a proper system-wide equalizer. Very useful for setups where th speakers seem to be off on equalization, or which include subwoofers. Working out the bugs, testing it more thoroughly before relasing Jaunty - that's what I think shuld be done.

---

### Post by Emanuele_Z on 2008-12-02
Well actually is 50% increment or 36% decrement, chose your point of view. :-)

Actually I'm not the only having performance issues with PA (eg. [http://ubuntuforums.org/showthread.php?t=973637](http://ubuntuforums.org/showthread.php?t=973637) ). This is why I'd suggest to test more such radical software inclusion.

Btw, if I was using oss + aoss why did killing PA increased such FPSes if PA is supposed to be very light?

Again, my specs aren't top end but 2xCore Duo T7700, 2 GB Ram and 8600 GT 512 Mobile are supposed to be kinda fast as well.

Regards,

---

### Post by GepettoBR on 2008-12-02
> **Emanuele_Z said:**
> Again, my specs aren't top end but 2xCore Duo T7700, 2 GB Ram and 8600 GT 512 Mobile are supposed to be kinda fast as well.

Wow, you definition of a fast computer is light-years away from mine. I'm running on a Core 2 Duo E7200, also with 2GB of RAM and a GeForce 8600 GT.

Also, Pulse was already included in Hardy. As I said, it was just poorly implemented this time around. That would probably account for the abnormal behavior on your machine, while it works well on some (like I said, perfect from the go on my old Compaq Evo n11020 and working well after a few headaches on my PC). Many people are having trouble with Pulse, and many are not. It's not a *total* failure, but it does need a LOT of work before it can be considered stable in Ubuntu. I hear it works quite well in Fedora, though, but that's just hearsay :)

---

### Post by psyke83 on 2008-12-02
> **Emanuele_Z said:**
> Well actually is 50% increment or 36% decrement, chose your point of view. :-)

Actually I'm not the only having performance issues with PA (eg. [http://ubuntuforums.org/showthread.php?t=973637](http://ubuntuforums.org/showthread.php?t=973637) ). This is why I'd suggest to test more such radical software inclusion.

Btw, if I was using oss + aoss why did killing PA increased such FPSes if PA is supposed to be very light?

Again, my specs aren't top end but 2xCore Duo T7700, 2 GB Ram and 8600 GT 512 Mobile are supposed to be kinda fast as well.

Regards,

PulseAudio is not meant to be "light". The resampler used is of a higher quality than what "dmix" uses, and there have been calls from developers for the integration of SSE optimizations into these resamplers to help reduce CPU usage.

The Ubuntu build of PA uses a lighter resampler than upstream (speex-float-1 vs. upstream's speex-float-3), but it's probably a little more resource-intensive than dmix. If you take a look my guide you'll see a brief overview of resamplers and their rough ranking of resource usage; I believe that dmix uses the "trivial" resampler, which is one of the least processor-intensive resamplers (and worst quality).

Many users will get annoyed to see the pulseaudio process consume 3-10% CPU via top during audio playback, but they fail to understand that ALSA's dmix uses very similar resources; the difference is that dmix's CPU usage is "hidden" within system processes instead of a single user process.

PulseAudio is not perfect by any means, and there are numerous integration issues - but it seems to be on the right track towards solving the audio mess (in the long run) and bringing the Linux audio stack into the 21st Century.

P.S. Coming back to your specific issue with WINE. You're using the wrong tool for the job - "aoss" is the ALSA OSS wrapper. You need to use the PulseAudio equivalent instead, "padsp". 

I suggest you do some more research into PulseAudio so that you can understand the program you're critiquing.

---

### Post by Emanuele_Z on 2008-12-03
> **psyke83 said:**
> ...

PulseAudio is not perfect by any means, and there are numerous integration issues - but it seems to be on the right track towards solving the audio mess (in the long run) and bringing the Linux audio stack into the 21st Century.

P.S. Coming back to your specific issue with WINE. You're using the wrong tool for the job - "aoss" is the ALSA OSS wrapper. You need to use the PulseAudio equivalent instead, "padsp". 

I suggest you do some more research into PulseAudio so that you can understand the program you're critiquing.

Psyke, I did use **aoss** on purpose, in order to exclude my pulseaudio from usage. If I'm right is that when I use an ALSA application then PA shouldn't be called?
If yes then there's something wrong with pulseaudio architecture because killing that process (that -note- should not even be called) boosted (sorry restored) my FPS where they were before.

In any case anyway how do you explain that simply killing PA process restores your FPS? It is not a coincidence, I tried 3 times and actually that process was slowing down WINE.

All I'm saying is that you shouldn't include this piece of great software if it is reported that is incredibly slow. Because the average Joe won't be able to figure out why and how to fix it.
Ubuntu's target is the average Joe. Am I right?

Let me know what you think,

Cheers,

---

### Post by GepettoBR on 2008-12-03
Has it occurred to you that maybe if the process is being called when it shouldn't the fault is with whoever is calling it (aoss)? If you haven't tried al the well-known fixes, you shouldn't be so quick to label the software as junk.

---

### Post by Emanuele_Z on 2008-12-03
> **GepettoBR said:**
> Has it occurred to you that maybe if the process is being called when it shouldn't the fault is with whoever is calling it (aoss)? If you haven't tried al the well-known fixes, you shouldn't be so quick to label the software as junk.

I'm not saying that is junk.
Imho a sofwtare that actually acts as a deccelerator isn't worth until it provides at least 95% performance of its own competitors.
I'm asking another question:
[b][i]All I'm saying is that you shouldn't include this piece of great software if it is reported that is incredibly slow. Because the average Joe won't be able to figure out why and how to fix it.
Ubuntu's target is the average Joe. Am I right?[/i][/b]

The good thing about free software is that if I don't like it (eg. because I'm an idiot) I can still figure out myself how to remove and fix it my own way (eg. uninstalling the pulseaudio). But for the average Joe this is not simple, hence the above question.

Cheers,

---

### Post by GepettoBR on 2008-12-03
I agree with the bold statement, I just don't believe it suits PulseAudio that well. And you ignored the poitnt of my post: did you try padsp? If not, the problem might be in aoss and not just Pulse.

---

### Post by Zorael on 2008-12-03
> **Emanuele_Z said:**
> (OSS instead allows one application on the soundcard only).
I'll just pop by and tangent with some semi-noes!

The OSS libraries currently in the kernel are 10yrs+ old, at which point the creators made it proprietary. The community supposedly reacted by starting the ALSA project, which in turn is allegedly a confusing pile of Confusage&#8482;. Like everything else, OSS has developed quite a bit over the years (as proprietary software), and naturally a software mixer has been added way back - which is what's needed to play sound from several sources at once. Since a few years back, it's now licensed under the GPL, so technically it could be merged into the kernel without breaking licenses. I suspect ALSA developers hold a grudge towards OSS though, so chances are it likely never will. It's like the deal with Qt going proprietary, forcing people to ditch KDE and start GTK and GNOME, then Qt went GPL making KDE free again, but the grudge remains.

Wiki entry:[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)


Interesting read!: [http://insanecoding.blogspot.com/2007/05/sorry-state-of-sound-in-linux.html](http://insanecoding.blogspot.com/2007/05/sorry-state-of-sound-in-linux.html)

Bias inc.
> [...] the developers of the portable UNIX sound system - OSS, decided to go closed source and offer extra features (which regular users don't need) to paying customers. This of course created an uproar, and some Linux developers decided to create a new solution.

Now instead of just rewriting OSS at the core, or using a wrapper (which understandably doesn't fix the underlying mixer problem), or updating the existing open source OSS at its base, some developers for some absurd reason decided they needed a whole new system and API to go with it. This is known as the Advanced Linux Sound Architecture or ALSA for short. This new API is huge, mostly undocumented, incredibly complicated and completely different than OSS. Which means various sound card drivers have to be rewritten for ALSA, and all applications have to be rewritten (or have more sound system support like SDL and libao) in order to use ALSA.

Other advantages of ALSA is that they included a software mixer (which doesn't always work). But as should be apparent, applications aren't magically overnight going to start switching over to ALSA. And as ALSA isn't portable, people who want to support BSD and Solaris will of course be using OSS. Meaning to support ALSA would mean needing to support OSS and ALSA. Since OSS exists on Linux, why even bother? Realizing this, the ALSA developers programmed OSS emulation into ALSA, so sane developers can just program for OSS. But the big embarrassment here for ALSA is that using ALSA via its OSS emulation is usually better than using ALSA directly. I've heard from many users of SDL or libao powered programs that telling those wrappers to use OSS (which ends up being used via ALSA's OSS emulation) works better with less gaps (or other problems) in the audio than using ALSA directly by those wrappers.

But for some really stupid reason, ALSA's OSS emulation doesn't support mixing. Which in the end really defeats the purpose of ALSA in the first place. I also have two sound cards which work both under OSS and ALSA and find OSS to just work better. Even more shocking is that I found in cards that have hardware mixers installed, they don't seem to be used by ALSA's OSS emulation, leaving such users without mixing in OSS apps. However, for some reason, I'm seeing a lot of propaganda lately that I have to make all my new applications use ALSA and not OSS because OSS is deprecated. I really doubt that because Advanced Linux Sound Architecture now exists that suddenly FreeBSD has deprecated OSS. How can something portable be deprecated just because one really near sighted OS can't figure out how to deal with life? Using non portable APIs is what is deprecated. I've smartly been forwarding all such ALSA propaganda to /dev/null, but it does bother me that my laptop's internal sound card only has support by ALSA in Linux. And with all the propaganda, I am worried what if ALSA makes more headway? It's already annoying that some Linux distros for example ship SDL without the OSS bindings installed, and it could get worse.

A myriad of people have problems with Intel HDA cards/chipsets not working well with ALSA, due to model detection not working well, which could potentially be circumvented by going OSS, instead.

That said - yeah, most people are well enough off with ALSA. I just pick OSS because I like some portability to go with my free-as-in-freedom.


I don't think pulse works with OSS4 yet, though. I haven't followed the issue closely, but at least some 6 months ago there was a problem with Pulse - when using OSS drivers - calling some deprecated API call, and both parties blamed the other. (OSS crew for breaking compatibility with OSS3 [the 10yro+ version] and PA crew for not keeping with the times.)

I'll give that mix a try when I next reformat my netbook; when Mint releases Felicia.

---

### Post by psyke83 on 2008-12-03
> **Emanuele_Z said:**
> Psyke, I did use **aoss** on purpose, in order to exclude my pulseaudio from usage. If I'm right is that when I use an ALSA application then PA shouldn't be called?
If yes then there's something wrong with pulseaudio architecture because killing that process (that -note- should not even be called) boosted (sorry restored) my FPS where they were before.

In any case anyway how do you explain that simply killing PA process restores your FPS? It is not a coincidence, I tried 3 times and actually that process was slowing down WINE.

All I'm saying is that you shouldn't include this piece of great software if it is reported that is incredibly slow. Because the average Joe won't be able to figure out why and how to fix it.
Ubuntu's target is the average Joe. Am I right?

Let me know what you think,

Cheers,

Again, I suggest you do some research into PulseAudio.

Intrepid's ALSA libraries have been patched to transparently remap ALSA output to a running PulseAudio server; using "aoss" will most likely continue to remap audio to PulseAudio in an inefficient way.

You already have a vested interest in PulseAudio (evidenced by your posts), so I suggest you learn about the software before criticizing. There's plenty to talk about, but you're not quite hitting the mark at the moment.

---

### Post by Emanuele_Z on 2008-12-03
> **psyke83 said:**
> Again, I suggest you do some research into PulseAudio.

Intrepid's ALSA libraries have been patched to transparently remap ALSA output to a running PulseAudio server; using "aoss" will most likely continue to remap audio to PulseAudio in an inefficient way.

You already have a vested interest in PulseAudio (evidenced by your posts), so I suggest you learn about the software before criticizing. There's plenty to talk about, but you're not quite hitting the mark at the moment.

So actually I was using PA? Are you sure? So actually I was doing OSS->ALSA->pulseaudio ?
But the fact is that killing pulseaudio, so having OSS->ALSA only, restored performance.
Anyway the fact that PA offers really bad performance is even supported not only by gamers but even from the devs, as seen as they are going to rewrite part of it with optimizations.

Probably I'll try padsp next revision of Ubuntu. Sorry, but I don't have the will and time to fiddle around again to prove that pulseaudio is not fast :-P
For sure the next 9.04 will feature this software and hopefully the new revisions will be better than ALSA.

Again this thread is not about the fact that I personally don't like pa as it is now (I just don't like a new process that sucks all CPU blood as a vampire! :-) ), but the fact that the average Joe isn't ready to deal with such kind of sofwtare in case it's giving him issues (and believe the net, the pulseaudio inclusion has added many sounds issues, not only performance related issues ).

Cheers,

---

### Post by GepettoBR on 2008-12-03
I consider myself an average joe, and I must say you're generalizing too much.

---

### Post by Emanuele_Z on 2008-12-05
Psyke, any answer regarding the usage of aoss with PA?
Cheers,

---

### Post by halovivek on 2008-12-05
alsa is doing good than pulse audio. i could not find headphone option for sound. it is really worst when comes small games also.

---

### Post by psyke83 on 2008-12-05
> **Emanuele_Z said:**
> Psyke, any answer regarding the usage of aoss with PA?
Cheers,

I answered your question already, and if you did some research yourself the answer would have been evident to you.

Some examples, with a running PulseAudio server and WINE already configured to use the OSS driver via winecfg.

Example 1:
```
$ aoss wine wow.exe
```

If you check PA Volume Control (during sound playback), you'll see the client listed as "ALSA plug-in [wine] ALSA playback". This means that WINE is playing OSS sound, which is being "converted" to ALSA output by aoss, and the PulseAudio ALSA plugins are "remapping" ALSA output to the PulseAudio server. This is quite possibly the most inefficient way to play sound.

Example 2:
```
$ padsp wine wow.exe
```

If you check PA Volume Control (during sound playback), you'll see the client listed as "OSS Emulation [wine]". This means that WINE is playing OSS sound, and the padsp wrapper is "remapping" this OSS output directly to the PulseAudio server.

Example 1 will use a lot more CPU usage due to the extra, unnecessary conversion of audio API layers. This is the way you insist on running WINE, inexplicably...

Example 2 is more efficient, and CPU usage is lower.

Both of the above examples are not the most efficient way to use PulseAudio, but it's because WINE is not fully compatible. Either WINE should have a native PulseAudio audio driver, WINE should improve their ALSA driver to be more compatible with PulseAudio, or PulseAudio should improve the PA ALSA plugins to be more compatible (not necessarily a good thing, for complicated reasons).

---

### Post by GepettoBR on 2008-12-05
I just noticed that, while I do get sound while streaming from the internet in Firefox, Firefox doesn't actually appear in PulseAudios plyback screen. Does tht mean I screwed up my configuration somewhere and FF is bypassing PA?

---

