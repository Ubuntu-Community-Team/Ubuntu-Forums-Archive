---
title: "[New Game] Age of Fear"
date: 2011-04-10
forum: Gaming &amp; Leisure
---

### Post by leech13 on 2011-04-10
Hello,


Today we released a new indie turn-based strategy game.
There is also version for Ubuntu (deb package):


Age of Fear: The Undead King is a fantasy turn-based strategy primarily focused on single player mode. The game features a novel battle system and two campaigns with solid fantasy stories.
The story takes place in an untamed fantasy land, where three forces: the Human Kingdom, the Greenskins' Horde and the Undead Legion - are fighting for domination and survival.

You will encounter quick skirmishes, where wise unit's cooperation is essential. You will visit distant lands either as a honorable knight or an evil necromancer. You will conquer cities and destroy ancient evil!
Age of Fear: The Undead King is available for Windows, Mac OS X and Linux systems!


Home page:
[http://www.age-of-fear.net](http://www.age-of-fear.net)

Trailer:
[http://www.youtube.com/user/AgeOfFearTUK](http://www.youtube.com/user/AgeOfFearTUK)


There is also promotion during first two weeks:
* 50% off price in first week (until 17th April)
* 25% off price in second week (until 24th April)

Enjoy!
Les

---

### Post by Elfy on 2011-04-10
> The Undead King is available for Windows, Mac OS X and Linux systems!Where's the non-deb version?

---

### Post by leech13 on 2011-04-10
Hi,

we releasing only deb package for now, but you can use alien tool for conversion or extract content directly.

Check this thread:
[http://www.age-of-fear.net/index.php/component/kunena/9-technical-issues/82-installation-on-linux?Itemid=0](http://www.age-of-fear.net/index.php/component/kunena/9-technical-issues/82-installation-on-linux?Itemid=0)


Les

---

### Post by Perfect Storm on 2011-04-10
Sticked for a limited time.

---

### Post by Elfy on 2011-04-10
> **leech13 said:**
> Hi,

we releasing only deb package for now, but you can use alien tool for conversion or extract content directly.

Check this thread:
[http://www.age-of-fear.net/index.php/component/kunena/9-technical-issues/82-installation-on-linux?Itemid=0](http://www.age-of-fear.net/index.php/component/kunena/9-technical-issues/82-installation-on-linux?Itemid=0)


Les

Thanks - looked at the page 

I assume that there's a typo ... 

extract data files from package:
_ar_ vx age-of-fear.deb

---

### Post by leech13 on 2011-04-10
> Sticked for a limited time.
Thanks!


> I assume that there's a typo ... 
ar is **ar**chive tool. It's pretty useful for extracting content from deb packages :-)
[http://nixdoc.net/man-pages/Linux/ar.1.html](http://nixdoc.net/man-pages/Linux/ar.1.html)

---

### Post by Elfy on 2011-04-10
> **leech13 said:**
> > Sticked for a limited time.
Thanks!


> I assume that there's a typo ... 
ar is **ar**chive tool. It's pretty useful for extracting content from deb packages :-)
[http://nixdoc.net/man-pages/Linux/ar.1.html](http://nixdoc.net/man-pages/Linux/ar.1.html)

Didn't know that - fair enough, though I would guess I'd not be the only one to wonder when you've got this ;)

> extract data files from package:
ar vx age-of-fear.deb

extract the contents of data.tar.gz using tar:
tar -xzvf data.tar.gz

---

### Post by ELD on 2011-04-12
Can someone pop some screenshots up for me so i can check while at work?

---

### Post by NewWorld on 2011-04-14
> **ELD said:**
> Can someone pop some screenshots up for me so i can check while at work?

[http://www.age-of-fear.net/images/screenshot-1.png](http://www.age-of-fear.net/images/screenshot-1.png)
[http://www.age-of-fear.net/images/screenshot-2.png](http://www.age-of-fear.net/images/screenshot-2.png)
[http://www.age-of-fear.net/images/screenshot-3.png](http://www.age-of-fear.net/images/screenshot-3.png)
[http://www.age-of-fear.net/images/screenshot-4.png](http://www.age-of-fear.net/images/screenshot-4.png)
[http://www.age-of-fear.net/images/screenshot-8.png](http://www.age-of-fear.net/images/screenshot-8.png)

---

### Post by Perfect Storm on 2011-05-08
un-sticked.

---

### Post by Perfect Storm on 2011-06-25
Re-sticked.

---

### Post by HolgerB on 2011-06-29
Err...the demo deb is i386 only ?
Any chances for a amd64 demo ?

Edit: 
Got a reply from one of the devs I guess:
> 
this package should work on any platform.
It was previously marked as all-architectures, but new Ubuntu rules marked it as warning, so we switched to i386.

You might install it by:
>sudo dpkg -i *--force-all age-of-fear-demo.deb*
So if you are trying out the demo under x64 Ubuntu (or derivates) and get a "wrong architecture" warning, then try the above command.

Edit2: Yes, works perfectly...although this not my game type. I just wanted to try out...just too complicated stuff to me :)
I rather go for crash-boom-bang :D

---

### Post by HolgerB on 2011-07-11
> **Domnick.wlisey said:**
> Will you provide us demo version
What does this question mean ?
Will you provide a demo version for us ? If yes, then checkout their web page. They provide a demo of Age of Fear in Deb format.

Edit: In case following links and searching pages is too hard:
[http://www.age-of-fear.net/downloads/age-of-fear-demo.deb](http://www.age-of-fear.net/downloads/age-of-fear-demo.deb)

---

