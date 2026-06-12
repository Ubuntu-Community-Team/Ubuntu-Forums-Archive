---
title: "Smooth Graphics: Impossible?"
date: 2007-10-07
forum: Desktop Effects &amp; Customization
---

### Post by Batuhan on 2007-10-07
I have my display drivers and all that stuff correctly installed. Everything is running normal as expected. What I call as a problem is not a problem for most people I think, but I'll give explaining it a try.

I'm using compiz fusion with XGL but that is not a problem. Same thing happens without CF too. If you are using wobbly windows, I suggest you disable it to see what I mean but you can keep it on too, it still happens.

Open any window, grab the titlebar and start moving the window around. What you will see is that on the sides of the moving window there will be discontinuities in graphics, when it is in motion. I don't know how to explain it, if you are dragging the window to right, then some parts of the window will fall behind and some parts will go righter when the window is in motion. The lagging part and the other part of the graphics will change  places in a wavy motion.

This gives the gui a VERY cheap feel, and this not only happens in Linux but in Windows too. The effect is very visible in Linux, it's a bit better but not completely gone in windows and it simply is not there in Mac OSX!!!

I have Ubuntu as my main os in this computer then there is Windows and Mac OSX(this is an ordinary pc so it is a hack osx). When I boot into osx, I move any windows, all the graphics are VERY smooth, there is no sign of that ugly discontinuity effect whatsoever! And if you have never used mac osx I should tell: It changes the feel of the desktop in a VERY strong way.

Now, I want to ask, if there is any way of achieving that in ubuntu and/or Linux in general. When I did not have osx, I was thinking that this was a refresh rate issue as I'm on a laptop and the refresh rate of my panel is max 60Hz. But this is the same when I boot into osx. So that is not releated to refresh rate, as far as I can see.

Please, if you have a mac or if you have friends who has a mac, try to focus on this a little, and see what I mean.

Remember that this does happen when you are moving, resizing windows, anything big moving in general.

I'm hoping, there is a way of fixing it.

What do you think?

---

### Post by steveneddy on 2007-10-07
You may be experiencing what some people call "tearing".

It could be that you don't have enough video card for what you are doing, enough VRAM (video RAM), enough system memory, maybe a processor that isn't fast enough, the programs aren't compiled to run on your system (try compiling CF from source), the video binary drivers aren't the newest version, if you are running nVidia, maybe the settings are too low.

It could be one of many things or a combination of a few of these things, or sometinng completely different.

Please tell us the hardware you have.

Is it a laptop or desktop?

What video card do you have? Specs?

How much memory do you have?

What processor? Is is a 32 or 64 bit processor? 

Are you running a 32 or 64 bit OS?

I found that by running the 64 bit version of Feisty on my Core 2 Duo laptop, that most of my video tearing issues disappeared. AAMOF, many display issues are not even there anymore after switching to the 64 bit version of Ubuntu. I guess the hardware wanted/needed the 64 bit processes to optimize the operations of the computer.

my 2 cents.

:popcorn:

---

### Post by Batuhan on 2007-10-07
Hi Stevenedy, thanks for your input.

"Tearing" explains the effect perfectly. I'm not a native english speaker and did not know that this thing had a name. Yes, it is tearing.

I think, I have a fast computer. 256megs of VRAM on ATI x1600 mobility graphics card, c2duo T7200 duo core CPU with 4megs of cache at 2ghz(this is an 64bit processor).

1280x800 at 60hz.

This is a laptop. And I have 1gigs of system memory. I'm running 32 bit Ubuntu Feisty. 64bit is not an option for me as some of the software I use my computer for still relies on 32bit architecture.

My first experience with Ubuntu was the 64bit version but I don't remember how it was, duh...

I'm using the restricted drivers from ATI. Maybe I can give it a try, can I use the restricted drivers manager from the 64bit live cd? Maybe I can install my graphics card drivers form there and see if it still happens.

