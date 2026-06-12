---
title: "Vsync in Linux:"
date: 2009-10-29
forum: Desktop Environments
---

### Post by Oranges10e on 2009-10-29
Hello, right to the point: I am new to Ubuntu, well, new = been around for a few months now. I have acutally managed to install Ubuntu on a few systems, especially on those of my friends and fam. but now I am facing something different. My school wanted me to show them Ubuntu, because I suggested it. Beeing the only one that has, as far as I can tell, ever done this, they told me to show them what it's about. Long story, told short: they like it but they need fluid and nice vsync'd video. Which works fine, unless you activate compiz or any nice looking effects. On a small LCD it is not such a big deal but on a huge wall (at a good quality), it's just too difficult not to notice it. 

So, here I am, asking this: who else would like a combination of good (3d?) desktop-effects AND vsync enabled by default on windows AND videos - no more tearing in other words, no matter where and why? Is it a good idea? Maybe you don't care about it, maybe you do. I sure do. Other OS's can do it without problems, why should the Nr.1 Linux distro be missing? This is something that even WindowsXP and especially the newer Vista and Windows 7 have. It's a shame beeing forced to go down and use Meta, just to watch something without the screen getting teared in to pieces, ya know? ;D :popcorn:

Thank you for your time.

Edit: [https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/212587?comments=all](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/212587?comments=all)  <- for more information on this "bug".
Oranges

---

### Post by Amaranth on 2009-10-29
I've already told you, this is simply not possible right now. We'd all love to love to have it but our drivers and Xorg lack the capability.

---

### Post by &#1057;&#1090;&#1088;&#1072;&#1085;&#1085;&#1080;&#1082; on 2009-10-30
+1
 
Developers should work on that

---

### Post by jonasback on 2009-10-30
Hum, are you ppl sure it doesn't work. Because i set this up for myself about a week ago, when i connected my computer to my 40" tv. The videos that i watched had a lot of tearing, i activated Vsync in nvidia-controlpanel but it didn't help. I googled a lot and found the solution. 

1. Install compizconfig-settings-manager
2. System --> Preferences -> CompizConfig Settings Manager
3. General Options --> Display Settings (This is a tab)
4. Uncheck "Detect Refresh Rate"
5. Fill in the refresh rate that your monitor supports
6. Tick the box beside "Sync To VBlank"

This works for me. I'm not really sure if this is what you wanted. Just woke up, so I'm a little tired. Good Luck!

---

### Post by Oranges10e on 2009-10-30
@Amanranth: Hi, yes, you did. It is not possible right now but, what doesn't work, can be made to work. Isn't Gnome3 comming out next year? Why not use that chance and make a "few" more changes or try to find or build something that does make it possible, especially if others already have it? 

@Jonas: Hi, thanks for the tipp, I already tried that, though. It works fine for the desktop or my window-movement, they all get vsync, but my videos remain teared. I tried Kubuntu last week - the same thing. Amaranth already said it is not possible right now, that is fine. But since we all know, what doesn't work in or on Linux, can be made to work, even if it takes some work or time. Now that Ubuntu has strong support (Canonical), this should be done and the power the has granted thou shall be used.....wait...ah...I'm too much in to Zelda right now, sorry :popcorn:

Oranges

---

### Post by jonasback on 2009-10-30
If you have a graphics card from NVIDIA this will work for you. I set it up myself about 1-2 weeks ago. All my videos are playing fine right now. On my monitor and on my 40" TV.

1st set up the things i already told you. 

Then. In NVIDIA-settings

X Screen 0
   X Server XVideo Settings, tick "Sync to VBlank"
   OpenGL Settings, "Sync to VBlank" "Allow Flipping"
Then GPU-0 
  DFP-0 - (Samsung SyncMaster) it says like this for me
  Uncheck "Force Full GPU Scaling"

I'm attaching my nvidia-settings config file. 

If you however don't have a card from NVIDIA i can't help you.

---

### Post by Oranges10e on 2009-10-30
Hello again, thanks a bunch for the information. 

Yes, I do have a Nvidia card (7300go and 8600gt). I am at school right now, I'll try that out as soon as I get home. Actually, I should have everything you posted enabled, I'm not sure about the "force full GPU scaling" thing, though. Got to check that. Anyway, if this actually is a solution to the vsync problem, why would ppl claim it isn't possible, if it actually is O,o Hmm, two different opinions. I'll try it out and post my results tonight.

