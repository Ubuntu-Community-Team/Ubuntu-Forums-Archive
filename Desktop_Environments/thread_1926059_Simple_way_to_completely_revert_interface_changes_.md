---
title: "Simple way to completely revert interface changes after maverick?"
date: 2012-02-15
forum: Desktop Environments
---

### Post by Dreamer Fithp Apprentice on 2012-02-15
I've been using Ubuntu primarily for a couple of years now, but I am for the first time, about ready to give up on it. Every time I try updating past 10.10 the desktop, windows and so on, basically everything to do with the user interface, goes to [censored][bleep]. I've tried following instructions in a lot of the threads that purport to restore the old look but none of them seem to address more than a small part of the changes. I want my old themes. I want my old scripts for toggling color schemes and font sizes to work. I want my old tweaked gnome panels back.  I'm tired of half assed "kinda like it used to be" work arounds. As it stands right now, nothing past 10.10 is worth a darn to me. But there are some things I want that require apparently a newer version. So I'm beginning to think it will be less effort to try another distro altogether. Maybe go back to Sabayon or try BSD. It looks like restoring the old UNBROKEN user interface is going to be as much work as learning BSD would be so maybe my time would be better spent there. Is there any way out of this nightmare or is it just FUBAR?

---

### Post by cwklinuxguy on 2012-02-15
Are you talking about the fact that 11.04 had the transition to Unity, and the somewhat poor "Gnome Classic" session? If you really want good old fully functional Gnome 2 back, my advice is to back up your data (all your scripts, documents, photos, music, etc.) to an external hard drive, download Ubuntu 11.10 and do a fresh install completely wiping your previous installation, and then [install]("http://wiki.mate-desktop.org/download") MATE Desktop Environment (the Gnome 2 fork). I'm also working on an Ubuntu-based [distro]("http://paradiseos.wordpress.com") that will use MATE as it's main UI (but that's not ready for prime-time yet). Hope this helps you, and sorry if I misunderstood your question.

---

### Post by Dreamer Fithp Apprentice on 2012-02-15
Thank you. This looks promising and I'll tinker with it for a while. At least some of the changes date from whatever one upgrade past 10.10 was. I forget the numeral but I thought it was a 10.nn, maybe 10.40, not an 11.nn. Sorry, if I'm not too clear.  I'm still a little uncertain on the exact roles of x, compiz, and so on. Part of what I want back is the clearlooks theme, or at least some components of it and I've read it won't work with Gnome 3, which I find quite surprising.

 You said on top of a fresh installation, but since it wouldn't take long anyway, and there was nothing to lose but an installation I'd otherwise wipe anyway (I have a 10.10 boot partition I use and another boot partition where I keep trying to make whatever is the latest standard version, currently Oneiric, less obnoxious) I tried those commands on an Oneiric installation I had built up from the minimum install and had already managed to partially revert some of the changes by following the steps in two other threads here. Didn't see any difference and I still couldn't get Clearlooks.

So then I tried applying the changes to a fresh installation of the mimimal install of Oneiric with only synaptic, nautilus, nano, and x11-xserver-utils added. So far I haven't been able to get any graphical programs at all to run on that.

Probably I shouldn't be trying to learn how to do TWO different non-standard things at the same time. So next I suppose I'll try either try a full regular installation of Oneric and apply your modifications and try to get that working before I try to see if I can do the same thing with a lean-built-from-the-bottom-up-with-mini.iso installation. Unless, before I get to it, I catch on to what I'm missing in this one that I need to get graphical aps to work.

Good luck with the distro. I'll bookmark it.

---

### Post by cwklinuxguy on 2012-02-15
Nope. Versions come out every 6 months, and are always in the format of yy.mm (e.g. version 10.10 was in October of 2010). The next version after (6 months later) was version 11.04 (April of 2011).

x11 is basically the framework that is used to produce graphical images in Linux...but that's the very very simple way of putting it...I'm not quite technical enough to give you a better explanation. Compiz is a compositing Window Manager, which is what can produce all those effects that you see people showing off on YouTube like the Desktop Cube, fire paint, etc. Some of them are a bit useful, but most of the effects are just eyecandy. Compiz also happens to be what Unity is built on (which, by the way, was a very bad idea on Ubuntu's part). For that reason, it is highly inadvisable to tweak your Compiz settings at all--this has extreme potential to break your system. 

I'm a tad lost as to what you've been messing with, but my advice is to just try MATE. It's got some bugs, and it's not QUITE up to the stability level of the old Gnome 2.3x, but it's getting there. You can still install Clearlooks in MATE from the Gnome website, however I am unsure of how well it works--changing themes in MATE sometimes breaks the panels. However, as long as you are careful when you go poking around, you should be fine.

---

### Post by Dreamer Fithp Apprentice on 2012-02-16
Thanks. I have Mate running in my Oneiric now. It is promising.  Not an install-and-forget-it-drop-in-replacement as I will need to find new names of things like gconf2 to get my scripts working again but it is getting there. Not gonna mark this solved yet, but maybe I won't need to abandon Ubuntu yet. We'll see. My god, how I hate the new g3/unity cutesy-poo user interface.  I'll give Mate a good try and if it doesn't work adequately I'll give Debian or BSD a try.

---

### Post by cwklinuxguy on 2012-02-16
I'm glad it seems to be going well for you. I'll also be sure to let you know when my distro is stable enough for everyday use.

---

### Post by Dreamer Fithp Apprentice on 2012-02-16
I'm also trying the route of using another of the alternate session types at log in. I forget what the menu there calls it, but I've seen that session type called "gnome panel" elsewhere and it looks more like a trad desktop gui. For a specific example of the kind of problems I've had with Ornery/Gn3/Unity that have been pushing me away from it/them I made a separate thread about gconf2 commands in Oneiric here
 [http://ubuntuforums.org/showthread.php?t=1926788](http://ubuntuforums.org/showthread.php?t=1926788)

---

### Post by mister_p_1998 on 2012-02-17
I'm not the only one then... still running Hardy at home and Lucid at work. Now and again I install the newer versions in VirtualBox only to walk away shaking my head. ALL the friends I recommended Ubuntu to are now running Mint.

---

### Post by 3rdalbum on 2012-02-17
> **Dreamer Fithp Apprentice said:**
> It looks like restoring the old UNBROKEN user interface is going to be as much work as learning BSD would be so maybe my time would be better spent there. Is there any way out of this nightmare or is it just FUBAR?

There's a 0% chance that everything will go back to the way it was. This is computing - things change and it's inevitable.

Gnome 2 is no longer maintained by its developers. A distro switch might buy you some time, but ultimately Gnome 2 will be gone from all distros within a few years; except of course for distros that will no longer be updated.

The MATE desktop environment is Gnome 2 on life support, but I don't think it will be maintained for long either.

My honest best advice for you would be to either stick it out with Unity and adapt yourself to it. It's certainly very different to Gnome 2 but there are some useful features that will make your computing more efficient when you use them; for instance, the search field.

Another thing you could try is a different desktop environment. Gnome Shell, KDE and XFCE are in the repositories. Or try Gnome Fallback Session - it's like the Gnome 2 panels based on Gnome 3 infrastructure. This may not be a valid long-term option either, and by default it looks more like Gnome Shell, but if you alt-right-click on the panels you can tweak it more like Gnome 2.

So, basically, the long-term solution is to get used to the new software. All computer users have to get used to new software eventually as it's the nature of the industry - there's no way to make yourself an exception.

---

### Post by Dreamer Fithp Apprentice on 2012-02-18
I'm going to mark this as solved because a few days of research has convinced me that ALL of us posting in this thread, including me and the other disgruntled, and the "roll over, take it, and STFU" crowd are operating under a misconception born not of Canonical's programming efforts so much as the poor job they did of COMMUNICATING what happened, why it happened, and how to deal with it. Essentially, the old interface IS STILL THERE. It just takes a bit of tweaking to get it back. If you've written a lot of custom scripts like I have, it will take a little more tweaking but it still looks pretty doable. See my post #8 here:
[http://ubuntuforums.org/showthread.php?p=11698572#post11698572](http://ubuntuforums.org/showthread.php?p=11698572#post11698572)

---

