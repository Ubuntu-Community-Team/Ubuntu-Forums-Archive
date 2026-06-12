---
title: "very good so far"
date: 2007-02-04
forum: Development CD/DVD Image Testing
---

### Post by ronacc on 2007-02-04
Thanks guys
  Feisty looks like its on the right track . I like herd3 so much I went ahead and wiped my edgy partition and installed herd3 ( I always had issues with edgy) . Startup is noticably faster , hardware detection (on my system atleast) is better. I had no major glitches with either herd 2 or 3 live cd's (other than the bogus add/remove crash report and hanging on shutdown) , the install of herd3 to my HD went smoothly although I wish ubuntu would ask before overwriting my existing grub, I'd rather edit it myself, ubuntu always does a lousy job of detecting/adding other distro's .Not freindly on a mutiboot system.

 things it did right :
got my monitor and resolution right (1440x900 lcd) edgy didn't .
is the only distro I have tried out of many to make setting up and using my PCHDTV card a real snap , modprobe cx88-dvb , install mplayer and watch tv ;)
all other hdw detected and working at bootup including my wired network with one exception .
I like the new control center. saves digging through menus to find frequently used settings and apps. please keep it!

things that needed help :
 the only thing I had to tweek so far is the video card setup , it is correctly identified as nv34 fx5200 128mb in lshw but as in edgy shows up as "generic video card"  and vesa driver in xorg.conf , and while the vesa driver seems better than the one in edgy it still sucks. cured that by changing xorg.conf to nvidia and installing the latest x86_64 beta propriatary driver from the nvidia site (9746).I tried a couple of the drivers from synaptic while still on the live cd but went with the nvidia beta because it worked better.
 Opera is not available through synaptic ( I really hate firefox) and downloading the edgy i386 from the opera site and force installing it yeilds a non working install ( that did work with dapper and edgy), its there but wont start either from the menu or from terminal , the terminal says it cant find the binary when it is pointed right at it.

all in all a good job , looking fwd to the betas and the release ,from what I've seen so far it should be super.

---

### Post by pochu on 2007-02-04
Hi ronacc!

You can install Opera from the canonical commercial repository.

And about your issues, please, report them to Launchpad, in order to let us fix them.

Thanks
Pochu

---

### Post by ronacc on 2007-02-04
I don't have any issues yet with feisty , for me it has "just worked" other than the video card thing  and I was going to install the propriatary driver anyway. I added the canonical feisty comercial repository but opera isn't showing up there either ( I'm 64bit ). I'll keep poking at it and see if I can make it wiggle . Feisty is still alpha so I dont expect every thing on a silver platter. I am impressed with what I have seen so far, no crashes yet even when stress testing my tvcard with fullscreen hd atsc , synaptic updating repositories ,a browser open , and playing a game. the only vaguely anoying thing it did was the sound quit after a while and that may not be feisty's fault the pchdtv card is kind of known for that.and I was scaling to fit my 1440x900 display which is not native hdtv.

---

### Post by feld on 2007-02-11
This raises a good point.

Will Feisty give 64bit users access to 32bit only apps like it should? We shouldnt need to use a chroot to access Opera, Skype, etc. Just because they're 32bit only doesnt mean 64bit users shouldnt have access to them. We can run these applications just fine, so please give us access to them in the repos. It shouldn't be difficult to do at all if you come up with some standards for installing 32bit apps in 64bit Feisty.

I think we can all agree it will help squash Bug #1

---

### Post by pochu on 2007-02-11
Hi feld

I think the problem there is that, as the code is closed, the upstream devs (skype, opera...) are who should make 64bits binaries, because you can't do it without the source code.

Regards
Pochu

---

### Post by ronacc on 2007-02-14
A little addena that dosen't have directly to do with cd testing, after days of trying to get opera working without chroot ,I installed superkaramba for another reason completely ( gdesklets isn't working in 64bit , i filed a bug on that) and I wanted a monitor on my desktop , and when I went to install widgets it called opera to go to the LWP web site and it popped up and has been working ever since ??? now what in the H has supeK a kde prg got to do with opera in gnome ?

---

### Post by wolfger on 2007-09-07
> **pochu said:**
> Hi feld

I think the problem there is that, as the code is closed, the upstream devs (skype, opera...) are who should make 64bits binaries, because you can't do it without the source code.
Feld's point is that AMD64 can run 32 bit pre-compiled apps, so why not let us? No 64-bit version of Opera? Put the 32-bit version in the repos instead.

...which leads to the question that brought me here:
Is there no commercial repos at all yet for Gutsy? Synaptic keeps erroring out on commercial.

---

### Post by pochu on 2007-09-07
The commercial repo is at canonical: [http://archive.canonical.com/](http://archive.canonical.com/)

---

### Post by wolfger on 2007-09-08
> **pochu said:**
> The commercial repo is at canonical: [http://archive.canonical.com/](http://archive.canonical.com/)
So in other words....
```
[DIR] Parent Directory                             -   
[DIR] dapper-commercial/      17-Aug-2007 21:03    -   
[DIR] edgy-commercial/        17-Aug-2007 21:03    -   
[DIR] feisty-commercial/      17-Aug-2007 21:03    -   
```
No, there is no commercial for Gutsy yet.

---

