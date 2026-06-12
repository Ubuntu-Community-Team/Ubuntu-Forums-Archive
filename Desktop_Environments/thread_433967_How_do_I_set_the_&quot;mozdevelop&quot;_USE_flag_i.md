---
title: "How do I set the &quot;mozdevelop&quot; USE flag in/for Firefox - to solve Firebug bug"
date: 2007-05-05
forum: Desktop Environments
---

### Post by motin on 2007-05-05
I cannot use the Firebug extensions in Firefox in Feisty. Error message:

Error: Firebug has no properties
Source File: chrome://browser/content/browser.xul
Line: 1

The same problem *with solution* is available here: 
[http://panela.blog-city.com/firefox_plugin_weirdness_with_firebug.htm](http://panela.blog-city.com/firefox_plugin_weirdness_with_firebug.htm)
[http://forums.gentoo.org/viewtopic-t-530799.html](http://forums.gentoo.org/viewtopic-t-530799.html)
[http://groups.google.com/group/firebug/browse_thread/thread/f5092eeca5dac719/a7d3e9a82edef7fd](http://groups.google.com/group/firebug/browse_thread/thread/f5092eeca5dac719/a7d3e9a82edef7fd)

But I can't figure out how to set the "mozdevelop" USE flag in Ubuntu...! Please help - Firebug saves so much time...

---

### Post by motin on 2007-06-11
So nobody knows this?

If I have been unclear please tell me and I will rephrase. Thanks

---

### Post by bunker on 2007-06-11
Are you referring to gentoo's USE flags?  Ubuntu doesn't have such a concept.  You'd need to compile firefox from source manually if you want the same effects as you get with portage.

---

### Post by motin on 2007-06-24
> **bunker said:**
> Are you referring to gentoo's USE flags?  Ubuntu doesn't have such a concept.  You'd need to compile firefox from source manually if you want the same effects as you get with portage.

This makes it even stranger. Everyone I talked to, everywhere I've searched, I have only found Gentoo users having the same problem, and they all have solved it by emerging with the mozdevelop flag set... 

So what does the mozdevelop flag do? Maybe I could solve this if I knew. I'd rather not rebuild from source since Firefox is so integrated into Ubuntu and I've read that there are many configure-settings needed to be set correctly to have it work in a good manner.

---

### Post by bunker on 2007-06-26
Short form: "emerging with USE flag X" is exactly the same as compiling from source with some compile option X set in the ./configure step.  Since Ubuntu packages are binary, you don't get to choose any compile options so if you want to enable mozdevelop, you have no other option but to compile from source.  You can see what compile arguments have been used by typing about:buildconfig in the address bar.  Personally I find compiling a piece of software as big as firefox to be way more hassle than it's worth on a binary distro; you might want to try to get it re-packaged with a friendly bug report :).

---

### Post by motin on 2007-07-16
Thanks for clearifying this matter! Wow with the about:buildconfig I can probably pretty easily recompile firefox!

I can get the correct source tree (correct version and with Ubuntu specific patches) by issuing apt-get source firefox, but now where do I specify the configure options with debuild?

I'd use ```
debuild -i -us -uc -b
```. Should I simply run ./configure with the about:buildconfig + -mozdevelop options before running debuild?

---

### Post by jjrockman on 2007-07-30
I'm not sure if you've fixed your problem yet, but I was having the same issue and was able to fix it by disabling the ColorZilla extension...

---

### Post by motin on 2007-08-02
> **jjrockman said:**
> I'm not sure if you've fixed your problem yet, but I was having the same issue and was able to fix it by disabling the ColorZilla extension...

BAAAH BAAAH BAAAH BAAAH BAAAH. Gurgel whim wham whidaladoodelidoo! That was it!

:lolflag::guitar::lolflag::guitar::lolflag: :guitar: :lolflag::popcorn:

[SIZE="6"]Big thanks![/SIZE]

PS I had disabled ColorZilla before, but not restarted Firefox in between - slipped my attention... !

---

### Post by aamche on 2007-08-07
Wow that really works.

I have messaged both the Colorzilla and Firebug guys about a possible conflict between the two, lets hope they find a solution. Both extensions work together on windows and I can't live without them.

---

