---
title: "nVidia black window bug: finally gone?"
date: 2008-04-12
forum: Desktop Effects &amp; Customization
---

### Post by hyperair on 2008-04-12
I was messing around with a few OpenOffice.org windows open today, and then I realized something.. I hadn't seen the black window bug on my system for quite some time already! So I had some fun... I opened 100 gnome-terminals, none of them ended up as a buggy black window! Before this I usually hit approximately 20 and it'll go black. 

Specs: 
GPU: nVidia Geforce4 MX 440 AGP 8x
Driver: 96.43.05 (nvidia-glx 1:96.43.05+2.6.24.12-16.34)
GPU Memory: 64MB
Resolution: 1280x1024
Colour Depth: 24bit

For those who still have the issue, I'll attach my xorg.conf file. 

If anybody wishes for me to post any other config files please notify me.

---

### Post by chewearn on 2008-04-12
Haven't seen this bug for ages, not since feisty.

---

### Post by hyperair on 2008-04-12
I had it when I first switched to Hardy. Also if you have very little VRAM then only the bug rears its head.

---

### Post by Zorael on 2008-04-12
Fate/stay night, hmmm? :>

I never had it on my Go 7600 PCI-E, for which I'm thankful. I'm one of those bandwagoners whose first version was Feisty, though.

---

### Post by Half-Left on 2008-04-12
it's a bug with the nvidia driver and nvidia supposed to have fixed it in the last release, some people still report the same issues. As I remember it had something to do with VM being drained

---

### Post by hyperair on 2008-04-12
VM? As in Swap? Hmm, my Swap wasn't drained, though if I opened another 100 windows it would have. But I would expect the black window bug to arise in that case. It'll be a wonder if anything can actually continue functioning once swap and RAM are drained.

@Zorael: Yes, Fate/Stay Night. I love the animé. Just watched it recently.

---

### Post by Half-Left on 2008-04-12
Video memory is what I meant since compiz uses that and if it drains you get the black window bug. :)

---

### Post by zzivkovic on 2008-04-18
Bug is still here.
I have nv fx5200/64mb agp card and after 4-5 firefox windows next is BLACK.
:(

---

### Post by hyperair on 2008-04-19
@Half-Left: The bug was fixed in nVidia's 96.43 legacy driver, with better texture_from_pixmap out-of-memory handling. So now, once the VRAM is drained, it will use the system RAM. IMO black windows will still occur, but only once you've exhausted both RAM and swap. But then your system will also go down so it's no surprise.

@zzivkovic: What Ubuntu release are you using and what nVidia driver do you have? To find out, run this command: ```
dmesg | grep -i nvidia
```

For me, I get this:
```
[   40.828995] NVRM: loading NVIDIA Linux x86 Kernel Module  96.43.05  Tue Jan 22 19:36:58 PST 2008
```

---

