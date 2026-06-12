---
title: "Laggy Scrolling in some pages (Using Firefox 3.0.5)"
date: 2008-12-22
forum: General Help
---

### Post by owoaux on 2008-12-22
In some pages like [http://ubuntulinuxhelp.com/](http://ubuntulinuxhelp.com/) the scrolling lags awfully.
I have smoothscrolling enabled + compiz running. 
I have tried disabling desktop effects but the laggy scrolling stayed. :/

edit: i disabled smooth scrolling and it's better but still not as speedy as it must be and i used to be in Windows XP.

---

### Post by SlidingHorn on 2008-12-22
as overly simple as it may sound, I think it could just be the content of the pages.  Just enabling the flash element on the page (using flashblock here) caused a noticeable slowing in the scroll speed.

---

### Post by owoaux on 2008-12-22
> **SlidingHorn said:**
> as overly simple as it may sound, I think it could just be the content of the pages.  Just enabling the flash element on the page (using flashblock here) caused a noticeable slowing in the scroll speed.

It's scrolling smoothly with Opera.
So, I have a problem with Firefox. And, yes, it seems the problem appears in pages with flash elements.

---

### Post by SlidingHorn on 2008-12-22
Check out Swiftweasel...basically it's an optimized build of f*ref*x for linux without any proprietary bs

then install flashblock and adblock plus ;)  maybe even noscript if you're really pressed

not saying that will solve your problem, but it can only help

---

### Post by owoaux on 2008-12-22
> **SlidingHorn said:**
> Check out Swiftweasel...basically it's an optimized build of f*ref*x for linux without any proprietary bs

then install flashblock and adblock plus ;)  maybe even noscript if you're really pressed

not saying that will solve your problem, but it can only help

I want to use Firefox as it is.
And I don't want to disable any flash elements in the pages I visit 'cause they are nice looking :-)

---

### Post by kostkon on 2008-12-22
In most cases Flash ads with lot of animation cause lagginess on some pages.

But in this case ([http://ubuntulinuxhelp.com/](http://ubuntulinuxhelp.com/)), the site uses a non-repeated background. From my experience *Firefox* tends to have jerky scrolling on pages that have their background set to non-repeat (a CSS rule).

---

### Post by ajgreeny on 2009-03-15
I had a similar problem in FF on mint6 which I am looking at (not as good as ubuntu 8.04) and found a post that stopped it happening with an addition to my xorg.conf file.  I run an ati 9200SE card and it may be specifically for that card but these are the two lines added to my already edited conf file.
```
Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    DefaultDepth    24
    SubSection "Display"
        Modes        "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    Option "AccelMethod" "EXA" #This line added to speed up scrolling in some applications.
    Option "MigrationHeuristic" "greedy" #This line added to speed up scrolling in some applications.
    EndSubSection
EndSection
```

---

### Post by sdennie on 2009-03-15
Scrolling speed in FF3 is also influenced by the system theme you are using.  Compiz certainly doesn't help when it comes to smooth scrolling but, using a faster gtk theme (as measured by gtkperf) can make a huge difference.  I found smooth scrolling so unpleasantly choppy with the default Ubuntu theme that I turned it off.  However, using the Nimbus theme (which, gtkperf shows to be about 2x faster to draw widgets than the default theme), smooth scrolling is as smooth, if not smoother, under compiz than the default theme is under metacity.

---

