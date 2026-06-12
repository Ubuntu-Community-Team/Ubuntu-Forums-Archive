---
title: "Browser slow--firefox's fault?"
date: 2009-05-30
forum: General Help
---

### Post by rreyes1316 on 2009-05-30
I honestly dont do much besides listen to music, record movies, and surf the net. I am running 9.04 and am fairly new to ubuntu. In fact, I am going on 3 months without windows and loving it.

However . . .and here it is . . . my browsing has been slowed down. Not the download time but the response time to scroll with the keyboard or mouse. When ever I use the drop down menus on sites it takes about 3 seconds for it to respond. If I click I fields to fill out it takes a few seconds to respond. Is this a video card issue or some sort of web script that is not working? We are talking about precious lost time here DARN IT!!!:) Seriously, though, it is getting old.

---

### Post by DSClear on 2009-05-30
I want to add a thing, as I also found fire-fox in ubuntu is a bit slow when loading the page with many flash and other elements, the text is very fast, but other elements are slow, is it the nature of fire-fox?

---

### Post by 73ckn797 on 2009-05-30
Some pages that I go to with a lot of graphics are slower than others but generally things move quite well.

[http://www.foxnews.com](http://www.foxnews.com) is one of those.

Look here: [http://www.tweakguides.com/Firefox_1.html](http://www.tweakguides.com/Firefox_1.html) for some tweaks that will improve the speed in Firefox.

---

### Post by rreyes1316 on 2009-05-30
TWEAKGUIDES! Wow. I forgot about that guy. I will check it out.

BTW, it's not just the flashy stuff. Here for example is slow. When I type it takes a few secs for it to display at times.

---

### Post by 73ckn797 on 2009-05-30
> **rreyes1316 said:**
> TWEAKGUIDES! Wow. I forgot about that guy. I will check it out.

BTW, it's not just the flashy stuff. Here for example is slow. When I type it takes a few secs for it to display at times.


What are your computer specs? Video, processing speed and memory can affect everything. I am sure you know that anyway.

Still, could be something with Firefox but I have never had any issue so probably can offer no other solution(s).

---

### Post by TheNosh on 2009-05-30
i find opera to be MUCH faster than firefox on my machine. but if closed source bothers you thats no help

---

### Post by rreyes1316 on 2009-05-31
[HTML] <strike> Windows XP Home</strike>[/HTML] Ubuntu 9.04
AMD Athlon 64 3400+ 2.21 ghz (No OC'ing)
2 GB RAM 
WD RAptor 140 (OS Drive)
4 Disk RAID 5 600GB (Music, Photos, and Movies)
SB Audigy 2 ZS Audio Platinum
EVGA 8800 GTS
ASUSTeK Computer INC. A8N-SLI DELUXE 
Dell 30 inch Monitor 
SONY DVD RW DRU-810A
PC Power & Cooling silencer 750

---

### Post by lovinglinux on 2009-05-31
You could benchmark Firefox at [http://service.futuremark.com/peacekeeper/index.action](http://service.futuremark.com/peacekeeper/index.action) and post the results.

---

### Post by anarchyinc on 2009-05-31
Is it just with Firefox or do you have any sluggishness outside of Firefox? Honestly It seems like it would be your computer or too any programs grabbing resources.

---

### Post by rreyes1316 on 2009-05-31
My score was 988. It almost looks like the site was sponsored by Safari.

---

### Post by raymondh on 2009-05-31
I got 945 but don't have the same issues as the OP

---

### Post by lovinglinux on 2009-05-31
> **rreyes1316 said:**
> My score was 988. It almost looks like the site was sponsored by Safari.

I don't know if it is relevant, but my score is only 360 and don't have those issues.

---

### Post by rreyes1316 on 2009-05-31
I'm not to sure about this bench browsing. I just returned to my computer and did the benchmarking again. This time I got 1008. And this is returning to all the open windows I had left last night.

---

### Post by karmaloop on 2009-05-31
Ever since I upgraded my Ubuntu, my Firefox has been weird.  When I browse the internet, I cant click on the back button, does anyone know how to fix this?

---

### Post by lovinglinux on 2009-05-31
> **rreyes1316 said:**
> I'm not to sure about this bench browsing. I just returned to my computer and did the benchmarking again. This time I got 1008. And this is returning to all the open windows I had left last night.

There is some variation, but in overall the benchmark seems to work fine. The difference between 988 and 1008 is practically irrelevant. I have tested a few browsers several times in different conditions and the results are consistent. For example, when I do the test with a clean FF profile I get about 50% more points than when testing FF with all my extensions loaded. Chromium gives me about 300% more points than FF without extensions and Opera is always lower than FF.

Peacekeeper is developed by Futuremark, which has been on the market for a long time and has, as far as I know, the best tools for 3D benchmarking. 

Nevertheless, I think it is more useful for comparing browsers and to give you some idea of the performance of the browser in different situations.

Have you tried to open the sites you are experiencing problems on another browser like Opera to see if it also have issues? 

You could also try to create a new profile and check if you have the same issues. This would indicate if something on your profile is slowing it down. To create a new profile run this:

```
firefox -P
```

If a new profile doesn't lag, then you could try to optimize your current profile. Please let me know if this is the case, then I will post a tutorial on how to compact FF databases.

---