The tearing I experience is a "subtle" effect, I think most people would never consider it as a problem. But Mac OSX has no sign of tearing problem whatsoever and it runs in this computer(and this computer was not designed to run osx actually, the display driver is a hack). And once you see how "no tearing" feels on your desktop you instantly recognise it in Linux and the whole experience feels very cheap after that.

Anyways, I'm happy to hear that some people are not experiencing this, this means I have a chance of fixing it.

---

### Post by steveneddy on 2007-10-07
I'm not familiar with ATI, but in nVidia we have a utility that lets the users of nVidia hardware tweak the settings to get a desired effect on the display we are using. 

You may look into this, if there is a utility for changing some of the default setting with an ATI card.

For nVidia, it is

nvidia-settings

Good Luck - 

:popcorn:

---

### Post by Batuhan on 2007-10-07
Ok I've researched a bit.

I'm using the fglrx drivers because I have a x1600 mobility card. I'm running on XGL so direct rendering does not work.

I think this has something to with vsync and hsync settings. When I move a window horizonally, tearing occurs on the edges. When I move it vertically, no tearing on up and down parts of the screen but the window contents are a bit "wavy" . Like some parts are going faster ans some are going slower but it is consistent in a line so it does not look like tearing.

In my xorg.conf:
```
Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-64
	VertRefresh	43-60
EndSection
```

Horiz sync and vertical refresh are set as ranges. Might this be causing the problem?

When I boot into mac osx I have no tearing issues so maybe It has the correct settings for it. Does anyone know how I can see the sync and vertical rate setting in mac osx? So I can copy them from there maybe?


************************************************************************
And one more thing, I've seen a thread where this issue was solved by a driver update.
My current ati driver version is: 8.34.8

When I look at the ATI site, the latest version seems to be 8.40.4.

I checked the repos and they are still at 8.34.8, why is that?
If I install the package from ATI site would that cause a problem, break something?
Things can surely go wrong but what I want to know is is there a reason for the repos to be outdated and installing them by hand would be a silly act... If not, I'll give it a try.

Thanks

---

### Post by Batuhan on 2007-10-08
Uh ok I've been struggling with this for hours but basically nothing works.

I've installed the latest ATI drivers with Envy, which did a great job.
It did not help either. The new aticonfig does not write the horizrate and vsync values to xorg.conf but looks them up from EDID I guess.

I used a EDID extractor in windows and used it's raw output to feed xorg but it did not help either. I ave this tearing only horizontally. Scrolling webpages are ok(top down).

And I have the same issue in windows too bu I've checked other machines and basically all of them have it. They have small horizontal tearing problems.

But as I said, somehow MacOsx sets things up correctly so there are no problems.
Duh...

---

### Post by Batuhan on 2007-10-08
Oh and I wanted to try custom Horizrate and vsync values in xorg.conf to see if they would make any difference but I think they are just ignored. Why is this?
I write absurd numbers(like 1000) to those and X still works fine without any change.

Does this have something to do with XGL? I'm confused...

---

### Post by Batuhan on 2007-10-08
No, basically nothing works.
I believe this is how things work and people are seeing this as normal.
This is also the issue with every windows(XP) box. As far as I've seen.

I've checked the xorg logs and display driver extracts the EDID info from my screen correctly. So it is seting things up correctly, I assume.

Enabling vsync does not help.

I want to see a linux box which does not have this issue to be sure. Dragging the window from left to right or reverse should cause minor distortions, is there anyone who does not have this issue? And knowing what I'm talking about?

Most tearing problems in forum I see are big problems, they effect video playback and screensavers dramatically. So according to those my system would be ok, but I would not consider this to be ok.

Phew, anyways. Wasted enough hours on this...

---

### Post by rsambuca on 2007-10-08
I think you will have less of an issue if you used an nvidia card and drivers.  ATI video works, but is somewhat more problematic in linux at the present.  This may change in the future, though.

