---
title: "Fluxbox Project, Can It Be Done?"
date: 2010-10-04
forum: Desktop Environments
---

### Post by meditatingfrog on 2010-10-04
Well, i'm looking at improving ubuntu i guess, and one of the things i'd like to explore is trying to get it to be more efficient.  i realize this is probably a sysyphian task, but hey, it's something to do.

i installed fluxbox to investigate how much ram it would use, and noticed that a clean boot of ubuntu using fluxbox used under 400MB, this is better than a clean boot of ubuntu using gnome, which hovered around 900MB for me.  

i'm not really sure what is going on here, to be honest.  but i know i want to maximize ram in order leave more available for other applications, particularly chrome which i tend to have a plethora of tabs open at any given time.  

so here's my problem.  what i absolutely need from fluxbox in order to use it, is i need a color scheme similar to what i'm using with gnome at present.  a low intensity, high contrast, darker color scheme.  the problem is, i am presently using super+m with compiz to enable this in gnome (because i can't specify the color of chrome any other way) thereby just inverting the high intensity, high contrast lighter color scheme.  so is this even a configurable option in fluxbox?  or am i wasting my time, and should i just try to learn python?

these other two i think are doable.  but i would also want to get working at some point:  

suspend to ram (s3).
volume control (alsamixer in a terminal might be just fine).

and wireless, which i think i solved, but haven't tried with wicd yet (nm-applet was flaky for some reason).

anyway, this is my project, but i can't do it alone, so if anyone is out there that is willing to help, it would be greatly appreciated.

P.S. i'm using 9.10 currently.

---

### Post by The Bean on 2010-10-19
Hi m*frog!
Years ago I used Fluxbuntu a short time but on my old laptop runs antiX 8.5 with fluxbox today. I read it's hard to replace gnome by fluxbox (but never verified myself). If you don't shy the effort it is possible. Fluxbox is extreme flexible and adjustable.
Some links that could help you:
Fluxbox styles [*http://tenr.de/styles/*]("http://tenr.de/styles/")
How to modify them [*http://tenr.de/howto/style_fluxbox/style_fluxbox.html*]("http://tenr.de/howto/style_fluxbox/style_fluxbox.html")
Fluxbox wiki [*http://fluxbox-wiki.org/index.php?title=Fluxbox-wiki*]("http://fluxbox-wiki.org/index.php?title=Fluxbox-wiki")
more styles [*http://customize.org/fluxbox*]("http://customize.org/fluxbox")
Also it is very useful to adjust your gtk theme. [*This should help you*]("http://www.google.com/search?hl=en&source=hp&q=modify+gtk+theme&btnG=Google+Search");-)

Hope you will have success! MfG Bean

Edit reveals: My antiX with fluxbox, wbar, pcmanfm and conky uses less than 50MB after booting ;)

---

### Post by wojox on 2010-10-19
Have you tried [#! Crunchbang]("http://crunchbanglinux.org/").

I know it's Openbox but still a good window manager.

---

### Post by The Bean on 2010-10-20
I think meditatingfrog needs more eye candy than openbox can offer but its still a good and very lightwight wm. Used #! on a stick but currently it is crashed and the alternative will be antiX. [antiX]("http://antix.mepis.org/index.php?title=Main_Page")

---

### Post by Megaptera on 2010-10-20
Have you looked at Linux Mint Fluxbox? It's a Community Edition based on Mint 9 (based on Ubuntu).
Their webpage isn't loading for me at the moment, but I'll try to add a link later.

---

### Post by cascade9 on 2010-10-21
> **meditatingfrog said:**
> Well, i'm looking at improving ubuntu i guess, and one of the things i'd like to explore is trying to get it to be more efficient.  i realize this is probably a sysyphian task, but hey, it's something to do.

i installed fluxbox to investigate how much ram it would use, and noticed that a clean boot of ubuntu using fluxbox used under 400MB, this is better than a clean boot of ubuntu using gnome, which hovered around 900MB for me.  

Is that RAM actually in use or cached? 

Persoanlly, I'd go for a minimal install + gnome (or even Xfce). Amazing how much RAM that frees up, without needing to go to fluxbox/lxde/etc.

---

### Post by Darknezz41 on 2010-10-21
Buy more memory because every year the need for more ram from apps continues to rise. I have 4 gb of 1333 Gskillz memory and I use Linux Ultimate Edition x64 and I push it just a little past 3gb of use on a regular basis. I know it seems arrogant to suggest that but really today the apps are starving for it. Or we are just multi tasking to the extreme these days. I think both.

---

### Post by Megaptera on 2010-10-21
> **Megaptera said:**
> Have you looked at Linux Mint Fluxbox? It's a Community Edition based on Mint 9 (based on Ubuntu).
Their webpage isn't loading for me at the moment, but I'll try to add a link later.

Here's the link  [http://blog.linuxmint.com/?p=1523](http://blog.linuxmint.com/?p=1523)

---

### Post by Simian Man on 2010-10-21
[LIST]
[*]How much RAM do you have?
[*]Is that 900 including the cache? (It seems a bit high)
[*]How much do you use with/without compiz? (metacity itself is very light)
[*]Chrome is a memory hog, why not try Midori, Epiphany or even Firefox?
[/LIST]

---

### Post by phredbull on 2010-10-25
> **Megaptera said:**
> Have you looked at Linux Mint Fluxbox? It's a Community Edition based on Mint 9 (based on Ubuntu).
I tried it out as a live USB on my humble 2gHz P4 512mb ram laptop, and it was really snappy, much more than the Ubuntu Gnome (w/Compiz) that I have installed. I could imagine a full install would be even better. The only problem was that the USB stick took over an hour to boot.:mad:
But based on my short experience, I'd recommend it!

---

### Post by Megaptera on 2010-10-26
Glad it was of interest!

---

