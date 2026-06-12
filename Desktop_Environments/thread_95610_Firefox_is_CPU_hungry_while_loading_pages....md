---
title: "Firefox is CPU hungry while loading pages..."
date: 2005-11-26
forum: Desktop Environments
---

### Post by bb002 on 2005-11-26
No matter what I'm doing or what page I visit, firefox is using a 1/3 of the CPU whenever it is loading a page. If a page happens to be extremely slow to load I'm stuck with 33% cpu usage for firefox to practically be idling. I'm probably a freak but I often have 7 or more different windows/tabs open at the same time. If some of those windows/tabs get stucking open a slow to load or large page then firefox-bin has effectively brought my system to a halt with 100% cpu usage. I'm lucky to be able to open a terminal to kill firefox off or even to get alt+ctrl+backspace to work.


I really need a solution to this. I'm currently working around the problem by forcing myself to use only one window but it is really cramping my style.

---

### Post by RAOF on 2005-11-26
You could possibly use the Firefox 1.5RC3.  It's faster in general.  There's a howto [here]("https://wiki.ubuntu.com/FirefoxNewVersion?highlight=%28firefox%29").

---

### Post by Perfect Storm on 2005-11-27
My suggestion is that you switch to epiphany

```

sudo apt-get install epiphany-browser epiphany-extensions

```

---

### Post by Brent Dax on 2005-11-27
[QUOTE=bb002]No matter what I'm doing or what page I visit, firefox is using a 1/3 of the CPU whenever it is loading a page.[/QUOTE]
Do you have any extensions installed?  If so, try disabling them.

Are there any particular pages which cause the CPU to jump?  Although I've never seen such a thing, I suppose a particularly plugin/Javascript-happy page could be eating CPU.

---

### Post by bb002 on 2005-11-27
no deb huh? When is the 1.5 stable gonna be out? anyone know? I checked the road map and it only said "2005". Sure there is only about 34 days left of 2005 but a more precise date would be nice. :)

The howto is pretty straight forward but I would prefer to stick with using a deb package.

---

### Post by dto on 2005-11-27
I seem to recall reading in the last couple of days that 1.5 is supposed to be out on the 29th of this month (next Tuesday).

---

### Post by bb002 on 2005-11-27
Wow took me a whole hour and a half to make my last post.....Seriously. Went and made myself a sandwhich and forgot all about my incomplete post...hehe. Seems there some posts while I was sitting at the "Reply to Thread" page. So here are my answers.

> My suggestion is that you switch to epiphany
epiphany and I rather dislike each other. I happen to prefer IE over epiphany. It may have been the version that I was using (dunno what version it was, it was back when i used mandriva) but it seemed like if i sneezed epiphany crashed. Besides I love firefox too much to just switch to something else.

> Do you have any extensions installed?
No I don't think so, I don't even think I've installed flash yet. The only thing firefox lists is "English (GB) Language Pack 1.0.4" and I can't do anything to it.Though by the name of it I don't think I would want to anyhow.

> Are there any particular pages which cause the CPU to jump?
I assume you didn't see where I said "No matter what I'm doing or what page I visit" but I'll clarify. By page I mean it could be an image, plain txt file, or a html page. As long as that round thing in the upper right corner of the browser window is active (indicating a webpage is loading) firefox-bin is eating up 33% of the processor and that's per window/tab that is loading a page.

---

### Post by Perfect Storm on 2005-11-27
> epiphany and I rather dislike each other. I happen to prefer IE over epiphany. It may have been the version that I was using (dunno what version it was, it was back when i used mandriva) but it seemed like if i sneezed epiphany crashed. Besides I love firefox too much to just switch to something else.

That's alright, no hard feelings from me ;)
Though Epiphany is rock stable on my system and very fast. I think you should give it a try and if you don't like it remove it. :)

---

### Post by eeried on 2005-11-27
On the ubuntu Wiki they say better install Firefox from mozilla.org (so a binary tar.gz file) rather thean the Ubuntu deb package because the original app is faster.

I'll try that, and then yuou don't have to wait for the 1.5 Ubuntu package (you still have to wait for the stable 1.5 version from mozilla.org though, not quite ready yet! :cool: )

Cheers,

---

### Post by dcstar on 2005-11-27
[QUOTE=bb002]No matter what I'm doing or what page I visit, firefox is using a 1/3 of the CPU whenever it is loading a page. If a page happens to be extremely slow to load I'm stuck with 33% cpu usage for firefox to practically be idling. I'm probably a freak but I often have 7 or more different windows/tabs open at the same time. If some of those windows/tabs get stucking open a slow to load or large page then firefox-bin has effectively brought my system to a halt with 100% cpu usage. I'm lucky to be able to open a terminal to kill firefox off or even to get alt+ctrl+backspace to work.


I really need a solution to this. I'm currently working around the problem by forcing myself to use only one window but it is really cramping my style.[/QUOTE]
This may help, but it looks like you have an underlying problem:

[http://fasterfox.mozdev.org/](http://fasterfox.mozdev.org/)

---

### Post by bb002 on 2005-12-05
I installed Firefox 1.5 following the wiki but that didn't help. I then unistalled 1.5 following the uninstall also located in the wiki.

I fixed my issue by compiling firefox from source. Dunno what installing from source did that's so special compaired to the pre-compiled version but it worked.

---

