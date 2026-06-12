---
title: "Question about Beryl"
date: 2009-06-06
forum: Desktop Environments
---

### Post by swish on 2009-06-06
Hey all,
I am new to using linux. 
I got Ubuntu and was wondering how to install the beryl manager.
If i google it, there are instructions on beryl for ubuntu fiesta, but there are no instructions for installing it on regular ubuntu. My version is 9.04.
To be specific I want the 3d cube desktop.

thanks for any help,

Swish

---

### Post by kayvortex on 2009-06-06
You're a couple of years late! Beryl was merged back into Compiz and no longer exists. All those fancy graphics are now a part of Compiz Fusion. And, luckily, it's pre installed: just go to *System* -> *Preferences* -> *Appearance*, go to the *Visual Effects* tab and choose the *Extra* option.

Edit:
If you want the desktop cube, you'll also have to install the settings manager. Run this command in a terminal:
```
sudo aptitude install compizconfig-settings-manager
```
Then, in a terminal enter:
```
ccsm
```
In the program that opens up, go to the section headed *Desktop* and check the box *Desktop Cube* (and click on the Disable button **if** any warning box pops up).

Edit edit:
Let me know if anything makes no sense to you and I'll be more explicit on what to do.

---

### Post by swish on 2009-06-06
Hey thanks for the reply.
I seem to be having a problem though; when I try to activate the effects, the 
screen blinks, but it gives me a cannot apply effects error.
Maybe its a driver issue?
  Here are my technical specs:

---

### Post by swish on 2009-06-06
Hey thanks for the reply.
But I seem to be having some problems.
When I try to apply the effects, the screen flashes for a second,
but then it says effects could not be applied.
I think it maybe a driver issue.
I checked Hardware Drivers and there is only one driver listed there which is my wireless card.
If you need technical specs:
Dell Laptop
Intel Core 2 Duo 2.4 Ghz
4 GB RAM
Intel onboard graphics card(tell me if you need the exact specification to help me out)
I am dual booting vista and ubuntu, if that has any affect.

Please help me if you can.

Thanks,
Swish

---

### Post by kayvortex on 2009-06-07
Most likely it will be a driver issue. Could you tell me what graphics card you are using and I'll do a bit of research. Just type in (Edit: into a terminal, I mean):
```
lspci
```
and post what comes out if you don't know off the top of your head.

---

### Post by 3rdalbum on 2009-06-07
> **kayvortex said:**
> Most likely it will be a driver issue. Could you tell me what graphics card you are using and I'll do a bit of research. Just type in (Edit: into a terminal, I mean):
```
lspci
```
and post what comes out if you don't know off the top of your head.

> Intel onboard graphics card(tell me if you need the exact specification to help me out)

There are known issues with Intel drivers on Ubuntu 9.04, unfortunately. I haven't used Compiz on Intel drivers on 9.04 so I don't know how to fix the issue, but there are lots of threads about this on the forums. (do a search for "desktop effects intel", probably).

---

### Post by swish on 2009-06-07
Hey,

Terminal lists the following two drivers for graphics:

00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)

In the mean time, I will try to search the forums like 3rd album said.

thanks,

Swish

Edit: By the way my old laptop, when I ran Ubuntu 7 a year or so back, there were some effects. For example, when I dragged the windows
it would "swirl." That laptop had a intel onboard graphics as well, so 3rd album you sure its because of intel? My best guess is that 
Ubuntu 9 has a "updated" driver for intel chipset. Is there a way I can test the ubuntu 7 driver that I used on my old laptop?

---

### Post by kayvortex on 2009-06-07
OK, as 3rdalbum says, there are a few guides on what to do around here. Googling your card, I came across thiese:
[http://www.rudkin.me.uk/2009/04/22/how-to-get-your-intel-gm965gl960-working-with-compiz-on-ubuntu-jaunty-jackalope/]("http://www.rudkin.me.uk/2009/04/22/how-to-get-your-intel-gm965gl960-working-with-compiz-on-ubuntu-jaunty-jackalope/")
[https://bugs.launchpad.net/ubuntu/jaunty/+source/compiz/+bug/363821]("https://bugs.launchpad.net/ubuntu/jaunty/+source/compiz/+bug/363821")
So just give them a read and follow their instructions.

---

### Post by swish on 2009-06-07
Hey,

Kayvortex the link you sent me was the solution.
It works perfectly now.


Thanks,

Swish

---

### Post by swish on 2009-06-07
Sorry for the double post.

But I ended up disabling because my system crashed when i tried to enable the desktop cube.
Even without the desktop cube, my computer felt unstable.
I guess intel is just no compatible with compiz. 

I hope it will be fixed in future updates.

However, is there a way I can report this so that Ubuntu tries to address this on their next release?

---

### Post by kayvortex on 2009-06-07
Well, the bug has been registered already and is rated "critical". If they get a fix sorted they might patch it into a Jaunty release, or else have it fixed for Karmic (which will be released in a few months time). Keep an eye on the bug reports and read through the comments to see what's happening and what others are suggesting or trying:
[https://bugs.launchpad.net/ubuntu/jaunty/+source/compiz/+bug/363821]("https://bugs.launchpad.net/ubuntu/jaunty/+source/compiz/+bug/363821")
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/359392]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/359392")

---

### Post by swish on 2009-06-07
Okay thanks, I will keep an eye on the bug report.
Hey by the way when there is a new release of Ubuntu, will the update manager take care of it
or will I have to burn a new iso?

Swish

---

### Post by phantom3113 on 2009-06-07
It will be available through the update manager. Some prefer to burn a new iso since straight upgrading can sometimes "break" packages, but it's generally a matter of personal preference.

---