Anyway, any tipps for ATI cards? The ATI card my girl has is a "X800 Pro". The good thing: drivers were auto. installed after a fresh install of Ubuntu. Bad thing: no vsync either. Anyone any tipps for that? 

Thanks so far, I appreciate it! :KS

Oranges

---

### Post by Amaranth on 2009-10-30
Making this work requires changes to Xorg, mesa, every graphics driver, and every compositor. "GNOME 3" isn't required to make these changes but you'll be waiting for nvidia to support it even after the rest of us get this.

---

### Post by Oranges10e on 2009-10-30
Okay, I have returned. I will now try what Jonas suggested.

@Amaranth: Hm, well, changes have to happen sooner or later. Let's just wait and see how many actually want this. Like I said, I wouldn't have thought about this that much, if  the ppl at my school wouldn't have said anything about it - they've never tried anything else besides Windows and they don't know how things work. As far as their knowledge goes, when something doesn't work like they're used to it, then it's just "broken" for them. That is why I understand the need of features like this. Not only is it something, relativ, important for the mass-market or the "normal" user, especially the ones switching (most of them will be Windows or Mac users), but it's also a standard long used by it's competitors (a "feature" that actually does something good). About Nvidia, well, I know they aren't that open like ATI is, but what can you do about it? They do have good drivers, though. Anyway, I mentioned GNOME 3 as a chance to do this, a opportunity to bring new features or to fix things, not as a requirement. About Nvidia taking so long to support things: I have no clue about that kind of stuff. Maybe someone should give them a few million $$$ or some :popcorn: :P

Oranges

---

### Post by KlinerDraken on 2009-10-30
@jonasback good tips, this worked for me!

---

### Post by jonasback on 2009-10-31
> **KlinerDraken said:**
> @jonasback good tips, this worked for me!
Well thank you! Finally someone belive me! \\:D/

---

### Post by Oranges10e on 2009-10-31
@Jonas: Hi, sorry for the late report. I tested this on two PC's. It actually worked. Jonas, you were right. Sometimes tearing still happens, but not all the time like before.

My question now is, how can this be, if it is said not to work on Linux? If it is this easy to set this up, why isn't this activated at default on a fresh system install or why isn't this listed on any documentation about this relativ important option on the official Ubuntu site (FAQ)?

I think someone should really take a look at this.

Oranges

---

### Post by jonasback on 2009-10-31
Well good for you! :D I don't know why this isn't listed anywhere. I posted like 2 or 3 threads here and got no response at all. Then i suddely found some guy that suggested to change the settings in CCSM.. I had aleady changed my NVIDIA-settings so that was all that was left to do. This is issue is VERY annoying and it took me a couple of days to figure out how to solve it. My displays are working perfectly now and i have no tearing at all whatsoever. 

Interesting that the devs don't know about this?

---

### Post by sherington on 2009-10-31
@jonasback
Thanks for posting your tip about installing the compiz config tool.

I followed your tip and those settings seem to work just fine for me.

Flickering and tearing drives me nuts and this seems to make it better.

---

### Post by Oranges10e on 2009-10-31
@Jonas: Yes, indeed, it really is strange and interesting. It is said not to work on Linux, but it actually does. It makes you wonder about a few things. I have been looking around on a few forums too, there was always a bit of confusion about this. I think this should really be examined. 

@sherington: You are not alone, my friend. You are not alone.... :D

Oranges

---

### Post by Oranges10e on 2009-11-01
So, how come the devs didn't know about this? 

By the way, I have a new problem. I don't know if this is related or not, but, as soon as I plugin my second LCD and use that one as my main and only panel, my screen starts to go black for half a second, like the blink of an eye, every few minutes. It happens at random, I guess. What's up with that?

Oranges

---

### Post by Amaranth on 2009-11-01
The developers know about it. :)

I've already explained in the launchpad bug report that spawned this thread why this doesn't actually fix the problem and why we can't do it by default anyway.

---

### Post by screaminj3sus on 2009-11-01
Its completely ridiculous for a modern 3d desktop to have such horrible tearing and a vsync option that does not work. Vista and OSX have had this for ages.

---

