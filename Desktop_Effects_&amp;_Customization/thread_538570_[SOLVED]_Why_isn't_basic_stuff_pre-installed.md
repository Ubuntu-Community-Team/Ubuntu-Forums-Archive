---
title: "[SOLVED] Why isn't basic stuff pre-installed?"
date: 2007-08-30
forum: Desktop Effects &amp; Customization
---

### Post by Officer Dibble on 2007-08-30
Okay, I confess, I've used Windows all my life and I am clueless as to Linux - especially so Ubuntu 7.04.

I wanted to install Wine, but have learned that I need to first go through some lengthy process to install the "Universe" before I can do that. Before I need to do that however I need to get my display sorted out as the onboard video card I have on this system isn't recognised by Ubuntu... that's not a problem though, I just need to download Xorg Via drivers for it... but what's really annoying is that I need to first install some kind of "Subversion" doo-daa before I can even think about the drivers.

Please don't get me wrong, I like the concept of Linux, and I want to know it, love it, and live it... but why can't basic structural resources be integrated into the main install rather than getting everything flat packed, and then only to find you also have to make your own screws and screw holes...

I want Ubuntu Linux on this system, I want Beryl on this system, but I don't want to be an old man before any of that happens... :)

---

### Post by ThrobbingBrain66 on 2007-08-30
All the basics that can be installed by default, are installed by default.  Your situation isn't the norm.  Installing things through subversion *can* be a pain, but chances are a howto exists for your video card. Enabling the universe repo isn't hard either.  Go to System > Administration > Software Sources.  Then check the boxes for universe and multiverse.

Universe has no guarantee of support and bugfixes and multiverse contains "non-free" packages, therefore, they aren't enabled by default.
[http://www.ubuntu.com/community/ubuntustory/components](http://www.ubuntu.com/community/ubuntustory/components)

Beryl isn't in development anymore, so I would suggest using Compiz Fusion:
[http://3v1n0.tuxfamily.org/dists/feisty/eyecandy/](http://3v1n0.tuxfamily.org/dists/feisty/eyecandy/)

---

### Post by Officer Dibble on 2007-08-30
> **ThrobbingBrain66 said:**
>  Go to System > Administration > Software Sources.  Then check the boxes for universe and multiverse.


There isn't "Software Sources" under Adminstration. But there is an "Update Manager" which goes belly-up each time I try to use it with the following error: (There should be an image attached here all being well)

So if "Software Sources" isn't under Administration, would I find it elsewhere?

Many thanks for your help here. :)

---

### Post by Lord Illidan on 2007-08-30
There IS or at least should be a System Sources under Administration, if you are using Ubuntu 7.04. Are you sure you installed Ubuntu correctly? It could be a corrupted disk.

---

### Post by Lord Illidan on 2007-08-30
Try this command :
```
gksu gksu --desktop /usr/share/applications/software-properties.desktop /usr/bin/software-properties-gtk
```

---

### Post by rsambuca on 2007-08-30
Are you even sure beryl will run with Via onboard video?

---

### Post by Officer Dibble on 2007-08-30
> **Lord Illidan said:**
> Try this command :
```
gksu gksu --desktop /usr/share/applications/software-properties.desktop /usr/bin/software-properties-gtk
```

Tried that and got this... (see attached image please)

---

### Post by rsambuca on 2007-08-30
Can you right-click on your menu (top left panel), select "Edit Menus", then select Administration (right at the bottom).  Does "Software Sources" show up on the right hand side?

---

### Post by Officer Dibble on 2007-08-30
This is all I have under 'Administration'... See attached image...

---

### Post by Officer Dibble on 2007-08-30
> **Officer Dibble said:**
> This is all I have under 'Administration'... See attached image...

Trying to attach image again...

---

### Post by Lord Illidan on 2007-08-30
You have a really messed up system there..

I think it's a problem with how you burned the disk..was the Administrator Menu always that small? Did you often meddle with sudo?

---

### Post by Officer Dibble on 2007-08-30
> **rsambuca said:**
> Can you right-click on your menu (top left panel), select "Edit Menus", then select Administration (right at the bottom).  Does "Software Sources" show up on the right hand side?

Ah, good find!! Only problem is that when I tick the box to select "Software Sources" it automatically deselects/unticks again.

I want Ubuntu on all my systems, but I'm not sure I need this kind of thing... :(

---

### Post by rsambuca on 2007-08-30
This is definitely a very rare problem.  I think that something has gone wrong with your installation.

---

### Post by rsambuca on 2007-08-30
If you can get to a terminal, try entering this:```
sudo apt-get install alacarte
```

---

### Post by Officer Dibble on 2007-08-30
> **Lord Illidan said:**
> You have a really messed up system there..

I think it's a problem with how you burned the disk..was the Administrator Menu always that small? Did you often meddle with sudo?

I haven't messed with anything, this is a fresh install, and I don't have a clue what Sudo is. I'm only a noob as far as Linux/Ubuntu is concerned, so I haven't been wandering around tweaking things I know nothing about... yet... :-\"

---

### Post by Officer Dibble on 2007-08-30
> **rsambuca said:**
> If you can get to a terminal, try entering this:```
sudo apt-get install alacarte
```

I did this... what's supposed to happen?

---

### Post by Lord Illidan on 2007-08-30
> **Officer Dibble said:**
> I haven't messed with anything, this is a fresh install, and I don't have a clue what Sudo is. I'm only a noob as far as Linux/Ubuntu is concerned, so I haven't been wandering around tweaking things I know nothing about... yet... :-\"

I'd reburn the whole thing then. Make sure the problem isn't in the file you downloaded, or did you use a shipit cd?

---

### Post by rsambuca on 2007-08-30
Well what did it say after you pressed 'enter'?

---

### Post by Officer Dibble on 2007-08-30
> **rsambuca said:**
> Well what did it say after you pressed 'enter'?

Well, after the first attempt of copying and pasting that line into Terminal I was asked for a password, so I entered my password.

Nothing happened after this, so I pasted the same line again and pressed enter and this time, absolutely nothing happened.

The CD? I downloaded the image and burnt it myself. There were absolutely no issues while installing.

If I need to reinstall this is there an easy way of doing this when it is dual booting with XP?

Whoever solves this is gonna gain some major Guru street cred from it, especially from my point of view.

---

### Post by rsambuca on 2007-08-30
Definitely something wrong with your install.  If you have the original iso file still on your hard drive, I would first check the md5sum.  That will ensure your download was error free.  If that checks out to be fine, then I would burn another cd at a slow speed, and not on a rw disc.  Then run the cd check on the installation cd.  Then install.

---

### Post by Lord Illidan on 2007-08-31
Here, try this : [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto) .

It explains how to run an md5sum. Also, always burn distros at a low speed..I burn mine at 4x.

---

### Post by Officer Dibble on 2007-08-31
What shall I do if what I have now is dual booting with XP? Unfortunately I still need the XP install that's currently on. If I wipe off the current Linux install but keep the boot options bit, will the fresh install of Ubuntu recognise and compensate for the presence of a previous dual boot profile?

---

### Post by ThrobbingBrain66 on 2007-08-31
When you reinstall, choose the manual partitioning method and make sure you use the exact same partition(s) that Ubuntu is currently on. Ubuntu will still recognize your XP partition and your dual-boot will be kept intact.

---

### Post by Shin_Gouki2501 on 2007-08-31
i know this is not very polite still i do:
I play games with my console, no windows, no PC, no Linux FOR GAMING.
But the disc in, and it works ya know.
Have fun with ur wine though :)

