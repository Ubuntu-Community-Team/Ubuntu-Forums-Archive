---
title: "Hardy Issues (speed problems, login/out process issues) - Any thoughts on this?"
date: 2008-04-25
forum: Desktop Environments
---

### Post by AlchemyMan on 2008-04-25
Well, I was rather happy with my Gutsy. Ran fast, with modest desktop effects, pretty stable and reliable over all. On the other hand, this Hardy installation has, perhaps, been the most frustrating of all. I am not one to curse the winds of change, but we all know that change can be darn painful sometimes.

Anyways, on to my account and request:

There was no networking when I installed Hardy, but now I've got that running pretty well. The Effects also disappeared initially, but once I finally got my ATI driver working they came back. I made the mistake of installing xgl for a while, thinking that that might have been the missing link, but instead it slowed my system to a dying crawl. I removed it, the desktop effects still work, and things seem a good deal more normal now.

However, there is still a noticeable performance decrease from my Gutsy installation. On Gutsy, everything ran smooth and fast. Now, Hardy at the moment runs pretty well, in that it's usable ... but it's definitely markedly slower. Applications and even Nautilus folders take several seconds longer to launch. A rather irritating several seconds. This is with and without effects (the effects themselves are a bit more choppy, but I am assuming it's all coming from the same place).

Another really strange problem is that the log out option doesn't seem to work. There are a few lines of text, then the screen goes black and stays there. And stays there. Happened three times already. 

On loggin in, my one main complaint is that it doesn't seem to remember my volume settings until the GUI is already running, so the Ubuntu music always plays full blast and I have to scramble to turn it off...it seems a small issue, but I live in a small place and have roomies. I am an insomniac, but they don't always keep to my crazy sleeping schedule, and I don't want to wake them.

Is there anyone out there who has any ideas as to how to fix one or more of these issues, or what could be causing them? I thank you in advance!

---

### Post by gtg on 2008-04-25
No answers here - just like to echo your (lack of) speed observation.  Gutsy was crisp, clean, and fast. In fact, my 10-year old preferred it to WinXP on the same machine.  Today, I clean-installed Hardy on this machine and, within 10 minutes of use, that same 10-year old was thinking about rebooting to WinXP.

I tried setting the Visual Effects to "None."  That seemed to yield some speed improvements, but it's still slower than Gutsy.  :(

---

### Post by Islington on 2008-04-25
The spped issues may be because of the massive strain on the apt servers, that shoudl die down in a couple of weeks.

---

### Post by jimv on 2008-04-26
gtg, just curious, what exactly feels slow?  The effects?  Opening/closing folders?  Opening programs?

---

### Post by Cogito² on 2008-04-26
> **jimv said:**
> gtg, just curious, what exactly feels slow?  The effects?  Opening/closing folders?  Opening programs?
For me many things are pretty slow, but especially the default Firefox 3. Actually if I close it, ubuntu will ask me if I want to force quit it each time, since it takes so long to close...and that's even if it's on about:blank.

---

### Post by Cogito² on 2008-04-26
> **Islington said:**
> The spped issues may be because of the massive strain on the apt servers, that shoudl die down in a couple of weeks.

This seems like it could very well be it for me, but it seems like an odd reason. I'm not a programmer and no linux expert, but I don't see why checking the apt servers should require so many computer resources...seems like inefficient programming to me.

---

### Post by Islington on 2008-04-26
Also guys try installing preload. I absoultely is a must for speeding up my system. to install it ```
 sudo apt-get install preload 
``` to read more about it and the numbers and such go to [http://www.techthrob.com/tech/preload.php](http://www.techthrob.com/tech/preload.php)

---

### Post by gtg on 2008-04-26
jimv asked what seems slow.  The default bootup process was much longer (2x-3x) in Hardy versus Gutsy.  Some of this seemed to be alleviated by cutting back on the Visual Effects.  Opening Firefox 3.0 Beta 5 on Hardy takes much longer than opening Firefox 2.0 on Gutsy.  I'm following Islington's preload advice in the hope that it will help this problem.  My 10-year old's complaint was associated with the responsiveness of Firefox 3.0 Beta 5.  I'm hoping the Visual Effects change helps with this.  

In the end, this may be largely associated with the heaviness of the new Firefox.  I've had to endure what Cogito² has noticed - many forced quits with Firefox 3.  A forced quits seem to be less likely if only one tab is opened at the time of the quit.

Thanks to all who are responding with concerns and helpful hints.

---

### Post by jimv on 2008-04-26
The firefox thing is odd.  Mine just pops up and asks me if I want to save my tabs, and then closes.  Takes about half a second.  And this isn't a fast laptop.

Maybe try turning off any extensions or backgrading to 2.0

---

### Post by robbiev80 on 2008-04-26
I experienced many problems when I upgraded from 7.10...
The environment was super slow, I couldn't access my home directory from the GUI, and my resolution was horrible.

So I just did a clean install (and redid all my partitions)
and it was by far the best thing I could have done. The install
was as easy as it gets and ubuntu recognized my ATI video card
from the start! 

I'm very happy with Hardy so far!

---

### Post by AlchemyMan on 2008-04-27
Well, at least I am not alone in this... hopefully things will improve soon. I will definately try the preload thing, Islington, and see if it makes any difference. 

I've unfortunately had the system partially freeze (I suspect due to firefox but am not 100% sure) three times since the installation, and had to test out the EISUB trick. I've been running Linux for about a year now, and in that whole year I think my system had crashed only once, so this is a bit ...unsettling, I guess. All in all, it runs alright and is pretty usable. The issues are, of course, annoying, mainly because of the comparison I inevitable draw between the way Hardy currently runs, and the way Gutsy used to, but I am hoping they will be addressed over time.

The login sound issue seems to come and go, strangely enough. I haven't had the need to log out yet, so not sure what's up with that at all.

---

### Post by Super Jamie on 2008-04-27
I'm having the same deal with Hardy and slowness.

Opening programs takes a long time, alot of things in Firefox (opening, closing, clearing download lists, loading pages, loading a few tabs at once, scrolling) seem to hang the system while it has a think about it. Every now and then, the system is unresponsive and there's alot of hard drive activity, System Monitor running in the Panel just shows the CPU in 100% IOwait during this.

This is a new install of Hardy on a SATA hard drive, 3Ghz, 2Gb RAM, Geforce, etc. Preload is always one of the first packages I install, as well as turning off stuff I don't need like bluetooth, printing, Tracker, compiz, etc.

Gutsy worked great on the same hardware, Hardy is slow as.


edit: Reading further around the forums, and as I suspected, there have been similar little troubles with previous releases before. But hey, at least if people report them, then they get known about and fixed. Any ideas on how we could get logging or errors or anything helpful out of "it's slow" would be muchly appreciated. It also seems a few users have had luck upgrading to the new 2.6.25 kernel, hopefully this will appear in repos soon.

---

