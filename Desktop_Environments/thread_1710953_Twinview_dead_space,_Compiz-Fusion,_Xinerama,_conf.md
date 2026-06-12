---
title: "Twinview dead space, Compiz-Fusion, Xinerama, confusion/etc."
date: 2011-03-20
forum: Desktop Environments
---

### Post by TheVrolok on 2011-03-20
I'm a born again Linux newbie in that I've installed Linux distros a number of times over the last decade, used them for a month or two, and then gone back to Windows ... primarily because 1) I am (was?) a fairly hardcore PC gamer, 2)  Have had a Lexmark printer that has (historically) had terrible Linux support, 3) Am a student and are often forced to use the latest MS Office documents which have not always been easily readable in Linux.  So while I've used Linux before, I wouldn't say I'm much more than a newbie.

I'm due for a new go-around, and I'm going to try to make it work this time because I'm not nearly the gamer I used to be, and can work around school, etc. I'm still running Windows 7 on my primary HDD, but have put Maverick Meerkat (Kubuntu, but I don't really think it's a KDE specific issue) on the secondary HDD all by itself while I see if I can make the conversion. I just finished setting up my dual monitors (GTX 285 support a 24" BenQ (1920x1200) and a 20" ViewSonic (1680x1050)) which was actually a bit of a PITA as the 20" isn't sending/has corrupted EDID.  But, I managed to extract the EDID from the Windows registry and set up the monitor is CustomEDID.  Anyway, they're working now, but set up with Twinview and a metamode of 3,600x1200, so there is 150 pixels of dead space in the vertical region. 

Now, that dead space really annoys me as Windows has no problem using 2 monitors with independent resolutions and spanning them. However, I understand the only way to have individual resolutions for each specific monitor in Linux is to set up a separate X server for each monitor (which is NOT Twinview) and this will not allow windows to be drug across.  I also understand that this problem can be fixed with Xinerama, which would allow a separate X for each monitor (so no dead space like I currently have) AND allow dragging across the monitors - BUT the catch here is that 3D acceleration occurs on only one of the monitors so no Compiz-Fusion on both, essentially?

I've done a bunch of google/forum searching, but I only seem to find articles that are 2-4 years old, so what I'm wondering now is what is the current state of dual monitor support.  Is there any way (hopefully stable) that I can have 2 monitors, each with an individual resolution (therefore no dead space), the ability to drag windows across from one monitor to the other, AND use Compiz-Fusion (or whatever the current eye candy manager is)?  Or am I just dreaming?

Thanks in advance guys, can't beat the Linux community for support help!

---

### Post by TheVrolok on 2011-03-21
bump

---

