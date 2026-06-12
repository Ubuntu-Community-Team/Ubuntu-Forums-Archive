---
title: "Firefox Perpetually Slow"
date: 2009-01-20
forum: General Help
---

### Post by Valok on 2009-01-20
For a couple weeks now I've been forced into using Opera browser (which I'm not a big fan of but it works at a normal pace) because firefox has come to a snails pace for me.  I've tried un-installing and reinstalling firefox via Synaptic but it doesn't seem to make it any better.

I'm not sure what to do or where to look next.  Is there some file hidden in the depths of my computer that doesn't get deleted when I click "select for complete removal" in synaptic?  I'm just not sure what the problem could be, I'd love any advice.

---

### Post by DeMus on 2009-01-20
> **Valok said:**
> For a couple weeks now I've been forced into using Opera browser (which I'm not a big fan of but it works at a normal pace) because firefox has come to a snails pace for me.  I've tried un-installing and reinstalling firefox via Synaptic but it doesn't seem to make it any better.

I'm not sure what to do or where to look next.  Is there some file hidden in the depths of my computer that doesn't get deleted when I click "select for complete removal" in synaptic?  I'm just not sure what the problem could be, I'd love any advice.

For a complete removal of Firefox you also have to delete the hidden folder .mozilla in your user area.
Open Nautilus, in the menu view select show hidden files en delete .Mozilla.
You will also delete your bookmarks so if you want to keep those, save them first somewhere else.

---

### Post by oldsoundguy on 2009-01-20
or you can go get the latest version of the program here:

[http://sourceforge.net/projects/ubuntuzilla/](http://sourceforge.net/projects/ubuntuzilla/)

and forget the repository install/removal.  This version will let you know when there is an update and HOW to go about updating.  Been using this since 7.10 and hasn't missed a beat.

ALSO .. make sure you do not have a gang of plug ins and add-ons running in the background.  If you do not use that hot plug in you put there 4 months ago to "try out", disable and un install it!

---

### Post by Yashiro on 2009-01-20
Quite alot of these posts in the past few days.

I wonder what the common factor is.

---

### Post by Valok on 2009-01-20
*Edit*

After playing with firefox and going to a few additional pages it slowed right back up.  No idea what the hell is going on, but after deleting EVERY firefox file on my computer and re installing I still can't get it to work.

If it helps, when I installed firefox it didn't seem to have the default skin enabled, looked more like the one gnome goes to when something gets messed up.  Very chunky, blocky and ugly grey looking.

---

### Post by scouser73 on 2009-01-20
You should try tweaking Firefox as show in this tutorial; [http://www.ubuntugeek.com/speed-up-firefox-web-browser.html]("http://www.ubuntugeek.com/speed-up-firefox-web-browser.html")

---

### Post by misswham on 2009-01-20
Been happening to me also.

---

### Post by Feivel on 2009-01-20
> **Yashiro said:**
> Quite alot of these posts in the past few days.

I wonder what the common factor is.

Geez...Firefox is....Haven't you been reading :)

---

### Post by DeMus on 2009-01-20
When you write Firefox is slow, what do I have to think of: opening in 10 seconds or more, showing pages bit by bit. How long does it take to show the forum page, 1 second, 10 seconds, half a minute? In other words: What is slow?

---

### Post by Valok on 2009-01-21
By slow I mean that to load up any page it takes about 10-15 seconds, sometimes more.  As opposed to other browsers I'm using which do it just about instantly.

---

### Post by ellalan on 2009-01-21
I increased the speed by removing one of my add ons, smooth scroll was my culprit. Since I removed that FF works fine.

---

### Post by Valok on 2009-01-21
I'm currently running FF with no addons or extensions enabled, but still with the impressively slow speeds.

---

### Post by oldsoundguy on 2009-01-21
have you bothered to check your internet speed  A visit to one of several speed test sites might help .... 
and again, complaints about something from the repositories ...

For ANYTHING Mozilla, to get the latest:

[http://sourceforge.net/projects/ubuntuzilla/](http://sourceforge.net/projects/ubuntuzilla/)

and it will NOTIFY you when updates are available AND it will tell you how to install it .. really EASY .. almost as easy as installing a virus program in Windows!

---

### Post by Valok on 2009-01-21
Yeah I know its not an internet problem because everything else runs fine.  Opera, video games, pidgin all work at acceptable speeds.  And other computers of my same router also aren't having any problems.

I tried installing Firefox via Ubuntuzilla and still had the same problem.  I think at this point I'm just giving up on firefox and waiting for chrome to come out.  

Anyone know when that will be?

---

### Post by ellalan on 2009-01-22
You are right valok, FF3.0.5 is painfully slow when it starts and browsing seems to be slowed down as well. The recent updates may be the problem and hope they will rectify it soon.

---

### Post by DM was on fire! on 2009-01-22
I gave up on Firefox back when it was still in 2.5.
It crashes on me and runs super slow. :(

I would suggest either Konqueror or Epiphany with epiphany-extensions. The latter package has Greasemonkey, bookmark tray, et cetera.
I thought it had Adblock, but I guess not? o.o
That's why Konqueror's a good idea, because it has adblock already installed.

---

### Post by Yashiro on 2009-01-22
Any chance of posting what version of Ubuntu/Linux you guys are having Firefox slowdowns with?
Saying "it's slow" without giving any information will never result in a fix.

---

### Post by Valok on 2009-01-22
I'm using Ubuntu 8.04 with firefox 3.0.5

Thanks for the other browser recommendations, I'll check em out!

Quick question, is Konquerer only for KDE?  From what I can tell it looks like it is, but I could be wrong.  Either way Epiphany looks pretty cool and I'll give it a spin.

---

### Post by DeMus on 2009-01-22
> **Valok said:**
> By slow I mean that to load up any page it takes about 10-15 seconds, sometimes more.  As opposed to other browsers I'm using which do it just about instantly.

Would this help you:
[Improve Firefox](http://www.ubuntugeek.com/speed-up-firefox-web-browser.html)
Another idea, which is also mentioned on that webpage is to download the add-inn Fasterfox.
Success.

---

### Post by philinux on 2009-01-22
> **Valok said:**
> I'm using Ubuntu 8.04 with firefox 3.0.5

Thanks for the other browser recommendations, I'll check em out!

Quick question, is Konquerer only for KDE?  From what I can tell it looks like it is, but I could be wrong.  Either way Epiphany looks pretty cool and I'll give it a spin.

Just to pinpoint the problem try running in safe mode. From a terminal.

firefox -safe-mode

---

### Post by Valok on 2009-01-22
> **philinux said:**
> Just to pinpoint the problem try running in safe mode. From a terminal.

firefox -safe-mode

Thanks, I'll give that a shot.

---

