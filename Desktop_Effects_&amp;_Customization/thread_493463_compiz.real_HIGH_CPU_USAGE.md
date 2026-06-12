---
title: "compiz.real HIGH CPU USAGE"
date: 2007-07-05
forum: Desktop Effects &amp; Customization
---

### Post by AriciU on 2007-07-05
Is it normal to have a 35-40% cpu usage when not doing anything (firefox, pidgin and amarok open) and 75-90% when rotating cube, alt-tabing, browsing firefox, etc, etc, etc

The culprits in my case are compiz.real and Xorg.

For example, when opening the bookmarks tab in Firefox and scrolling thru it CPU usage jumps to 80-100% (xorg + firefox).

I can't believe Ubuntu + Compiz fusion is running slower and choppier then Vista with only 1gb ram.

AMD 3500+
Geforce 6800gt

---

### Post by Barleyman on 2007-07-16
I have the exact same problem on a fresh install of feisty.

I tried the nvidia restricted driver first and then the driver directly from nvidia

My video card
GeForce 7600 GS

If I leave the computer on overnight, X is completely unresponsive with compiz.real and Xorg using 99%cpu.

I have read something about a legacy driver for some nvidia cards, but am unsure if my card is one that should be using that.

---

### Post by _simon_ on 2007-07-16
> **AriciU said:**
> Is it normal to have a 35-40% cpu usage when not doing anything (firefox, pidgin and amarok open) and 75-90% when rotating cube, alt-tabing, browsing firefox, etc, etc, etc

The culprits in my case are compiz.real and Xorg.

For example, when opening the bookmarks tab in Firefox and scrolling thru it CPU usage jumps to 80-100% (xorg + firefox).

I can't believe Ubuntu + Compiz fusion is running slower and choppier then Vista with only 1gb ram.

AMD 3500+
Geforce 6800gt

No, it's not normal.

As to why it's happening for you guys, I'm afraid that I don't know.

I'm running 64bit Feisty, X2 4600+, 2Gig Ram, 256MB 7900GS.

---

### Post by sagara on 2007-07-17
> **_simon_ said:**
> No, it's not normal.

As to why it's happening for you guys, I'm afraid that I don't know.

I running 64bit Feisty, X2 4600+, 2Gig Ram, 256MB 7900GS.

I have the same problem as them... fresh install as well... what NVIDIA drivers are you using?  the restricted ones that come with feisty?

---

### Post by _simon_ on 2007-07-17
No, I used the Envy script to install my drivers.

Currently using 100.14.11

---

### Post by sagara on 2007-07-17
Ok, I will try installing my drivers through envy.

Silly question, how do I check what current NVIDIA drivers I am using?

---

### Post by sagara on 2007-07-17
Nevermind... I am now also using 100.14.11 but I still have the high CPU usage...

---

### Post by What The Deuce on 2007-07-18
This might not be the answer, but i used the add/remove app to get the nVidia drivers and i always had an abnormally high cpu usage.  But then i reinstalled them and I have found that the nVidia driver from automatix is giving me less CPU usage...can't explain it.

---

### Post by sagara on 2007-07-18
Could you tell me what NVIDIA drivers you are using?

---

### Post by marsmissionaries on 2007-07-18
compiz fusion uses high cpu usage on any configuration. not just nvidia.

---

### Post by UncleJock on 2007-12-31
This doesn't have anything to do with drovers.
Right click on your desktop. Select "Change Desktop Background".
Select tab "Visual Effects"
Select none.
Note the sudden drop in CPU usage.
The effects work great on a high powered machine with no noticeable drop in performance.
The effects are cool, but one can live without them for the performance increase.

---

### Post by slempl on 2008-03-09
Hey guys... i've just made my compiz.real to use max 6% of cpu and i have 1.5GHz core2duo.
I've just decreased cube transparency to 0. CPU went from 48% to 4% and a few sec later went to 6%.
Hope this helps you all.  :)

---

### Post by sagara on 2008-03-09
I'm now using Gutsy with the restricted nvidia drivers and using the compiz fusion that comes in the ubuntu repositories.  The high CPU usage is now gone.

During cube rotate with transparencies on, the CPU will go up by max 20%

---

### Post by EliteTech on 2008-03-22
I started having this problem aswell. If your hardware isn't up to today's standards then you will need to disable some of the effects compiz uses. I tweaked mine out some and I now am getting 0% usage for compiz.real under idle, and max 4% while rotating cube.

---

### Post by xvedejas on 2008-04-01
I randomly and unexplainably got this problem. Before, compiz would take 0% cpu always. Now, it's 50% (I'm running a dual-core). And the only thing I did differently was install gnome-partition-editor? What?!

---

### Post by ben2talk on 2008-05-01
This is a bug, I think. I have Nvidia 8600 (Asus built) and had no troubles with any settings for 4 months. Today I ended up backing up my entire home folder contents and trying to start again from scratch - but when compiz-real is running, it hogs CPU and freezes my com. I have core2duo, 3
GB Ram - but the issue here is that CPU isn't for the eyecandy. Eyecandy should be handled only by the GPU. No GPU, no eyecandy! With XP, Nvidia have settings for transparency etc. Something is wrong with Hardy maybe - what do you run?

Right now it's running nicely - with compiz enabled. I didn't fix it! It will come back :(

---

### Post by enbuyukfener on 2008-05-06
> **ben2talk said:**
> This is a bug, I think. I have Nvidia 8600 (Asus built) and had no troubles with any settings for 4 months. Today I ended up backing up my entire home folder contents and trying to start again from scratch - but when compiz-real is running, it hogs CPU and freezes my com. I have core2duo, 3
GB Ram - but the issue here is that CPU isn't for the eyecandy. Eyecandy should be handled only by the GPU. No GPU, no eyecandy! With XP, Nvidia have settings for transparency etc. Something is wrong with Hardy maybe - what do you run?

Right now it's running nicely - with compiz enabled. I didn't fix it! It will come back :(
Very similar scenario.

8660M GT, tried several drivers (currently 173.08), problem improves and worsens over time seemingly at random, high CPU usage when using GUI with Compiz Fusion on, even similar CPU and RAM (Core 2 Duo 1.8GHz and 2GB RAM). Using hardy but this problem was on gutsy too.

---

### Post by alfaalex101 on 2008-05-08
I'm using a Athlon XP2000+, 512mb ram and a Nvidia 6200 agp and I'm getting on average 49fps (when moving the cube)! Smooth enough!! Maybe you should do  a fresh install and remove any trash that any packages left over? (yes - I'm talking to you Compiz fusion and Compiz get)

---

### Post by carloslosgrande on 2008-05-08
[FONT="Comic Sans MS"]I'm also having this problem and I noticed that shutting down amarok fixes the problem immediately. I tested it repeatedly.
I've also been having a couple of difficulties with amarok that I had before (Dapper, Feisty), that were fixed with updates then, but have now returned with Hardy.[/FONT]

---

### Post by pp7 on 2008-07-22
I had this problem then set cube transparency (in advanced desktop effects settings.. desktop cube.. transparent cube) to 100.0000 and now it uses alot less cpu.

---

