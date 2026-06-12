---
title: "Dell mini 12 with Hardy seems very slow"
date: 2009-03-23
forum: Dell Ubuntu Support (CLOSED)
---

### Post by kevinchannon on 2009-03-23
I have just received my Mini 12.  I ordered it with Ubuntu pre-installed, since I have been running Ubuntu on my other computers for some time now and I find it to be excellent.  However, the version of Hardy that comes with the Mini 12 seems to be very slow. I know that the "netbook spec." of this model means that it is going to be a little slower that I'm used to, but even so, it seems slower than I'd expect.  For instance, we also have an Asus EeePC on which we binned the original operating system and installed Ubuntu (originally Hardy, but upgraded to Intrepid) and that runs significantly faster than my Mini 12. If I check the system monitor "performance" tab, then one of the cores is always running at ~50% and the other at ~15%, even if there are no other programs open.  Although, If I run top then all the processes show 0 in the CPU field.

In addition to the slowness, I have had two complete lock-ups since I got my Mini 12 (three days ago).  These seemed to be related to the networking in some sense, but I couldn't reproduce them. In any case, all I could do was hold the power button down until it reset.  As I said, I have been using Ubuntu since Hoary Hedgehog and I don't recall this ever happening in the past, on any of the may computers that I've installed and run it on (except in those instances when I have changed something which foobar'd something important, but in this case I haven't touched a thing).

So, basically, what the Dell's up?  Why is this version of Ubuntu so slow and unstable on the Mini 12?  And, what can I do to fix it?  I really like the form of the Mini 12, and everything (except the bluetooth) works most of the time, it's just very slow.  I hope that someone knows how I can either install a standard Ubuntu (unlikely, since I have read that there are multiple driver issues with the video and such) or speed this one up some.

Thanks.

---

### Post by armandh on 2009-03-23
The first thing I did with my mini9 was restore the factory OS.

knowing I could do that, I felt free to try anything else.

---

### Post by sirebral on 2009-03-23
> **kevinchannon said:**
>  If I check the system monitor "performance" tab, then one of the cores is always running at ~50% and the other at ~15%, even if there are no other programs open.  Although, If I run top then all the processes show 0 in the CPU field.


This part sounds like a BIOS problem.

---

### Post by mocoloco on 2009-03-24
Wow, same here.  My wife's new mini 12 has done some odd things, like suddenly restart X11 for no reason, and it just "feels" a bit too slow to me, even moreso than what I would expect from a netbook.
I haven't been able to do any real troubleshooting yet, only seems to go wacky when I'm not around to look at it.
The speaker is extremely weak, to the point I think there's at least a software config issue, if not a hardware issue.
I'm going to see what I can figure out over the next few days.

---

### Post by kevinchannon on 2009-03-24
Yep, I have experienced both random X restarts (about 3 of them, I think) and the speakers are almost inaudible.

---

### Post by snowpine on 2009-03-24
I have the Mini 9, not the 12, so take my advice with a grain of salt....
Have you run the update manager yet to bring your system up to date? Installed the latest bios? I would start by updating your system to see if this solves the problem.  

If not, there are a lot of people switching to "regular" Ubuntu or Xubuntu (or even Crunchbang) instead of the Dell version. Can't speak for the Mini 12, but on the 9, the only issue is the sound card, which is easy to fix. Sites like [http://www.ubuntumini.com/](http://www.ubuntumini.com/) have all the tips and tricks needed. I hear Jaunty in particular is quite fast; I personally am sticking with Dell 8.04 for the time being; it is adequate for my modest needs. :)

---

### Post by jackwcole on 2009-03-24
The Mini 12 does run slow as setup by Dell, I'm not sure of the solution. Changing to a different version of Ubuntu has a lot of drawbacks and problems so I am sticking with the original version and hoping for improvements with upcoming releases.
Jack

---

### Post by flysteve on 2009-07-03
I just installed Ubuntu 9.04 Netbook Remix on a Dell mini 12 that came with XP and had the same problem, it was extremely slow.  I switched to the classic desktop using the decktop switching tool on the system menu and everything is running much better.  The install was very straight forward, installed from a .img file loaded to a ram stick.  Good luck

