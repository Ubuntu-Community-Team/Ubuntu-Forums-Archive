---
title: "iLife on ubunto"
date: 2006-01-15
forum: General Help
---

### Post by john123 on 2006-01-15
im not running a mac, but ive heard that it is possible to install mac programs onto linux. i just wanted to know if its possible to install apples "iLife" on ubuntu

---

### Post by pbb on 2006-01-15
I am no expert on this, but I would guess it is only possible to run *terminal applications* from the Mac on Linux, since both use the same base OS.

---

### Post by mcduck on 2006-01-15
I think you have understood it the wrong way. It's possible to install Linux programs to mac.. :)

---

### Post by jasmuz on 2006-01-15
You could also compile Mac programs to GNU/Linux

---

### Post by john123 on 2006-01-15
[QUOTE=jasmuz]You could also compile Mac programs to GNU/Linux[/QUOTE]
does that mean i could use iLife on ubuntu?

---

### Post by john123 on 2006-01-15
come on, anybody who can explain this to me?

---

### Post by lupine_nickt on 2006-01-15
Apple & i386/AMD64/EM64/etc. are binary incompatible, but the sources "can" by cross-compiled (if you're not too unlucky). You'd need to get the source code for the program, then try to compile it.

I've had a quick Google, and can't see any sources for iLife; looks like a proprietary Apple program.

So all that leaves you with is trying to get an Apple emulation program for Linux.  I've not ben keeping up with the emulator scene, so I don't know if there's anything available... anyone else?

xF,

...Nick

---

### Post by lupine_nickt on 2006-01-15
Ah. Here's the sort of thing you'd need...

[http://pearpc.sourceforge.net/](http://pearpc.sourceforge.net/)

No idea how good/bad it is. What is basically does, is pretend to the Mac program(s) that they're running on a Mac. Obviously, it can't be perfect ;). 

Anyone have any idea of how good/crap this one is? Or if there's anything better? I can think of a few Mac programs I wouldn't mind running, too...

xF,

...Nick

---

### Post by slux on 2006-01-15
I't hardware emulation and it's s l o w. That's the best there is unless you are actually running Linux on a mac in which case you can use Mac-on-Linux to run at near-native speeds.

With the new intel-macs being introduced, I guess MOL could be possible for any PC and a WINE-equivalent is also conceivable (and probably quite a bit less work) but there's no really useful way to run mac apps on x86 pcs at the moment. Not that iLife is *that* amazing IMO, try looking at the Linux equivalents for most of the apps.

BTW, even if the sources were available, it wouldn't be as easy as just compiling.

---

### Post by eq235 on 2006-10-25
I think that ubuntu needs to release the equivalent of iLife for linux - which I think is basically what UbuntuStudio is supposed to be, although I don't know if they're making much progress. The audio and video apps should come pre-bundled and configured to work with each other, as it's not that easy if you don't know what you're doing. They should release ubuntu as one distro, and the studio apps on another, so it's an optional install, just like iLife. There are enough quality apps to do this - but getting them to work right can be a pain (in my experience).

What bothers me about linux is that everyone has to go through the same steps to get everything working right - so why not just have it so those steps aren't necessary? The only way people are really going to use linux is it doesn't require anything to work properly. Most people just want to use their computer and do their work, and not have to spend their time just getting it to function. For a linux savvy person, it's no big deal to work in the terminal and mess around for hours, and that's fine, if that's their interested. But I think the average user sees the computer as a tool to do things with, and not as a project in itself. If I had the money, I would hire a small team of software engineers to make ubuntu as ready-to-go as os x. I think it would only take maybe 3 or 4 people if it were their full time job.

---

### Post by az on 2006-10-25
> **eq235 said:**
> ngs with, and not as a project in itself. If I had the money, I would hire a small team of software engineers to make ubuntu as ready-to-go as os x. I think it would only take maybe 3 or 4 people if it were their full time job.

There are fewer than ten people from Canonical working full-time on the Ubuntu distribution.  However, there are a few thousand people who develop code for all of the applications in Ubuntu.

Some projects zoom along, while others take some time or fizzle out.  It depends on whom is out there who is able to scratch their itch.

If you really want to help out, check out some of the specs for the next developer summit and try to contribute by adding your ideas and helping them happen.  A lot of those specs are for making things easier for the end user.
[https://launchpad.net/distros/ubuntu/+specs](https://launchpad.net/distros/ubuntu/+specs)

---

### Post by Doovoo on 2006-10-25
You were wise to ask this here, because anywhere else you'd almost certainly be met with "stfu n00b." 

Anyway, although you can't run iLife, you can get the equivalent of it.

iPhoto = [F-Spot]("http://f-spot.org/Main_Page")
iMovie = [Kino]("http://www.kinodv.org/"), [Diva]("http://www.diva-project.org/")
iDVD = [DVD Styler]("http://dvdstyler.sourceforge.net/index.html")
Garageband = [Audacity]("http://audacity.sourceforge.net/"), [Rosegarden]("http://www.rosegardenmusic.com/"), [Ardour]("http://ardour.org/"), [Wired]("http://wired.epitech.net/")
iWeb = There's lots of HTML IDE's out there, this doesn't need explaining.
iTunes = [Banshee]("http://banshee-project.org/Main_Page")

---

