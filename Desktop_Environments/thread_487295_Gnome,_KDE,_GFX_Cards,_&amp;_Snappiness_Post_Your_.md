---
title: "Gnome, KDE, GFX Cards, &amp; Snappiness: Post Your Notes"
date: 2007-06-28
forum: Desktop Environments
---

### Post by wyth on 2007-06-28
What's the best gfx card to use for your desktop environment?  Or what's the best desktop environment for your gfx card?  It seems each gfx card will work differently with each desktop environment, depending on which drivers are being used, so how do we know what works best with what?  

That's what this thread is meant to help us find out -- which setup is snappiest.  If people post their results, it could be a good resource for others who are looking for the best drivers/gfx cards/desktop environments/general setup for their rigs (or rigs to be).  Just to keep this relatively focused, let's try to focus on Gnome and KDE; yes, if we really want true speed you could use open box or something, but I want to keep this thread focused on the main offerings, and aim it towards new users.

So I'll start: I have a Radeon R250 card on a laptop.  It's old and limited.  I used to use the proprietary ATI drivers up through Edgy.  With those, KDE was faster than Gnome and Windows.   
[INDENT]***ATI proprietary drivers + ATI R250: KDE fastest, then Windows, then Gnome***
[/INDENT]As of Feisty, the proprietary drivers no longer support my card, and I went to the open source drivers.  Now Gnome is faster than KDE on my laptop, but Windows is snappier than both.
[INDENT]***ATI open source drivers + ATI R250: Windows fastest, then Gnome, then KDE***
[/INDENT](This post was inspired by [this thread]("http://ubuntuforums.org/showthread.php?t=477483") about the relative speed and snappiness of Ubuntu vs. Windows.)

Post away!

---

### Post by wyth on 2007-06-29
giving this a bump

---

### Post by Happy_Man on 2007-06-29
Hmm...... I'm not sure. Sure, Windows was pretty fast on my old gfx card (Nvidia GeForce 4 MX 420) at first, but then Windows slowed down, as Windows is always gonna do, but I don't think that was my gfx card's problem. Ubuntu runs about as fast as my fresh Windows install did, whether I'm in GNOME, KDE, Fluxbox, Openbox, or XFCE. I use the Feisty nvidia-glx drivers, and the ride keeps getting smoother. Compiz Fusion never looked better. Now then, I'm off to go minimize stuff so I can watch the animations. Ta!

---

### Post by chronic on 2007-06-29
iv found that linux isn't as snappy as my well configured xp install but I use Compiz Fusion (which looks fantastic btw).

Im using a x800 gt all in wonder, although ATI don't seem to support all in wonder cards under linux .Is there a way to do this? anyway Im using fglrx with XGL which is a lot faster than the open source drivers and iv found them to be a lot more stable as well. beryl used to run slower on the open source drivers.

> Hmm...... I'm not sure. Sure, Windows was pretty fast on my old gfx card (Nvidia GeForce 4 MX 420) at first, but then Windows slowed down, as Windows is always gonna do, but I don't think that was my gfx card's problem. Ubuntu runs about as fast as my fresh Windows install did, whether I'm in GNOME, KDE, Fluxbox, Openbox, or XFCE. I use the Feisty nvidia-glx drivers, and the ride keeps getting smoother. Compiz Fusion never looked better. Now then, I'm off to go minimize stuff so I can watch the animations. Ta!

windows xp and below doesn't use 3D acceleration. all the "effects" are 2D and i think that things like the shadows etc. are done on the CPU. so your gfx card wont make the slightest bit of difference.

and i dont that microsoft even knows why windows slows down over time :p

---

### Post by wyth on 2007-06-29
I'm actually in the process of re-installing just a command-line system (Feisty), on which I'm adding kde-core, and then just the apps I need.  I tried it alongside ubuntu-desktop, and at least in my case (ATI Radeon R250), it was significantly faster.  So I made up a list of what Gnome apps I used, what KDE apps I used, and what DE-independent apps I used.  The independents won out by a long shot, with Gnome and KDE coming in dead-even.  That coupled with the fact that I literally could just work faster on KDE sort of sealed the deal.

So I wonder if more people with ATI cards (especially older ones) have better luck with KDE than Gnome.

This isn't a Gnome-slam; I used it happily.  But you gotta work with what works.

---

### Post by wyth on 2007-06-30
bump

---

### Post by deepclutch on 2007-07-01
with my nvidia 7300GT or on-board intel,I can say that GNOME is much faster than Kde.obviously kde needs a little more power and memory as a hell lot of "K" things u need to power up.
Yes.GNOME seems faster in most attempts in my computers i tried with.Kde is  a little sluggish than GNOME.
I am sure this DE comparing is illogical,the speed depends on- which DE is lighter will be faster,and gtk2 is as fast or better than qt compiled apps.so that also no chance.
..and GNOME works for me as usual,as stable and simple as it is always.

---

### Post by wyth on 2007-07-01
Deepclutch: Gnome is faster with the nvidia, right?  

I just removed Gnome and installed most of Kubuntu (installed kde-core and then added on top of that, but it ended up being most of Kubuntu). With my old ATI card, my desktop is *significantly *snappier.  I'm wary of stating that because as soon as someone says something like that, the comments come crawling out of the cracks about how it's only a *perceived* difference.  Perceived or not, when I make a mouse click or type something in KDE (with an older ATI card and a gig of ram), things happen *right now.*  Also, my fan isn't kicking in nearly as much or for as long.  

But that's why I started this to begin with.  Score one for old ATI+KDE, and score one for Nvidia 7300GT+Gnome.

---

### Post by wyth on 2007-07-07
Bumping this.  A week with KDE on an ATI video card has me mostly convinced KDE is better for my setup.  I sometimes find that *typing* lags a bit, but that may be something else.  Otherwise everything is just a couple steps snappier than I could get it on Gnome.

---

### Post by orb9220 on 2007-07-07
I find the sluggish typing is usaually a result of java. Am I wrong or does java in linux seem more like on valium than the windows conterpart?

For me Java seems to slow down any desktop Gnome or KDE? Has anybody else get this feeling?

---

### Post by wyth on 2007-07-09
Do you mean Java for OpenOffice, or Java overall?  Because I'm having the slow typing issue all over (and disabled it in OpenOffice).  I posted about that issue [here]("http://ubuntuforums.org/showthread.php?t=495675").  does Java in general shut down performance overall?  KDE is snappier for me, but if the typing input is going to be this slow, I'll probably head back to Gnome and then just hang out there on occasion until I can get a new laptop in a few years.

---

### Post by orb9220 on 2007-07-09
For me it is perception but I find in gmail,firefox,ktorrent that the sluggishness appears to be java.

I find that java  on xp running Firefox,gmail,utorrent,bitcomet,OpenOffice,etc... that use java appear a bit snappier and responsive than the linux version.

I hope this is wrong but I notice it every time I switch back and forth between Ubuntu and XP.

---