R/

---

### Post by kevinchannon on 2009-07-04
> **flysteve said:**
> I just installed Ubuntu 9.04 Netbook Remix on a Dell mini 12 that came with XP and had the same problem, it was extremely slow.  I switched to the classic desktop using the decktop switching tool on the system menu and everything is running much better.  The install was very straight forward, installed from a .img file loaded to a ram stick.  Good luck

R/

I have had a play with a live USB version of 9.04, and everything works fine, the only thing is that the required display driver doesn't seem to exist in Linux so the screen resolution is not found correctly, the screen is slow to re-draw and things like hardware accelerated graphics obviously don't work.  Have you observed this?  The whole thing is definitely generally faster though, don't you think?
   On balance, I've found it better to stick with the Dell-supplied version.  X has stopped crashing now too and I haven't hard to do a hard re-start for quite a while.  I just don't know why Dell had to go and make there own version of Ubuntu - it would have been much more satisfactory from a community point of view to just use the regular Ubuntu and write the driver for the GMA 500 graphics and contribute it to the Linux kernel (or wherever it's supposed to go!).  I've also seen that there are several other products that use GMA 500, beware.

---

### Post by almess301 on 2009-07-04
I have a dell inspiron mini 10 with the GMA 500, I managed to locate a usable 9.04 driver, but wish for a little better performance.  Anyone know if Ubuntu 9.10 will support the GMA 500?  and also where can I find the dell ubuntu image that came with my laptop?

---

### Post by mikewhatever on 2009-07-04
I don't know if Karmic will have better performance with GMA500. Hopefully, it will be an out of the box experience. There is [Dell reinstall iso here.]("http://linux.us.dell.com/files/ubuntu/hardy/iso-images/ubuntu-8.04.1-dell-reinstall.iso")

I wonder, why did you replace the pre-installed 8.04 with 9.04? Wasn't the out of the box experience decent?

---

### Post by kevinchannon on 2009-07-04
> **mikewhatever said:**
> I wonder, why did you replace the pre-installed 8.04 with 9.04? Wasn't the out of the box experience decent?

I have not found it to be.  As I said at the very start of this thread, I've been running Ubuntu on various hardware for quite a  while now, and I've never had it behave like this Dell-ized version does.  My fiancee runs 9.04 on an EeePC and it runs at what I'd consider a normal speed (you can't really notice the difference between that and my older HP full-sized laptop, in normal use).  Even though my Dell mini 12 has a dual core Atom processor (the EeePC only has a single core) it is noticeably slower.  The Dell Ubuntu used an lpia version of the linux kernel, I guess to get a bit more battery life.  I'm not sure it's worth it though, as I say it can be frustratingly slow.  It'd probably be OK if I knew how to get the lpia bit of the kernel (I suspect that there's some re-compiling steps, and then I'm not sure if the resulting kernel would work with all of rest of the stuff in the Dell Ubuntu package repository?).  At least the stability has improved!  Everything else about the Dell mini 12 is really nice though, it's just slow.

---

### Post by aysiu on 2009-07-04
> **kevinchannon said:**
> Even though my Dell mini 12 has a dual core Atom processor (the EeePC only has a single core) it is noticeably slower.  The Dell Ubuntu used an lpia version of the linux kernel, I guess to get a bit more battery life.  I'm not sure it's worth it though, as I say it can be frustratingly slow.  It'd probably be OK if I knew how to get the lpia bit of the kernel (I suspect that there's some re-compiling steps, and then I'm not sure if the resulting kernel would work with all of rest of the stuff in the Dell Ubuntu package repository?).  At least the stability has improved! I don't think lpia has anything to do with the slow performance. I don't know what it is, but it's not lpia.

I had a similar experience with my Ubuntu-preinstalled HP Mini 1120nr. It wasn't vanilla Ubuntu. It was some HP-customized version of hardy, and it was extremely slow, even after I upgraded the RAM from 1 GB to 2 GB.