### Post by Oranges10e on 2009-11-01
@Ama: Hm, well, could there, at least, be a documentation on this for Nvidia users? If someone knows this from the beginning, one can buy a Nvidia card instead of something else, if the others don't work well or have problems with this. Thats what I would do. If I know this is going to be a problem on, for example ATI or Intel, then I won't buy those. Sooner or later this is going to have to be done, though. Ubuntu is for the desktop-user, right? A desktop should have decent vsync. Now that Canonical is supporting Ubuntu, maybe they can help out with this - considering the fact that this would need a lot of work and, maybe even financial support, to make it work? IF enough ppl show interest, that is. Let's see how many actually want this.

Finding a working solution to this can take days for a "newbie". This is totally against the "get productiv" philosophy. The solution Jonas posted actually works very well, at least for me (Nvidia). I have turned off vsync in my Nvidia CP and only activated it in Compiz and followed the rest of the tipps given, it really does work. Windows and videos don't tear anymore, and if they do, it has to be minimal, because I can't see any tearing. This is a lot better then the default tearing you get after a fresh install. I haven't had any side effects with this.

If anyone else wants to try this out, then please post how it worked for you. 

Oranges :popcorn:

---

### Post by sherington on 2009-11-02
At the risk of flogging a dead horse, I'll just add another 2p...

Because of this issue the first thing I usually do after installing Ubuntu is to disable compiz and all of the visual effects because frankly it looks terrible when every menu flickers, and when windows tear when you move them.

With the 'fix' described in this thread, I have the maximum effects settings enabled and I think compiz looks great now - I wouldn't want to go back.

As amaranth says, and thanks for your clear explanations here and in the bug report, it's not a proper 'fix' - but it's a good enough fix for me.

---

### Post by Xorp21 on 2009-11-02
I can't get vsync to work on my ATI card, everything just lags, animations are not smooth enough, video's tear. It isn't anything massive but enough to irritate me so much I'm willing to give up, it just doesn't look as smooth as Windows does. I wanted to give Ubuntu a go but this absolutely is a deal breaker for me. I've been trying for 2 days now to get it to work properly.

---

### Post by duckdown on 2009-11-03
I am having VSync problems in Ubuntu also, with my NVIDIA 9600 GSO card (Supports VDPAU.)

I had a perfectly great working Ubuntu 9.04 setup with XBMC, everything was working great, then I decided to listen to the nagging update notice and upgrade to 9.10.  It has been a complete disaster; my X Server wouldn't start up, my USB is broken now, my bluetooth stopped working and only STARTS working when I remove and plug back in a hard-wired USB keyboard as weird as that sounds...  It has just been terrible

And on TOP of it all, I now have TEARING under XBMC that I never used to have before!

I already had the "Sync to VBLANK" options enabled under both OpenGL and XServer Settings but neither of those did a damn thing.  Then I followed jonasback's advice of un-ticking "Force full GPU scaling" and it is MUCH better now; however not perfect.  Nowhere near the performance of Microsoft Windows...  What the heck is going on?

I am using all the newest drivers

Thanks

---

### Post by screaminj3sus on 2009-11-03
With ati using either fglrx or the open source drivers compiz tears for me even with detect refresh rate ticked and the correct refresh rate entered. sync to vblank simply does nothing.

---

### Post by oobuntoo on 2009-11-04
As much as I love open source software, Linux in particular, there are also parts that I hate that are inherent to it. This is one example: Development of various parts of technologies that are supposed to fit well together just don't work well together simply because all these developers have their own agendas and philosophies to fulfill. There is no authority in charge to make sure that they all work toward the same goal as in proprietary environment, such as Microsoft. In the end, there are a lot of hacks just to get things to work. When the end users complained about not having features other OS'es have, they were either told those feature were not important enough or that they go code them for themselves. After all coders get to decide what's important.

So now we have technologies like Xorg, window compositor, graphic driver, kernel mode setting, and etc..., that just don't fit well together. VSync problem is just one example of these. I suppose this will continue for a long time to come; it's just part of open source software development.

---

### Post by Oranges10e on 2009-11-07
Well, at least it works without Compiz, if it wouldn't it would be a very BIG problem, but this should get some work. I managed to get my teacher to listen to me. I told him, that one could just turn off Compiz, use Meta instead and be happy, he said it's O.K.

So...I will report back and tell you guys how it goes with further discussion. 

