---
title: "Ut2004 on Ubuntu with dual-core"
date: 2006-08-15
forum: Gaming &amp; Leisure
---

### Post by roe_polak on 2006-08-15
I'm fairly new to Ubuntu and linux in general. Actually I installed Ubuntu only a week ago. I've got most things up and running pretty quick, compared to the meaningless hours I spent trying to get Suse 10.1 functioning and not crashing (10.0 wouldn't even find my hard-drives). Eventually the package manager drove me mad and I decided to ditch Suse and try Ubuntu. I'm happy. Wireless is still a pain, but still I'm happy. Now I've got a question about Unreal Tournament 2004.

My processor is dual-core and in Windows I have to assign ut2004 to run on only one of the cores, otherwise I experience strange lags, even when I test it offline. This made the game run as normal. Even though this "lag" isn't as obvious on linux, I still find it a bit frustrating. The lag typically shows itself as mouseclicks not getting registred or latency when clicking the mouse. But, as mentioned before, on linux it is not that dominating.

My question is: How do I, if possible, assign ut2004 to run on only one of the cores? You're also welcome to tell me if I'm just being paranoid and there's no need for this in linux. I haven't had any luck finding articles about it, and I only stumbled upon the Win-solution by accident.

I have the 2.6.15-26-686 smp kernel (from Synaptics) and I do believe my graphics card is set up properly, as I'm able to run the game at "wicked sick"-settings with decend fps. Furthermore, and I'm not too proud admitting this, but, my processor is an Intel Pentium D 820 (I think, it's 2.8 GHz).

Great forum by the way. I found all instructions to get my system running in here...

---

### Post by Eazy© on 2006-08-16
You are not being paranoid. I have the same issue, but have a AMD Athlon x2 4400+ cpu. When using the smp kernel or and k7-kernel I get strange lags, mouse lags and at the same time mouse accelerations. I have tried most things I can think of, like kompiling different kernels (with and without performance kernels) and different settings in the ini-files. I even bought new hardware (to the cpu I got now). You can read about my trobles here: [http://www.ubuntuforums.org/showthread.php?t=136630](http://www.ubuntuforums.org/showthread.php?t=136630)

The only soluton for me was to use the 386-kernel that orginal comes with Ubuntu to get UT2004 run ok. When using this kernel, I feel I'm just using half of my cpu, so if you find a solution maybe I will find mine. I am to adiccted to UT2004 and Ubuntu so until I find whats wrong, I have to stick with the 386-kernel.

---

