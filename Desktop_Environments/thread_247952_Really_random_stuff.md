---
title: "Really random stuff"
date: 2006-08-31
forum: Desktop Environments
---

### Post by bergfly on 2006-08-31
After been a KDE fan for a while, I have tried Ubuntu with gnome.  At first it seemed fine, but now has numerous problems, which could all be related. I am running it on a Dell Latitude D510 with an Intel 915 Graphics processor. 

The first problem, since day one of gnome has been the computer will not power off. It will power down to the text interface and then says 

will now haltswap.... plus random characters

it hangs there indefinately. Obviously i have to then power off with the on/off button. Sometimes it powers off by itself, apparently at random.

Secondly during normal use it will just hang for 5 to 10 seconds, not accepting any input, from mouse or keyboard. This makes it very difficult to use. It has done it at least a dozen times in typing this, which is more than a little frustrating, Sometimes, it works for hours without doing this at all. I saw a tread mention the powernowd daemon might have something to do with this, so removed this with no affect.

Since todays upgrade, compiz now will not display window borders, which is probably unrelated and not too much of an issue.

I assume most of these issues are gnome related as KDE is smooth and fast on this machine. 

Any ideas much appreciated. Let me know what info to post.

---

### Post by bergfly on 2006-09-01
Anyone want a crack at this. I have tried a bit, but googling the word haltswap returns only this post on the whole big internet. I need a few pointers here

---

### Post by orb9220 on 2006-09-01
What kernel are you using? And also check your bios and how dpms,acpi ect  are handled.

Just shooting in the dark. But if I had to guess it would be a kernel vs  mobo chipset sort of thing.

Sorry couldn't be more help.

---

### Post by bergfly on 2006-09-03
Could well be. I am using kernel 2.6.15-26-686. However, this did also happen on the previous kernel, which was the standard 386 one. The main reason i upgraded was to get past this, but no joy. Any idea what bios settings might be causing the issues. I haven't done much to the default config. Thanks for the reply though, I know there is not much to go on.

---

### Post by bergfly on 2006-09-04
I am begining to think this is wireless card related. Going through dmesg, found this. Any idea how to update, or is this a case of rebuilding the kernel?


[I][17179590.724000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.1.1
[17179590.724000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[17179590.724000] Warning: PCI driver ipw2200 has a struct device_driver shutdown method, please update![/I]

---

### Post by someguyouknow on 2006-09-04
For borders on windows, install cgwd themer.
The rest of this stuff i am not sure about. It seems like you have multiple desktops on one computer and i have not had good success with that at all.

---

### Post by bergfly on 2006-09-04
thanks mate. Unfortunately CGWD themer is installed and does absolutely nothing. Might have something to do with the way I installed Compiz, but to be honest that is the least of my worries. The problem with shutdown has been from day one, that is a clean install of only Dapper drake. All additional things, like upgrading the kernel and putting KDE on have neither fixed the problem, nor made it worst. The constant freezes in gnome have got so bad, that I can't use it at all now, so use KDE instead

---