I turned off Compiz at my home computer as well. For me it really is productivity over eye-candy. I also noticed, that a few "glitches" I had before (flash videos somtimes flashing in full-screen, crackling noise in games, multi-monitor setup probs and a few other weird things) are now totally gone. Sure, I feel like in WindowsXP, due to the missing modern effects, but this is the only way it works perfect. Sure, Jonas tipps work too, but it's kind of buggy sometimes (tried it out on a dual monitor setup and two other computers yesterday with different hardware-setups) and it's not an option for ATI card users or Intel GMA folks. So...

Oranges :KS

---

### Post by Cresho on 2009-12-03
well, I fixed my vsync issue just reading around.  what i did was forgot about the nvidia-settings since it's now useless unless you script it to turn on after a few seconds boot and force compiz on.  the compiz config manager is now your friend.

all you really need to do is double the refresh rate in display settings of compiz config manager under general options(install in synaptic).  in my case, i have 60 refresh rate, now its 120 (200 crashes the desktop with 3d games) and untick "detect refresh rates" and tick "sync to vblank". reboot if you want.

i can now play videos with no vsync problems in karmic koala

vsync problem is a major issue in kubuntu.  i went from ubuntu to kubuntu and back to ubuntu finding a generally easy way to play with settings.  as far as I know, vsync for video in kubuntu is not possible.  kwin or that settings manager for the opengl compositor has no option available.  compiz config is mature enough.

---

### Post by Yellow Pasque on 2009-12-26
For ATI open-source drivers, you need interrupts support as a prerequisite for vsync. That means you'll need a 2.6.33 kernel with KMS (kernel mode-setting) for RadeonHD cards.

While I don't expect it to work out-of-the-box in Ubuntu 10.04, it shouldn't be too difficult to set it up using the mainline kernel and xorg-edgers PPA's (once 10.04 gets close to relaease).

---

### Post by Oranges10e on 2010-01-28
Hello,

I don't want to bring this back to life for no reason, so I'll post what I have found out so far and what helps a bunch, especially for newcomers. I asked (in disguise) AaronP about this at nvnews.net and he gave me a few tipps:

**1)** As mentioned before: Download **ccsm** for **Compiz** via the **Software Center** in Ubuntu

**2)** Enable **Vsync** in **ccsm** (**General Options**) **and** in Nvidia drivers (nvidia-settings)

**3)** Quoted from AaronP: "Run** ccsm**, then click "**General Options**" and *check the box next to* "**Unredirect Fullscreen Windows**". While you're there, click on the "**Display Settings**" tab, *turn **off*** "**Detect Refresh Rate**", and then set the "**Refresh Rate**" *slider to **double** your screen refresh rate* (e.g. 120 if you have a 60 Hz screen). That should help improve smoothness and reduce tearing for regular non-fullscreen stuff."


**4)** For smooth and fluid video playback (DVBT, DVD, MPEG2 or h.264...etc.) use **VDPAU**. _Skip to step 4a if you don't need information on VDPAU_.

AaronP's words quoted: " VDPAU accelerates video decoding, which allows you to play HD video on plattforms (like the HP Mini 311 I'm using right now) that otherwise wouldn't be able to play them. It also presents video to the screen, which lets applications like mplayer and xine provide smoother, tear-free video. Getting videos to play is a separate issue... "

**4a)** Use VDPAU in combination with Mplayer or Smplayer. I recommend (for Karmic) Smplayer, if Mplayer should crash on you and you don't have the time or nerve to look up a fix or report the problem. I have tested it on three machines with Smplayer - works fine. Options -> Video -> At the top select **VDPAU** (remember to use up2date drivers - I think! it was 180.xx + for VDPAU).

For tear-free television on Ubuntu + Compiz:

**4b) **To get Kaffeine or Metv to use VDPAU, do this: 

"Yes, dvbt video streams are either mpeg2 or h264 that VDPAU will decode. The same applies to dvb-s/s2 and dvb-c.

Both kaffeine and me-tv use xine-lib as engine. In order to get VDPAU working with these players, you need to install a fresh svn copy of xine-lib 1.2 (which includes VDPAU support) and you have to recompile the players against it. Or just wait until your distro provides updated packages." <- Quoted from Crisalide on nvnews.net

