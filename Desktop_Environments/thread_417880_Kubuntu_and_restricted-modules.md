---
title: "Kubuntu and restricted-modules"
date: 2007-04-22
forum: Desktop Environments
---

### Post by teejay17 on 2007-04-22
Okay, so for 7.04 I thought I'd try something new: instead of going with Ubuntu this time around, I thought I'd give Kubuntu 7.04 a try and do a fresh install. Things are running fine, except for one thing: the restricted modules. I'm new to the KDE environment, so maybe (probably) it's something on my end that's messing up—namely me.
Anyway, what I usually do, and what I tried on Kubuntu, is get the 
```
restricted-modules
``` for 386 machines from Synaptic; usually when I install these, I just have to do a reboot and my wireless card/laptop display, etcetera all work properly. 
On Kubuntu, however, I had to install Synaptic first, and then I proceeded to install the modules as usual. Everything was working fine, the restricted-modules were installed and I was completely satisfied. I rebooted, and my machine was running optimally. 
Until I rebooted again. 
It seems that rebooting Kubuntu again made those restricted drivers disappear somehow, and I'm left without wireless internet and certain other hardware functions I get when these modules are installed. 
There must be a solution to this dilemma? I'd like to reiterate again that I was able to get all hardware working properly—the only problem is that this ability disappears when I reboot. 
Thanks in advance.

---

### Post by teejay17 on 2007-04-22
bump...because I would like to fix my problem.

---

### Post by teejay17 on 2007-04-22
bump.

---

### Post by eyelessfade on 2007-04-22
a bit werd. try installing the restricted modules manualy.
apt-get install linux-restricted-modules-`uname -r`

---

### Post by teejay17 on 2007-04-22
> **eyelessfade said:**
> a bit werd. try installing the restricted modules manualy.
apt-get install linux-restricted-modules-`uname -r`
Okay, thanks. I'll try that and see how it goes. I'll be back to update on my progress.

---

### Post by teejay17 on 2007-04-22
> **teejay17 said:**
> Okay, thanks. I'll try that and see how it goes. I'll be back to update on my progress.
Okay, I tried it out, and this is the message I was given:
> linux-restricted-modules-2.6.20-15-386 is already the newest version.
So I'm back to square one.

---

### Post by teejay17 on 2007-04-22
bump

---

### Post by teejay17 on 2007-04-22
bump

---

### Post by eyelessfade on 2007-04-22
-386?
why don't you try the generic kernel, or do you have a very old computer?
linux-image-generic and linux-restricted-modules-generic is the packages you want

---

### Post by teejay17 on 2007-04-23
> **eyelessfade said:**
> -386?
why don't you try the generic kernel, or do you have a very old computer?
linux-image-generic and linux-restricted-modules-generic is the packages you want
I already have those installed on my computer, it seems, so that doesn't seem to be a solution either.
Thanks anyway, though.

---

### Post by teejay17 on 2007-04-24
What makes matters even more confusing is that this problem sometimes happens, and sometimes it doesn't, totally at random, or at the whim of something I can't understand. For example, I might have two boots where the restricted modules work fine, and then the third and fourth don't, etcetera. This is so weird.

---