---

### Post by Therion on 2007-10-08
I'm going to chime in on this because, if I understand what is meant by "tearing", I'm getting it as well, and I'm an nVidia user.  To me, the problem looks like I have "pointer trails" enabled; only it affects the active window, not the mouse-pointer.  Are we talking about the same thing?  I'm going to assume we are.

The basics of my hardware config are an AMD 4200+ dual-core (clocks in at 2.2Ghz), 2GB of RAM and an nVidia GTS 8800 (320MB); I'm using the nVidia binary driver as downloaded and installed by Envy. Everything is running like a well-oiled machine thus far with the installed driver.

I just assumed this effect was normal, but it is most *certainly* annoying and if there's a way to fix it, I'm definitely interested in knowing how.  Thought I'd pop in here because it's not just an ATI problem apparently.

---

### Post by Batuhan on 2007-10-08
I've made an experiment and I think it proves that this has nothing to do with hsync-vsync or something of that sort. This is not a monitor issue, as I can actually capture it by taking a screenshot. If that was caused by a misconfigured display driver then it would look ok in a screenshot but would look bad to me in reality.

If I can capture it by taking a screenshot then it looks like it is happening because of the method things are drawn on screen.

The screenshot I'm attaching here look A LOT worse than it really is. The parts are so closer in real so it is not as annoying as you can see in the attached picture.

This happens only while moving horizontally ie: moving left to right or right to left.

I am not able to capture it by taking a screenshot in Windows XP(I haven't tried vista yet).
On macosx, there simply are no problems. (to recapitulate)

---

### Post by obsidience on 2007-10-09
Batuhan,

I'm a bit new here but I believe you want to be looking up the term "vsync".   This is a problem mostly with video games in which the video card renders faster than the monitor refreshes and results in tearing.  

I found some info that might be of some use to you:

[http://forums.gentoo.org/viewtopic-t-570888.html?sid=3247a48cc7e87bd4fc9a9bae81ebc8c4]("http://forums.gentoo.org/viewtopic-t-570888.html?sid=3247a48cc7e87bd4fc9a9bae81ebc8c4")

Good luck!

Obsidience

---

### Post by apauloisdead on 2007-10-10
Judging by the description, and the screenshot.... i'm having this EXACT problem.

I actually found this post in a google search, looking for a solution.


I'm on a Sony Vaio laptop, and i've never had this problem with Vista.

I pretty much agree with everything Batuhan has said, anyone know of any solution?

Edit: By the way, my video card is an intel 945GM express

---

### Post by Batuhan on 2007-10-10
Ok, I think everyone has this issue but not everybody cares about it.
I've searched deep in the Internets for this and did read much about it.

Windows XP for example has vsync on desktop disabled. That is why we have ugly tearing on XP desktop. Vista however, has vsync enabled on desktop.

And I've managed to get vsync on my ubuntu desktop. But it does not work with regular windows and such. Only opengl windows and maybe videos. Not sure about that.

To enable vsync in ati x1600 mobility, you need to turn OFF compositing(bye bye compiz fusion) so you can have direct rendering enabled.

After you have direct rendering(without xgl) you can use driconf to enable vsync.
According to my tests, with this method you can have vsync in opengl content without problems. But it is not possible with XGL. And even if you don't use XGL and have vsync enabled, the regular windows and your desktop usage is still unsynced.

The "sync to vblank" obtion in compiz fusion, when using XGL is just not working.

I think this is a driver issue with ATI.

I think there is a way to enable vsync in nvidia vards. I've seen it several times on differen threads. You add "sync_to_vblank" option to some config file and people say that it is working.

These simply is no hack for that for ATI cards(which use the closed source drivers).

apauloisdead, I don't know much about onboard intel chips. If you don't use Compiz, and have direct rendering enabled you can use driconf to sync yoour video to screens refresh time. I'm not sure how it will be with XGL though.

---

