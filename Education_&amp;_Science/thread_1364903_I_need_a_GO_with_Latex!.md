---
title: "I need a GO with Latex!"
date: 2009-12-26
forum: Education &amp; Science
---

### Post by madmax.santana on 2009-12-26
I am trying to switch to linux completely. So far, my experience with free source software has been perfect... Plus the satisfaction that I am not pirating software! ;)

Ok... I need to know how to use Latex. I aint asking for a tutorial at this time, just how should I start. I guess I install the latex engine, then an editor and then several plugins. But can anyone please give me a good step by step procedure and also list the apt-get packagenames....

Thanking in anticipation!!!

---

### Post by perroazul on 2009-12-26
about the latex packages:
```
sudo apt-get install texlive-base texlive-latex-base texlive-latex-extra 
```

about the editor, there are many flavors. it really depends on what you like. if you do a search for latex editors, I'm pretty sure that you will find existing threads about that :)

---

### Post by csaratchand on 2009-12-27
1. If you use LaTeX extensively then:
```
sudo apt-get install texlive-full
```
2. Kile is the most feature full editor for LaTeX. But it uses some KDE packages. You can use it. 
```
sudo apt-get install kile
```
3. Get back if you have any related problems.

---

### Post by waspbr on 2009-12-27
You may also want to check out lyx, it is a simplified latex editor. The outputs are very much the same and you can also input latex codes in it. 

it already comes with a tutorial and user guide, definitely worth checking out. 

When I used to work with latex directly I used an editor called winefish. Nowadays I stick with lyx.

---

### Post by earlycj5 on 2009-12-27
> **csaratchand said:**
> 1. If you use LaTeX extensively then:
2. Kile is the most feature full editor for LaTeX. But it uses some KDE packages. You can use it.

TexMaker comes awfully close if it isn't just as 'full', and it comes without KDE packages.

I use RKWard so KDE packages aren't an issue for me, but to say Kile is the most full, well, I think is a bit disingenuous having used both Kile and TexMaker.

To the OP, as it's been stated, there are SEVERAL editors to choose from. They've been discussed at length here.  Try them and see what suits you.

---

### Post by madmax.santana on 2009-12-27
Thanks a lot buddy! That was an awful lots of help!!! Thanks again!

---

### Post by Wolf-Ekkehard on 2009-12-29
Did you get that installed madmax???

I am trying to install LaTeX and Kile, both of which I had working on previous versions of Ubuntu.  The install keeps failing at the package texlive-latex-base.  A quick look in /tmp/fmtutil.xxxxxxxx reveals that the installer cannot find the file ushyph.tex.  Leads to a "fatal error" and from there on its downhill...  It is actually even hard to get rid of the failed package again (apt-get install -f won't do the trick)

As I see you're using 9.10 Karmic Koala too, so if you got it to work, I'd be highly interested in what you did to get to that point.

---

### Post by madmax.santana on 2009-12-30
> **Wolf-Ekkehard said:**
> Did you get that installed madmax???

I am trying to install LaTeX and Kile, both of which I had working on previous versions of Ubuntu.  The install keeps failing at the package texlive-latex-base.  A quick look in /tmp/fmtutil.xxxxxxxx reveals that the installer cannot find the file ushyph.tex.  Leads to a "fatal error" and from there on its downhill...  It is actually even hard to get rid of the failed package again (apt-get install -f won't do the trick)

As I see you're using 9.10 Karmic Koala too, so if you got it to work, I'd be highly interested in what you did to get to that point.
Haha man I am not a professional writer or something. I am just a student and most of my works are down greatly by Openoffice.org suite of applications. However, I am an enthusiast. I heard of latex, looked at it, installed it on Windows and really liked it. So I wanted to run it on Linux, I have installed the package latex-full but haven't yet tested it. Or to be honest, I didn't get the time to try it... Fall Exams dude!!! :D
Anyway, I'll keep in touch through the Ubuntu Community and surely letcha know when I try it...
And as for now, I suggest you look at some other Latex editor packaged, maybe lyx, try them. What I perceive of your problem is this:
> 2. Kile is the most feature full editor for LaTeX. But it uses [COLOR=Red]some KDE packages[/COLOR]. You can use it. 
Lemme tell you, KDE is one helluva difficult desktop manager to manage, at least more tricky than GNOME, and so are the packages of KDE. Maybe Kile is causing the problem?

---

### Post by perce on 2009-12-30
> **madmax.santana said:**
> 
Lemme tell you, KDE is one helluva difficult desktop manager to manage, at least more tricky than GNOME, and so are the packages of KDE. Maybe Kile is causing the problem?

Last time I tried kile (a couple of years ago) it installed fine under gnome. However I'd start with a simpler editor (gedit?) if you are unfamiliar with Latex: fancy editors make the work flow faster, but not easier.

---

### Post by autora on 2009-12-30
what about pvc?

---

### Post by madmax.santana on 2009-12-30
> **perce said:**
> Last time I tried kile (a couple of years ago) it installed fine under gnome. However I'd start with a simpler editor (gedit?) if you are unfamiliar with Latex: fancy editors make the work flow faster, but not easier.
Haha, no offense was intended pal. It was just as it looks to me. KDE appears a bit cluttered to me, but that doesn't mean it is not good...
Have a nice time.

---

