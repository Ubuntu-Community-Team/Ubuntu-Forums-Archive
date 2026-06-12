---
title: "Improving speed."
date: 2008-12-19
forum: Desktop Environments
---

### Post by TheHybrid520 on 2008-12-19
Is there anyway to speed up Ubuntu? I love ubuntu but I find my self using Windows to watch youtube videos or listen to music, and that is just hurting my experience with this operating system.

---

### Post by keithld on 2008-12-19
Could you provide a bit more details on the "Speed Problem" **TheHybrid520**???..

I see no difference when I watch vids on Youtube either with WindowsXP or Ubuntu 8.10, neither with listening to CD's or using Winamp on XP or Songbird with Ubuntu to listen to my favorite online stations...

---

### Post by TheHybrid520 on 2008-12-19
Well I noticed a lot of hiccups while watching vids while using Firefox. I also noticed loading up files while in ubuntu is slower just right clicking and changing desktop background takes a few seconds to load and songbird is sluggish as I scroll through my music list unlike in Windows XP where everything runs fast without a hiccup or a lack of speed, when I want something to load.

My pc requirements are above the quota on development site.

---

### Post by keithld on 2008-12-19
I have to agree with you on some of the "Programs Sluggishness" like starting etc. (Open Office is slow on both Windows & Ubuntu for me) I haven't tried changing backgrounds but when I change "Themes" it's instantaneous...

I actually noticed this stuff a few Updates ago... I think since installing Ubutunu around a month ago there have been about 5 or more updates... Firefox seems about the same for me either way tho it is a bit faster loading etc. with Ubuntu...

I kinda figured it was the Updates that were causing a few programs to run a bit slower...

---

### Post by TheHybrid520 on 2008-12-19
I was thinking about switching to Fedora 10 or SuSe 11.1 to see if it has improve speed or not.

Not that you mention it I refuse to use Openoffice on ubuntu since it's so slow and sluggish it isn't even worth it for me, while on Windows it runs fast and works fine.

If there is a way I can fix the sluggishness of the OS then I'll be happy, I was hoping there was something I can do.

---

### Post by keithld on 2008-12-19
Well I think once some of the Vets here read this they may have some "Tweaks" that may get you more speed...

---

### Post by TheHybrid520 on 2008-12-19
Well that would be nice :popcorn:

---

### Post by Sorivenul on 2008-12-20
As far as Firefox goes [this tutorial]("http://www.ubuntugeek.com/speed-up-firefox-web-browser.html") may be of interest, though I have no issues myself.

As far us improving application start-times and such, ["preload"]("http://www.techthrob.com/tech/preload.php") may be a good option, even if you have fairly new hardware. I notice the difference with preload on my older hardware more than my new hardware, but there is still a difference both ways.

---

### Post by AmericanYellow on 2008-12-20
Suggestion: 

If you just happen to be running Compiz, turn it off. I slows down window rendering and extremely slows down Firefox.(most noticeable on pages that utilise Flash eg. Youtube)

---

### Post by zika on 2008-12-20
try this:
1. switch to metacity (without compositing manager if You want it the fastest or with if You can not live without effects)
2. install preload
3. System->Administration->Services->CPU frequency manager (powernowd) (uncheck)
4. use writeback for Your disk(s).

---

### Post by Donalb on 2008-12-24
You can significantly speed up the start-up time of Open Office by reducing the number of Undo operations. The default for OOo Writer allows 100 Undo operations. I reduced mine to 50 and cut the load time by about half also. I wrote a 30,000 word thesis last year, I don't think I ever needed more than about 10/15. 
OOo>Tools>Options>Memory>Undo [Number of Steps]
Possibly there's a similar setting for each of the other apps.
Regards
Haven't tried Preload myself but I'm planning to on a new laptop.

---

### Post by redsoxreed on 2008-12-24
You could ditch Gnome and install icewm, TWM, or fluxbox.  *That[I]*[/I] would go fast.

---

### Post by Wisp558 on 2008-12-24
Amen to fluxbox. I'm using it now, and it *flies*.

---

