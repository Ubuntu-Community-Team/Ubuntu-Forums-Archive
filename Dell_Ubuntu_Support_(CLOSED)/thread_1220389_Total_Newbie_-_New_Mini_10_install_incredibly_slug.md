---
title: "Total Newbie - New Mini 10 install incredibly sluggish. Pls help!"
date: 2009-07-22
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Alaska_Jack on 2009-07-22
Hello everyone! I just took the plunge and installed UNR on my wife's Dell Mini 10. I am *shocked* at how sluggish it is. When I hover over one of the list items on the left- or right-hand side, it takes like *five seconds* to turn dark! And this is just one example. 

One possible clue: I figured out where the system monitor is. If I'm reading this correctly, I have two CPUs which are taking turns being absolutely pegged, even though I'm not actually running any applications.

I really want to love this, but as it is it's unusable. Please help!

[Edit - possible clue. I went into the file system by clicking on one of the icons in the right-hand column. There, things are snappy! Icons colorize instantly when I hover over them, and open right away when clicked. So maybe it's just the "launchpad" interface (is that the right term?) that's running like molasses.]

  - AJ

POSSIBLY RELEVANT INFO:

Dell Mini 10, refurbished
UNR 9.04 (it came with Windows XP, but I wiped that right away and installed a downloaded/checksummed copy of UNR)
CPUs = Intel Z530 x 2 at 1.6 GHz CPU
1 GB RAM
Kernel 2.6.28-11 generic
GNOME 2.26.1
I ordered the 1366x768 display, but UNR only seems to support 1024x768

---

### Post by mikewhatever on 2009-07-23
There is a problem with Dell mini 10 (z530, gma500). To sum it up, Jaunty has no graphics driver for gma500, the effect of which is wrong resolution and sluggish performance. Here is a more eloquent and informative review of the issue. [http://www.happyassassin.net/2009/01/30/intel-gma-500-poulsbo-graphics-on-linux-a-precise-and-comprehensive-summary-as-to-why-youre-screwed/](http://www.happyassassin.net/2009/01/30/intel-gma-500-poulsbo-graphics-on-linux-a-precise-and-comprehensive-summary-as-to-why-youre-screwed/)

There is a 2d driver for Jaunty in the mobile repository, which you can get installed following this guide [http://ubuntuforums.org/showthread.php?t=1213416](http://ubuntuforums.org/showthread.php?t=1213416). It should fix the resolution, but not the sluggishness. It sounds odd, but 9,04 UNR is unusable on Dells with gma500. I suggest either installing Xubuntu, a lighter desktop environment, or something even lighter like LXDE or Fluxbox.

PS: z530 is a single core cpu. I am not quite sure why it shows two (it's the same here), possibly because of multithreading.

---

### Post by snowpine on 2009-07-23
Dell makes a "remix" of Ubuntu 8.04 that has full support for the Mini 10 (it comes pre-installed, in fact). That would be my recommendation in this case.

---

### Post by shodai100 on 2009-07-23
to check what is making the CPU crazy, type : "TOP" into the terminal.

---

### Post by mikewhatever on 2009-07-23
> **snowpine said:**
> Dell makes a "remix" of Ubuntu 8.04 that has full support for the Mini 10 (it comes pre-installed, in fact). That would be my recommendation in this case.

Indeed, there is a 2d driver for gma500 in Hardy Heron.
[http://packages.ubuntu.com/hardy/xserver-xorg-video-psb](http://packages.ubuntu.com/hardy/xserver-xorg-video-psb)
Is that what Dell ships, or is there a different one?


> **shodai100 said:**
> to check what is making the CPU crazy, type : "TOP" into the terminal.

That would be Xorg.

---

### Post by sammyboy405 on 2009-07-23
Hello,

So since this got brought up..  I got a question then..

I tried the Dell 8.04 remix on my Mini 10.   And The performance was horrible! As compared to 9.04 with the makeshift psb drivers.

Also Has there ever been 3d support in any release for the GMA500?

I hear the GMA500 has great graphics, its just not widely supported in software. I guess GMA500 has some odd special needs im guessing?

Also [www.mydellmini.com](www.mydellmini.com)  has a nice little forum too that you might get some more specialized help for your mini10 as most people that goto that forum have a Mini of some kind.  But also check the Mini 12 forums as well as they have the same graphics chipset.

---

### Post by Alaska_Jack on 2009-07-23
Thanks so much for the input everyone! Really good stuff.

I think my options are probably:

* Try out that xserver-xorg-video-psb thing and see if it works. 
* Install another distro, prob Xubuntu.
* Install the Dell special-sauce version of 8.04
* Go back to Windows XP, as I still have the restore discs. Boo!
* Wait and see if there is a UNR of Karmic Koala, and see if that addresses these issues. Until then, do nothing, because hey, this netbook is for my wife, so what do I care?  :^)

I'll have to give it some thought. In the meantime, I might try posting the same query at the link sammyboy405 gave above. Thanks everyone!

  - AJ

---

### Post by Alaska_Jack on 2009-07-24
OK, so first I installed the patch that let me run the mini 10 at native resolution, as mikewhatever above suggested. Works great, although as he noted it did nothing to resolve the sluggishness.

Then another option appeared. While I was literally about to install Xubuntu, I noticed a preference pane to switch from the UNR desktop to the normal Ubuntu one. Since it seemed to be UNR that was pegging the CPU, I clicked it. So now I have basic Ubuntu on the Mini 10. And you know what? It pretty much seems to work fine.

I think I will keep it like this for a while. I may download XFCE and try that, though -- as I understand it, Ubuntu + XFCE is exactly the same as Xbuntu anyway.

  - AJ

---

### Post by ugm6hr on 2009-07-27
You may as well stop the Netbook Launcher from starting if you are not going to use it.  I find it amusing that the netbook version requires more resources than the regular one.

If you want to try Xfce - my guide to configuring the basics (albeit for Mini 9 screen): [http://ubuntuforums.org/showthread.php?p=7631053#post7631053](http://ubuntuforums.org/showthread.php?p=7631053#post7631053)

And to fix the volume issue: [http://ubuntuforums.org/showpost.php?p=7621935&postcount=13](http://ubuntuforums.org/showpost.php?p=7621935&postcount=13)

And, strictly, Ubuntu NBR + xfce4 is not the same as Ubuntu NBR + xubuntu-desktop, which is also, not quite the same as Xubuntu.  I used the first option.

---