### Post by RobbieThe1st on 2011-03-22
I just ran into this problem. I went with Twinview, and that allows compositing(including Compiz), my choice of screen-locations(My secondary monitor is on top of my primary one, and it's centered). The only thing I don't have this way is snapping to the edges of the secondary(smaller) monitor. Oh well.

---

### Post by Copper Bezel on 2011-03-22
It's going to depend pretty heavily on what graphics card you're using. The vanilla integrated graphics card on my netbook has no problems with two separate screens of different resolutions from one X session with compositing via Compiz and no dead space, etc, set up simply through Gnome Display Properties (Preferences -> Monitors.) Compiz crashes if the resolutions are too high and together exceed a certain virtual desktop size, but I don't have any problems with normal use.

If you have a special card installed with proprietary drivers, you probably won't have access to all of the same options, because settings from gnome-display-properties won't apply.

Edit: Wait, you're using KDE. Sorry. Similar things will apply while being named different things. = ) The DE you're using really *can *have an effect on this stuff, but as I understand it, KDE is generally better at this than Gnome, and the big question is whether or not you're using a graphics card that requires proprietary drivers.

---

### Post by TheVrolok on 2011-03-22
> **Copper Bezel said:**
> It's going to depend pretty heavily on what graphics card you're using. The vanilla integrated graphics card on my netbook has no problems with two separate screens of different resolutions from one X session with compositing via Compiz and no dead space, etc, set up simply through Gnome Display Properties (Preferences -> Monitors.) Compiz crashes if the resolutions are too high and together exceed a certain virtual desktop size, but I don't have any problems with normal use.

If you have a special card installed with proprietary drivers, you probably won't have access to all of the same options, because settings from gnome-display-properties won't apply.

Edit: Wait, you're using KDE. Sorry. Similar things will apply while being named different things. = ) The DE you're using really *can *have an effect on this stuff, but as I understand it, KDE is generally better at this than Gnome, and the big question is whether or not you're using a graphics card that requires proprietary drivers.

It's funny you say that; shortly after I posted this thread, I decided to reformat and put Ubuntu (with gnome) on instead of kubuntu.  Of course, I can just as easily install KDE and switch over if I'd like.  Running on an GTX 285.  So we'll see, I think I'll just have to backup my current xorg.conf and go about trying different things.  Try Compiz-Fusion with this set up, then swap to a separate X setup with Xinerama, try it in gnome, try it in KDE, and just see how things go.

I just hope I can stick with Linux this time, I really do prefer it, but I still do some gaming (I tried installing EVE under Wine last night and it installed, but wouldn't run), use a Zune (not really Linux compatible unless I want to use USB 1.1), etc. but we'll see. Might have to install Windows in a virtual environment and see how far that takes me.

---

### Post by TheVrolok on 2011-03-22
Just as an update to anyone who may find this thread searching.

I've swapped to a separate X screen set up (without Xinerama) and obviously the dead space on the smaller monitor is gone and all Compiz/Gnome effects still work just fine.  Of course now I can't drag windows between monitors (separate X servers after all).  So next I enabled Xinerama and bam, all 3D effects (Compiz/Gnome) are gone and no longer function, but of course I can now drag windows across the monitors.  So no "perfect" set up for me yet, I guess the best I could do is to pick up another 1920x1200 monitor and run the set up with TwinView.. but I don't have a spare 300 bucks.  So, I'm going to install KDE and see what happens (I imagine the same, but we'll see).

KDE functionality was identical.  Looks like there's no current way to do Compiz+Separate X's+Xinerama.  Not a terrible situation because you could use Compiz+TwinView as long as your monitors are the same resolution, but unfortunately mine are not so with TwinView I have 150 pixels of vertical dead space on my second monitor.  I may just suck it up for now and live with that as long as I can have my Compiz.  One day, maybe I'll sell some body parts and buy 2 identical monitors.

---

### Post by yunn11 on 2011-04-19
Install chrome :grin:

---------------------------------------
[pandora charms](http://www.rabattpandora-butikk.com/pandora-butikk.html)
[pandora jewelry](http://www.rabattpandora-butikk.com/pandora-online.html)
[billig pandora](http://www.rabattpandora-butikk.com/billig-pandora.html)

---

### Post by nathema on 2011-05-13
> **TheVrolok said:**
> Just as an update to anyone who may find this thread searching.

I've swapped to a separate X screen set up (without Xinerama) and obviously the dead space on the smaller monitor is gone and all Compiz/Gnome effects still work just fine.  Of course now I can't drag windows between monitors (separate X servers after all).  So next I enabled Xinerama and bam, all 3D effects (Compiz/Gnome) are gone and no longer function, but of course I can now drag windows across the monitors.  So no "perfect" set up for me yet, I guess the best I could do is to pick up another 1920x1200 monitor and run the set up with TwinView.. but I don't have a spare 300 bucks.  So, I'm going to install KDE and see what happens (I imagine the same, but we'll see).

KDE functionality was identical.  Looks like there's no current way to do Compiz+Separate X's+Xinerama.  Not a terrible situation because you could use Compiz+TwinView as long as your monitors are the same resolution, but unfortunately mine are not so with TwinView I have 150 pixels of vertical dead space on my second monitor.  I may just suck it up for now and live with that as long as I can have my Compiz.  One day, maybe I'll sell some body parts and buy 2 identical monitors.

Came to the same conclusion in [this thread]("http://ubuntuforums.org/showthread.php?p=10772784").

---

