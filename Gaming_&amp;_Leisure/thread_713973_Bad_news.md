---
title: "Bad news"
date: 2008-03-03
forum: Gaming &amp; Leisure
---

### Post by eragon100 on 2008-03-03
Quote form phoronix:

Is this the end of the proprietary NVidia drivers
[http://thread.gmane.org/gmane.linux.kernel/646638](http://thread.gmane.org/gmane.linux.kernel/646638)

Quote:
Originally Posted by drago01
Hi,
init_mm is no longer exported in 2.6.25, because there are no in tree modules that use it.
But the closed sources nvidia drivers are using it.
Is it possible to reexport this symbol to let the driver work with this kernel?
Chris Snook from Red Hat answered:

Quote:
Originally Posted by Chris Snook
The fact that there are no in-tree modules that use init_mm is rather
compelling evidence that it's not a necessary part of the kernel module API. Nvidia needs to fix their code. If this is a burden, perhaps they should publish their code under a GPLv2-compatible license so we can show them how to do it.
And later on:

Quote:
Originally Posted by Chris Snook
High-performance graphics developers are pretty much the last people on earth I want to see writing code that calls init_mm. These people patent their bugs, rather than fixing them, when they turn out to make things go a little faster and generate "mostly correct" results. I think we have a lot to teach them about kernel driver development, including how to get by without init_mm being exported.
As it seems now, the Change was reversed, but as German Newsticker heise.de points out this is just a temporary step backwards allowing developers of external kernel modules like VirtualBox to adapt their code.

Bye Bye 3d (and thus games) on linux?

---

### Post by Melcar on 2008-03-03
There is still AMD/ATI.  Intel and AMD seem to be doing all the right moves when it comes to open source.  I don't think nvidia will allow itself to be left out thought.

---

### Post by Sockerdrickan on 2008-03-03
never bye bye... they'll fix it

---

### Post by eragon100 on 2008-03-03
Why would the kernel developers BREAK it in the first place, and undoubtly manage to piss of lots of users? (if only because I don't want to buy another very expensice high-end gaming card because ATI will be working better than nvidia in a few months if this happens)

Open-source or not, the ATI drivers are much worse than the nvidia closed-source drivers, so i use nvidia, for wich I paid 300 euro's a month ago :(

---

### Post by karth on 2008-03-03
> **eragon100 said:**
> Open-source or not, the ATI drivers are much worse than the nvidia closed-source drivers, so i use nvidia, for wich I paid 300 euro's a month ago :(

It's more a matter of potential improvements than immediate efficiency.
It's up to the devs to improve their own proprietary software, and up to anyone to get into open source software.

Nvidia drivers may be more efficient right now, but in one year or two, it may change :)

---

### Post by disturbedite on 2008-03-03
> **eragon100 said:**
> Why would the kernel developers BREAK it in the first place, and undoubtly manage to piss of lots of users? (if only because I don't want to buy another very expensice high-end gaming card because ATI will be working better than nvidia in a few months if this happens)

Open-source or not, the ATI drivers are much worse than the nvidia closed-source drivers, so i use nvidia, for wich I paid 300 euro's a month ago :(
if you read the original post again maybe this time you'll see its nvidia's fault, not the kernel devs.

---

### Post by DoktorSeven on 2008-03-03
> **disturbedite said:**
> if you read the original post again maybe this time you'll see its nvidia's fault, not the kernel devs.

Actually it is the kernel devs, they had init_mm in the API and are now trying to remove it, and nvidia uses it in their code.

Honestly, as many times as the kernel devs have broken the nvidia driver (it's been quite a few times, if you weren't aware), I'm surprised nvidia still puts up with it.  Kernel devs don't care about playing well with closed-source drivers, and while it would be nice for nvidia to open (GPL) their drivers, I don't believe being antagonistic is a very good solution.

I'm with nvidia here.  You don't just arbitrarily change an API, no matter what.

---

### Post by Extreme Coder on 2008-03-03
> **eragon100 said:**
> Quote form phoronix:

Is this the end of the proprietary NVidia drivers
[http://thread.gmane.org/gmane.linux.kernel/646638](http://thread.gmane.org/gmane.linux.kernel/646638)

Quote:
Originally Posted by drago01
Hi,
init_mm is no longer exported in 2.6.25, because there are no in tree modules that use it.
But the closed sources nvidia drivers are using it.
Is it possible to reexport this symbol to let the driver work with this kernel?
Chris Snook from Red Hat answered:

Quote:
Originally Posted by Chris Snook
The fact that there are no in-tree modules that use init_mm is rather
compelling evidence that it's not a necessary part of the kernel module API. Nvidia needs to fix their code. If this is a burden, perhaps they should publish their code under a GPLv2-compatible license so we can show them how to do it.
And later on:

Quote:
Originally Posted by Chris Snook
High-performance graphics developers are pretty much the last people on earth I want to see writing code that calls init_mm. These people patent their bugs, rather than fixing them, when they turn out to make things go a little faster and generate "mostly correct" results. I think we have a lot to teach them about kernel driver development, including how to get by without init_mm being exported.
As it seems now, the Change was reversed, but as German Newsticker heise.de points out this is just a temporary step backwards allowing developers of external kernel modules like VirtualBox to adapt their code.

Bye Bye 3d (and thus games) on linux?
Relax a bit, I have no doubt nVIDIA will respond to this and fix their drivers, and besides, there are other graphic card makers such as AMD,VIA,Intel..

---

### Post by houstonbofh on 2008-03-03
Frankly if it comes to a showdown, I am not sure who would win.

Run the latest kernal, and buy a new card, or freeze on 2.6.26 and run nvidia...  A lot of people with money invested in nvidia graphics would have no reason to get the new kernal.  Myself included...  A showdown helps no one but egos.

---

### Post by Sammi on 2008-03-03
Exactly how hard will it be for Nvidia to code around this change in kernel api?

Without knowing the answer to this question, we're just wasting time.

---

### Post by BigSilly on 2008-03-04
Any more news about this? Should we be worried?

---

### Post by Melcar on 2008-03-04
> **BigSilly said:**
> Any more news about this? Should we be worried?


More than likely nvidia will work around this, like they have always done when it comes to their Linux drivers.  I doubt they will leave the Linux market to Intel and AMD.

---

### Post by eragon100 on 2008-03-04
I doubt the're will be a linux market anymore! People change to Ubuntu because it's easy to install and setup. You can't go tell them "Yeah your nvidia card won't work if you use the latest kernel which has all the security and other bugs fixed and uses less power and everything, and ATI doesn't run correctly on linux either, but the drivers are open-source so maybe that will change in one or two years. Or maybe not". I don't think they'll switch :mad::mad::mad:

---

### Post by eragon100 on 2008-03-04
By the way, I send a mail to the person who invented this idea. I told him that i didn't think many people, myself included, would be very hapy which this change if it would break, even temporarily, support for their graphis card. He responded by telling me that it isn't a good idea to game on linux any way and that i should just get a dual-boot if the change i couldn';t play games anymore! :confused:

---

### Post by BigSilly on 2008-03-04
> **eragon100 said:**
> He responded by telling me that it isn't a good idea to game on linux any way and that i should just get a dual-boot if the change i couldn';t play games anymore! :confused:

Screw that! I enjoy my gaming on Linux thanks. There might not be the commercial aspect of it (yet) but I still very much enjoy what's on offer regardless.

They'd better come to some solution. I'm surprised this hasn't been discussed by the wider Linux news sites. It could be nothing; a storm in a teacup. But if someone decides not to play ball, then we could all suffer.

---

### Post by janfsd on 2008-03-04
Well, we could always fork the kernel. :D

---

### Post by eragon100 on 2008-03-04
Isn't the kernel LGPL? Couldn't Nvidia do this and distribute a working kernel for automatic installation with their binary driver? I don't know relly much about the linux kernel, but would it be technically possible to make an extremely asy way of automatically changing the kernel when you install nvidia binary drivers?

And by "forking it", you mean that Ubuntu would simply distribute its own kernel to work with nvidia drivers, right?

---

### Post by PC_load_letter on 2008-03-04
> **eragon100 said:**
> By the way, I send a mail to the person who invented this idea. I told him that i didn't think many people, myself included, would be very hapy which this change if it would break, even temporarily, support for their graphis card. He responded by telling me that it isn't a good idea to game on linux any way and that i should just get a dual-boot if the change i couldn';t play games anymore! :confused:

I'm appalled to say the least about this dev's reply. 3D is not just used in games, how about 3D animations used in modelling and engineering applications? How about using Ubuntu studio now with Blender if I have an Nvidia graphics card? And what's the problem with Linux being popular
among gamers? 
How old is the dev, 5 yeasr old? Or am I missing something? Wasn't there any kind of communication with nvidia prior to this crucial decision been made?

---

### Post by eragon100 on 2008-03-05
> **PC_load_letter said:**
> I'm appalled to say the least about this dev's reply. 3D is not just used in games, how about 3D animations used in modelling and engineering applications? How about using Ubuntu studio now with Blender if I have an Nvidia graphics card? And what's the problem with Linux being popular
among gamers? 
How old is the dev, 5 yeasr old? Or am I missing something? Wasn't there any kind of communication with nvidia prior to this crucial decision been made?

No none at all, nvidia was totally surprised by this action :(

---

### Post by desertboy on 2008-03-05
Nvidia will certainly release new drivers soon enough, does this effect Hardy users? I doubt this would effect us Gutsy users and I can't see Ubuntu running updates to the kernel which break 1/3 the PC's running Ubuntu.

I bought my Nvidia card specifically because of good Linux support (And better performance than the Intel ones) and have never had a day's problem with it. Which is more than I can say for my Ati mobility chipset or the intel chipset in my eeepc, which both display compiz related 3d issues.

---

### Post by happyhamster on 2008-03-05
> **desertboy said:**
> Nvidia will certainly release new drivers soon enough, does this effect Hardy users?
No. Hardy uses a 2,6.24 kernel, while this discussion is about 2.6.25. (And perhaps even later, see: [http://marc.info/?l=git-commits-head&m=120431164622559&w=4](http://marc.info/?l=git-commits-head&m=120431164622559&w=4))

---

### Post by happyhamster on 2008-03-05
BTW: as long as the following sticky exists (Nvidia linux forum), I think there's nothing to worry about: 
[http://www.nvnews.net/vbulletin/showthread.php?t=61644](http://www.nvnews.net/vbulletin/showthread.php?t=61644)

:)

---

### Post by BigSilly on 2008-03-05
Well, if they're going to get snooty about things, there's always ATI. They've been slow to react in the past, but it looks as though they are improving support all the time. Isn't it true that they are actively supporting the development of open drivers and documentation too?

I'm up for buying a new PC this year, and it's going to be a solely Linux based machine. I'll see how things pan out, but if NVidia get the monk on with Linux, then I'll buy ATI. It's that simple.

Problem solved. :)

---

### Post by eragon100 on 2008-03-05
Yes, but I don't want to buy a new pc to be able to use my video card which worked perfectly. I hava a good pc, and I don't want 100ds of $$$ for a new one:(

---

### Post by lingnoi on 2008-03-07
I have to agree with the kernel devs on this, If everyone is moving in a certain direction then it doesn't make sense to keep a bad implementation in just so one company's drivers work. 

It's up to nvidia to update their drivers and avoid code rot, not for the Linux devs to cater to a closed source company.

As for ATI well, they haven't even released their 3D specs yet, only 2D is supported in the open source driver and I hear that even that isn't great.

It comes down to this. Linux devs are more concerned with doing things the right way, not fixing other peoples problems. This happens with others too for example the UVC driver not working in Skype. If it is a bug in Skype then it's their problem. They're not going to put work arounds in their code when the other code should be fixed instead.

It's not a closed vs. open thing, It's a better design thing.

The thing is, what's stopping you from just using your old kernel until Nvidia update their drivers?

---

### Post by SunnyRabbiera on 2008-03-07
But Nvidia has been a ally of linux for a little while now so I doubt Nvidia is going anywhere.
I trust them more then ATI at this point

---

### Post by BigSilly on 2008-03-07
> **lingnoi said:**
> I have to agree with the kernel devs on this, If everyone is moving in a certain direction then it doesn't make sense to keep a bad implementation in just so one company's drivers work. 

It's up to nvidia to update their drivers and avoid code rot, not for the Linux devs to cater to a closed source company.

As for ATI well, they haven't even released their 3D specs yet, only 2D is supported in the open source driver and I hear that even that isn't great.

It comes down to this. Linux devs are more concerned with doing things the right way, not fixing other peoples problems. This happens with others too for example the UVC driver not working in Skype. If it is a bug in Skype then it's their problem. They're not going to put work arounds in their code when the other code should be fixed instead.

It's not a closed vs. open thing, It's a better design thing.


On that score I'd be absolutely amazed if NVidia didn't offer an improved solution for Linux users. They've been an excellent choice for Linux users this far, and I'm sure they'll keep it up for the future. They constantly update their Windows drivers in order to perpetuate an improved experience for the end user. Why should Linux users be any different? Especially as Linux uptake has improved greatly in recent times, across home and profession users.

Ego clashes aside, there's no reason not to constantly improve Linux support, surely. I'm sure this will be sorted. 

/crosses fingers....

---

### Post by ronacc on 2008-03-09
If this is a necessity for the improvement of the kernel it will be a bitter pill to swallow , I build my own pc's and use nvidia cards becase they have always had the best linux support . If this is a thinly disguised move by the "idealogical purists" to stick a finger in the eye of propriatary software , it is just another example of why we have such a problem luring people to lunux and squasing bug #1.

---

### Post by houstonbofh on 2008-03-11
> **ronacc said:**
> If this is a necessity for the improvement of the kernel it will be a bitter pill to swallow , I build my own pc's and use nvidia cards becase they have always had the best linux support . If this is a thinly disguised move by the "idealogical purists" to stick a finger in the eye of propriatary software , it is just another example of why we have such a problem luring people to lunux and squasing bug #1.
The way the kernel dev worded it, it sounds more like a finger in the eye...  And it didn't win me over, and I am an avid user of Linux...

---