After installing the vanilla Ubuntu Jaunty, the performance is much, much improved. And that's also with lpia, so I'm pretty sure it's not an lpia thing.

Maybe Dell and HP have some weird services or background processes that run that slow down the UI somehow...?

---

### Post by kevinchannon on 2009-07-04
> **aysiu said:**
> I don't think lpia has anything to do with the slow performance. I don't know what it is, but it's not lpia.

That's kind of disappointing in a way, now I don't have a clue why it's so slow!

> **aysiu said:**
> Maybe Dell and HP have some weird services or background processes that run that slow down the UI somehow...?

I don't know, I've had a look at system monitor (and top) and there's nothing obvious that's taking up loads of processor.

I've attached screen shot of System Monitor, showing 60 seconds of resource usage.  I have no other applications open, just System monitor (which uses between 8% and 12% of one processor, according to top).  You can see that one core is running at over 60% and the other at over 40%.  This seems a bit extreme for just sitting there not doing any actual work!  What does anyone think?

---

### Post by mikewhatever on 2009-07-04
Try running the following command, **ps aux > ~/Desktop/processes.txt**, then look for processes.txt file on your desktop. Attach it to your next post, if you want.
There is a major problem with GMA500 and Linux, though I'm not quite sure you have the same issue. [Read more...]("http://www.happyassassin.net/2009/01/30/intel-gma-500-poulsbo-graphics-on-linux-a-precise-and-comprehensive-summary-as-to-why-youre-screwed/")

---

### Post by kevinchannon on 2009-07-04
> **mikewhatever said:**
> Try running the following command, **ps aux > ~/Desktop/processes.txt**, then look for processes.txt file on your desktop. Attach it to your next post, if you want.

I did **ps -ejH** (to get a tree view) the output is attached.  I'm not used to looking at so I'm not sure if there's anything telling in there, it all looks like fairly reasonable stuff.

> **mikewhatever said:**
> There is a major problem with GMA500 and Linux, though I'm not quite sure you have the same issue. [Read more...]("http://www.happyassassin.net/2009/01/30/intel-gma-500-poulsbo-graphics-on-linux-a-precise-and-comprehensive-summary-as-to-why-youre-screwed/")

Hmmm... that is a major problem.  I knew that the driver issue for the GMA 500 was bad, but this post makes me wonder what's going on over at Intel?  Do you think that they either have a *much* more developed version of the driver than the author of that blog was able to find, which they include in the Mini 12, or they make some modification to X so that it will work with something similar to the downloadable driver?

---

### Post by mikewhatever on 2009-07-04
The output you posted doesn't show CPU usage by process, which is what we are after. As for the graphics driver, I really don't know. Intel did not reveal any better drivers for gma500, and, adding to the complexity, the current driver has been licensed from a third party company. It's also apparent, that Dell, and not Intel, decides what goes into the mini 12. What strikes me as odd is that Dell ships sluggish systems. Don't they ever test them?

---

### Post by kevinchannon on 2009-07-04
> **mikewhatever said:**
> The output you posted doesn't show CPU usage by process, which is what we are after.

My bad, I thought that maybe there was a tell-tale process name that is known to cause problems or something :) I've attached a correct one.

Edit: I replaced my username with £'s, you can't be too careful these days ;)

---

### Post by mikewhatever on 2009-07-04
That's not too bad. There isn't a single program that uses a lot of CPU. I suspect that the System Monitor was adding a few cycles when you took the screenshot. It can be rather taxing.

---

### Post by kevinchannon on 2009-07-04
> **mikewhatever said:**
> That's not too bad. There isn't a single program that uses a lot of CPU.

That's where I'm stuck, there's no process that I can try killing to see if it speeds things up.  That was kind of why I originally came to the conclusion that it was something to do with everything being somehow intrinsically slow (i.e. the lpia thing).  But if that's not the case either, then...

> **mikewhatever said:**
> I suspect that the System Monitor was adding a few cycles when you took the screenshot. It can be rather taxing.

Yeah, as I said before, it adds ~10%, but not enough to make a huge difference.

---

