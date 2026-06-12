---
title: "Firefox Eating the CPU"
date: 2004-12-14
forum: Desktop Environments
---

### Post by Sepero on 2004-12-14
I've been using Debian on my personal desktop for a couple years now, so I'm not exactly new to Gnu/Linux. I'm trying to help my father escape MS, so I thought I'd get him a 'newbier' distro to start dual-booting with. I installed Unbuntu on his pc, and have fixed several little 'gotchas'. I've corrected modules, installed the printer, his internet connection, screen resolution, and setup a few better defaults.

Anyways, there's still a few problems to work out, and Firefox is at the top of my list. Whenever Firefox is loading a webpage, processor cycles increase about 40-50%! Now this is: "Loading the page AND looking at the page". Interestingly though, when a new blank tab is opened, an switched to, the processor goes down 40-50% again. When the page finishes loading, I can switch to it, and there's no huge increase in cpu.

But, there's more.  #-o

As I type this from his pc, right now using Firefox, the cpu is at a staggering ~75%! There is nothing else running in the background, there are no pages loading, but there are 4 tabs open in Firefox. When I close Firefox, the cpu always returns to the normal ~5% usage.


I can hear this now: "But what about flash (or some other plugin) ?"
I haven't even gotten around to installing those yet.

Now I hear: "His computer must be too old or slow."
Maybe, but my dad is dual-booting with MS XP. There he uses Firefox too. He regularly opens 30+ tabs there. Also, he has Flash, Java, etc. installed.


If anyone can explain how to fix this, it would be greatly appreciated.
The computer is a IBM Aptiva E Series 190.
AMD k6-2 500mhz
96Mb SDRam

---

### Post by jdong on 2004-12-14
You'd **definitely** want more RAM on that system! At least 128, 256 is always handy! 96 is almost unacceptable. Remember-- With Linux, RAM is much more important than CPU power.


What kind of video card are we talking about?

FF 1.0 Final fixes lots of various memory/resource leak problems. Perhaps try a Firefox 1.0 backport? (see [http://ubuntu-bp.sourceforge.net](http://ubuntu-bp.sourceforge.net))

---

### Post by jdong on 2004-12-14
Forgot to ask:

Does the computer's performance actually suffer as FF wallows in CPU resources? Lots of times, I've seen Firefox consume a concerning amount of resources, but actual performance never suffers from it!

---

### Post by Sepero on 2004-12-17
[QUOTE=jdong]Forgot to ask:

Does the computer's performance actually suffer as FF wallows in CPU resources? Lots of times, I've seen Firefox consume a concerning amount of resources, but actual performance never suffers from it![/QUOTE]
Two things:
1) Sorry I put 96Mb Ram. That was the factory setting and upon upgrade, I knew he would need more. I forgot to mention that. He actually has 192Mb, but everything else is still factory.

2) Yes, the actual pc perfomance does suffer. (badly ](*,))

EDIT:
Oh, I don't know what video card he has. I'm sure it's very generic or built into the motherboard. I'm conviced it has nothing to do with graphics though, because the problem persists when firefox is minimized. (remember, no flash or java)

---

### Post by jdong on 2004-12-17
Try my backported version of Firefox 1.0, linked above, and see if that helps at all.

---

### Post by Sepero on 2004-12-30
I installed the backport(nice job, btw). Unfortunately, it also chomps out high CPU cycles. I read this today, though, and I think this may explain it:
[http://justlinux.com/forum/showthread.php?s=&postid=788611#post788611](http://justlinux.com/forum/showthread.php?s=&postid=788611#post788611)

> *Posted by: madcompnerd *
[b]I recommend Galeon or Epiphany over firefox for a slow machine. Firefox appears to be more efficient at rendering, but it really just starts it's renders earlier leaving it with many page renders as the page finished downloading. The result is blazing fast web browsing on a blazing fast computer; but constant cpu usage on a slow computer. Mozilla generally waits, making it appear slow. But on my 700 Celeron laptop, I can notice the difference in CPU time the two take; and Mozilla takes much less.
Galeon and Epiphany will be more efficient in their interfaces than both.[/b]
I use Mozilla on my Debian box(700Mhz) instead of Firefox anyway, so I'll try installing that on his(500Mhz) and see how it works out.

---

### Post by Sepero on 2005-01-02
Before I originally posted this thread, I did multiple searches on this forum to see if anyone else has had this problem yet. I don't know if any have been posted since, but I believe that this was the first thread to address this problem.

I just want to say, Problem solved. Using regular Mozilla did the trick! No more wasted CPU cycles. Thanks for your help, jdong.

---

### Post by cutterjohn on 2005-01-05
on an ibook2 G3/500(currently @400) Firefox 0.93 (default install) is using 0% CPU when idle, and peaked briefly at 52% when loading various pages, including a reload of this thread page.  Generally it seems to use between 12-25% CPU when rendering a page with a few brief spikes, as mentioned above, to ~50%.

Seems ok(but I haven't noticed/checked) on OSX & Windows 2000. (Also this is all done over dialup which may have an affect as rendering speed/CPU usage as data access will be constricted by meagre bandwidth.)

Also, you may wish to investigate xfce.  It's a pretty nice little, lite desktop environment that is still a) useful, and b) looks decent.  Just don't use the file manager(xffm) use ROX or something else instead.  (xffm is taking simplicity a little too far, plus ROX or something else would get you icons on the desktop again if you wanted them.)

---

### Post by Sepero on 2005-01-05
The reason he's not having the problem on XP might be because he is using an older version. I installed it right around the time they changed the name from Firebird...

---