---

### Post by Officer Dibble on 2007-08-31
Okay, I'm currently writing another disc at 4X and will follow your advice on manual partitioning.

Incidentally, on the start-up menu of the Ubuntu 7.04 disc there is an option to 'check the disc' or something like that. I did this and according to a self-check the disc was okay.

Is there any possibility there was an option I missed during install that caused the issues that I've been having? The reason I ask is so that I don't do it again. For example, is there an option I should have selected to install Administrative features such as "Software Sources", etc?

---

### Post by ThrobbingBrain66 on 2007-08-31
No, nothing like that.  Just the basic Location, Keyboard, Partition questions along with setting up your username, password etc.  Just take things slow and double check your partition assignments to make sure you don't accidentally over-write XP. Hopefully after this install you'll have a fully functioning system :)

BTW, did you redownload the iso or do an md5sum check on the one you downloaded previously?  Probably not necessary if the disc passed the check, but it would rule out one more possibility.

---

### Post by Officer Dibble on 2007-08-31
> **ThrobbingBrain66 said:**
> 
BTW, did you redownload the iso or do an md5sum check on the one you downloaded previously?  Probably not necessary if the disc passed the check, but it would rule out one more possibility.

This is a very good idea... I'll download from another server/mirror and start again... again. :)

Watch this space... :popcorn:

---

### Post by rsambuca on 2007-08-31
Do you mind if I ask exactly what iso it is you are downloading, just to make sure it is the correct one?

---

### Post by Officer Dibble on 2007-08-31
> **rsambuca said:**
> Do you mind if I ask exactly what iso it is you are downloading, just to make sure it is the correct one?

I'm downloading the following ISO. Previously I downloaded from the Virginmedia server.

Currently downloading:

ISO:
**ubuntu-7.04-desktop-i386.iso**