For more information about VDPAU or if you want to see if your card is supported, then visit: **[http://en.wikipedia.org/wiki/VDPAU](http://en.wikipedia.org/wiki/VDPAU)** 


*Additional information*:

**Q**: "Anyway, I have a question about the Refresh Rate: Why does it need to be set to double the rate my monitor has (60hz)? Is there something wrong with the detection?"

**A**: "The refresh rate detection thing gets incorrect information basically because it interacts badly with something the NVIDIA driver has to do to ensure that your screen configurations are unique. It's best just to turn it off. 

It doesn't *really* need to be set to double, but setting it that way allows Compiz to queue up rendering without waiting on the CPU a lot." 

**Q**: "I read a lot about xorg not beeing able to do vsync and such, but without Compiz (only Meta) it works good with videos. How does that work?" 

**A**: "This is referring to core X rendering, which indeed does not sync to vblank.  The two main video presentation APIs, XVideo and VDPAU, both have their own separate vsync support. For XVideo, it's an option (which is enabled by default). VDPAU always syncs to vblank when your window is not redirected. In fact, if you disable the Composite extension entirely (with "nvidia-xconfig --no-composite"), VDPAU can use the video display hardware which is not even capable of tearing." 

**Q**: "If I use "nvidia-xconfig --no-composite" it will turn off Compiz, right? It's like if I would manually shut it down, eh?"

**A**: "Not quite, just manually shutting Compiz down leaves the Composite extension enabled. Disabling it in xorg.conf is a bigger switch."



That's about it. Personally, I think ALL this would be awesome if it were activated by default when installing the prop. Nvidia drivers. With the poll/survey about prop. software in Ubuntu and Lucid shipping with more bling bling (can anyone confirm this?), this would be a **VERY** user-friendly step. It's hurts any newbie looking up for all this on his own. This should at least be part of some FAQ or HELP file if it can't be activated once the prop. drivers are installed. Once you activate the prop. Nividia drivers, Compiz sais "hello!", too. So, this could be activated as well. 

Anyway, thank you for reading. :KS

Oranges

---

### Post by James M on 2010-02-11
> **Temüjin said:**
> For ATI open-source drivers, you need interrupts support as a prerequisite for vsync. That means you'll need a 2.6.33 kernel with KMS (kernel mode-setting) for RadeonHD cards.

While I don't expect it to work out-of-the-box in Ubuntu 10.04, it shouldn't be too difficult to set it up using the mainline kernel and xorg-edgers PPA's (once 10.04 gets close to relaease).

What you say is moot. Xorg and X11 can not sync to v blank as they are asyncronous. If X11 could vsync, apple would have used it instead of using and improving upon Quartz. Quartz was chosen because it is syncronous, and it doesn't suck, basically.

---

### Post by Stason on 2010-02-26
> **James M said:**
> What you say is moot. Xorg and X11 can not sync to v blank as they are asyncronous. If X11 could vsync, apple would have used it instead of using and improving upon Quartz. Quartz was chosen because it is syncronous, and it doesn't suck, basically.

Hmmm...on my machine I only get tear-free video playback if I select x11 driver. None of the other tricks worked.

---

### Post by ripps818 on 2010-04-02
After alot of experimenting in Lucid with radeon r300 KMS. I figured out what I think is the best way to reduce video tearing. I use mplayer with vo=gl:yuv=4:rectangle=1:swapinterval=0 and compiz with unredirected fullscreen checked.

Oddly, it seems disabling vsync seems to actually reduce tearing. I'm betting this has something to with the fact that vsync seems to throttle the video card and is instead causing it to render poorly, but this is only a guess.

---

### Post by psychok9 on 2010-05-10
> **James M said:**
> What you say is moot. Xorg and X11 can not sync to v blank as they are asyncronous. If X11 could vsync, apple would have used it instead of using and improving upon Quartz. Quartz was chosen because it is syncronous, and it doesn't suck, basically.

We need a new X.org/X11? Why the people that work on "X.Org" do not listen us?
It's the main bug of Ubuntu/Linux experience!

---

### Post by AshRice on 2010-05-18
I have to agree, I tried 8.04 a few years ago and gave up because I couldn't watch movies (read: back to Windows). Tried again with 9.10 and FINALLY found out about this VSync stuff. Everything is perfect in 10.04 on my desktop w/ a 9800GT. I had an oversight when buying a new laptop and now I have an ATI card :(. The tearing is terrible with or without compiz.
</rant>

This thread did help though!

As a side note even with my laptop if I play videos with VLC in OpenGL mode, the tearing is almost nil.

---

