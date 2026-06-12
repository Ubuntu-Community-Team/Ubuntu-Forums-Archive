---
title: "Firefox crashing computer"
date: 2005-12-09
forum: Desktop Environments
---

### Post by 12quality on 2005-12-09
I am having a problem where certain websites not only crash firefox, but my entire computer.  The screen just freezes.  I can still move the mouse, and if music was playing it will continue to do so, but nothing else has any response.  Ctrl-Alt-Backspace doesn't even work.

I recently upgraded to Firefox 1.5 as the popular wiki instructed, so that could be the source, but in the last few weeks I have also updated the kernel.  I also had to install new plugins and extensions when I upgraded to 1.5.  These include: Adblock, All-in-one Gestures, ProxyButton.  I also had flashgot, but removed it, thinking that was the problem.  I have flash, java, and mozplugger plugins.  I had the mozilla-mplayer package installed, but removed it thinking that was the problem.

The weird thing is that in trouble-shooting, I decided to used epiphany.  And, epiphany crashed the same way.

Here are two sites that have crashed the browser:

[http://www.chattablogs.com/quintus/archives/019666.html]("http://www.chattablogs.com/quintus/archives/019666.html")
[http://news.com.com/Unpatched+Firefox+1.5+exploit+made+public/2100-1002_3-5987401.html?tag=nefd.top]("http://news.com.com/Unpatched+Firefox+1.5+exploit+made+public/2100-1002_3-5987401.html?tag=nefd.top")

If I try to visit either of these pages, it will load a part of all of the page, but then just freeze.

I have tried disabling java and javascript to no avail.

Please help.

---

### Post by towsonu2003 on 2005-12-10
Visiting those pages while writing this: both loaded... No freeze... 

what if try it once with flashblock and noscript extensions... and remove adblock and replace with adblock plus as they say it causes memory leak (didn't work in my case but whatever). 

sorry, not so helpful...

---

### Post by magnusbb on 2005-12-10
No freeze here. But especially the first page demands a LOT of CPU.

---

### Post by cutOff on 2005-12-10
You could try to remove flash plugin and see if it causes the trouble.

---

### Post by yaztromo on 2005-12-13
Exactly the same problem here. Everything crashes. Only thing I can do is move the mouse. Ctrl-Alt-Backspace does nothing.

I have also upgraded to 1.5, it didn't do this before that.

EDIT:

It's not too hard to reproduce. Go to any site with a lot of content. A slashdot comments page will do. And scroll up and down by dragging the scroll bar. Eventually it will crash.

SECOND EDIT:

Falling back to 1.0.7 fixes this.

---

### Post by barbarian on 2005-12-14
no probs here, maybe 'cause I have flashblock extension..:confused:

---

### Post by yaztromo on 2005-12-14
Well it doesn't happen on flash sites. It can happen on any site. It is most frequent on sites with a lot of text when you are scrolling up and down.

Like the OP said. Everything freezes but the mouse pointer. It as if Firefox crashes taking X with it.

---

### Post by yaztromo on 2005-12-15
I have disabled renderaccel in xorg.conf and so far firefox hasn't crashed since.

---

### Post by 12quality on 2005-12-17
[QUOTE=yaztromo]I have disabled renderaccel in xorg.conf and so far firefox hasn't crashed since.[/QUOTE]
I did this and it seemed to fix the problem.  I had changed some settings in Xorg.conf before and it must have caused this crashing, which would also explain the crashing occuring in Epiphany.

Thanks.

---

### Post by PMO6022 on 2005-12-17
I have seen this problem for quite some time, and I too believe it to be a problem with renderaccel in xorg.  I remember having this problem during the hoary development cycle (see [http://www.ubuntuforums.org/showthread.php?t=23584]("http://www.ubuntuforums.org/showthread.php?t=23584")), and the solution was to disable renderaccel then. 

I am using an Nvidia GeForce 2 card, with the nvidia drivers from breezy, and I recently reenabled renderaccel to play around with the new composting manager in enlightenment-0.16.8. My computer locked up completly when starting firefox.  I disabled renderaccel, and tried the compositing options again, and no crashes - but since all of the work was being done by the computer instead of using the video card, it ran very slowly.  I hope this is something that will be fixed at some point.

EDIT: I just installed the latest nvidia driver from their site - v8174, according to the directions here: [http://www.ubuntuforums.org/showthread.php?t=75074&highlight=nvidia+driver](http://www.ubuntuforums.org/showthread.php?t=75074&highlight=nvidia+driver) and things seem to be working fine with renderaccel turned on.  I'll repost if I see any lockups.

---

### Post by aysiu on 2005-12-17
If it happens in Epiphany too *and* freezes up your whole computer (not just the open program), it's probably not a Firefox problem. I don't know what it is, though.

---

### Post by manis on 2005-12-17
I have no problem with the website in your suggestion. I using ubuntu breezy with firefox-mozilla browser. 
Unfortunely, I don't have idea when you can't load this page with your browser.
tk

---