Server:
**Great Britain (UK) Oxford University Computing Services (Europe)**

My original ISO was the same as above but from this server:

**Great Britain (UK) Virgin Media (Europe)**

Virgin Media is simply my ISP and nothing should be inferred by that... :)

---

### Post by rsambuca on 2007-08-31
Looks like the right one to me!  Sorry for asking, but I just wanted to make sure we weren't overlooking something trivial.

---

### Post by Officer Dibble on 2007-08-31
> **rsambuca said:**
> Looks like the right one to me!  Sorry for asking, but I just wanted to make sure we weren't overlooking something trivial.

Oh, don't apologise please. You could have saved me a lot of trouble by picking up on a very obvious mistake.

Happily I'm now getting different results. On installing, Ubuntu now has the Administrator > Software Sources option, and it has automatically detected the availability of updates and is currently downloading them.

A curious thing happened while installing though, and I remember it happening the first time around now too... This came during the install process, and first time around I thought it was normal, but you guys would know better. Please see the attached image. Can I expect further trouble down the line because of this or is it something that has fixed itself?

---

### Post by FuturePilot on 2007-08-31
At first glance I would say that's normal if there were errors corrected in the file system. I have seen that before. However the fact that it says fsck died with exit status 3 has me wondering.

---

### Post by Officer Dibble on 2007-08-31
Well, everything seems to be running a treat, your support has been absolutely brilliant, and enormous thanks to everyone that helped. =D>

Time for a group hug me thinks. :)

I need to locate some S3 Unichrome drivers for the onboard video card, but I don't think I'll bother on that system, I'll just get a decent graphics card instead... which I suppose leaves me with one last question... which flavour of video card does Ubuntu love the most? Nvidia or ATI?

---

### Post by rsambuca on 2007-08-31
Absolutely no real choice in this regard.  Go with nVidia.  While both have their issues, it is generally agreed upon that nVidia has waaaay less issues.

---

### Post by FuturePilot on 2007-08-31
> **rsambuca said:**
> Absolutely no real choice in this regard.  Go with nVidia.  While both have their issues, it is generally agreed upon that nVidia has waaaay less issues.

+1 on that. ATI support for Linux is terrible. Intel is also supported pretty well on Linux.

---

### Post by Zenham on 2007-08-31
I'd have to guess that you are trying this with an account added after the installation which wasn't given administration privileges. If that's the case, log in with the account you created during installation and run System->Administration->Users and Groups, choose the account you'd like to be abile to admin from, click Properties, go to the privileges tab and check the box next to "Administer the System".

If your video card doesn't work with X out of the box, it's most likely a recent chipset from a lesser-known vendor.

My biggest and best solution to offer you for "ease of everything" is to snag a machine that's a couple of years old which you don't need otherwise, install Ubuntu on there, and get accustomed to how it functions on a "simpler" piece of hardware first. That way, when you have trouble with more cutting edge components, you'll have a bit of context to work with.

Ubuntu is definitely simple to set up and use compared to most *nix distros out there, but it's still a complex multiuser operating system under the hood. It's never going to be as simple as Windows in most cases. Not only do most (opinion) hardware vendors not bother to write drivers for their own hardware under Linux, but it's complicated by the fact that you *can* get under the hood much more so than in Windows.

In any case, welcome to Ubuntu, and best of luck. It's a good OS, don't give up because you've hit a few bumps in the roads. Like anything else, understanding comes with experience.

Cheers,

---

### Post by Officer Dibble on 2007-08-31
Hi Zenham,

The problem was with a duff installation due to a duff disc. Once I downloaded another image and wrote another disc the install went through without issue. I've since installed Wine and the Windows app I needed to use, so this problem is sorted now with many thanks to the generous people of this thread.

Considering what you have explained though, it is very possible that the duff install messed up the admin access among other things. I really don't have the knowledge or experience you have to say otherwise.

It's interesting you suggested using an older machine. The first time I ever installed Ubuntu was on a PIII 500 system... and it loved it. As I hope to next have a go at CompFizz (sp?) it needed to sit on something with a better spec... so I chose a better rig to experiment on... my wifes computer. (rather than mine! :))

With the help and confidence I've gained with Ubuntu through the people here, I'm definitely going to put it on my own computer next.

Comments and corrections are always welcome with me Zenham, thanks for dropping your suggestion in.

---

### Post by Palmyra on 2007-09-02
If you have an option, and you are not a heavy gamer/demand a lot from your system video graphics wise, go with a well supported Intel graphics cards.  If you are a gamer, go with advice from fellow gamers.  If you want Compiz Fusion, I say an Intel card is perfectly fine, but some will tell you an Intel card is not enough.  

Whatever you do, the more homework you do, the less regret there will be in the end.

---

