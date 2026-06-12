---
title: "Couple of questions regarding glxgears and xorg.conf"
date: 2009-01-26
forum: General Help
---

### Post by empty_spaces on 2009-01-26
Until yesterday I was getting around 560 FPS using glxgears and 2GB ram. Today I upgraded my ram from 2GB to 4GB. Now I get around 350 FPS. Anyone know what might be happening here?

After seeing this, I went to look at my /etc/X11/xorg.conf file, but it's empty. So how are displays being managed in Intrepid?

**Here is my System Info:**
Laptop: Toshiba Satellite A205-S5855
Specs: 1.83 Ghz Core 2 Duo, Intel X3100.
OS: Ubuntu 8.10 Intrepid 64 BIT


RAM seems to be fine. All 4GB is being detected in the system monitor.

Attached is a file (Commands.txt) containing the output of all the following commands in that order:
1) cat /proc/meminfo
2) sudo lshw -C memory
3) glxinfo
4) glxinfo | grep direct
5) glxinfo | grep vendor
6) lspci | grep VGA

Thanks.

---

### Post by empty_spaces on 2009-01-26
**Update:**

I ran the laptop with the new 2GB stick of ram and removed the old 2GB stick - my FPS went back up to 560 fps.
So each 2GB stick by itself gives me 560 fps, but when i put in both for a total of 4GB, my fps drops to 350 fps.

Are there some steps/process that I'm missing that helps Ubuntu to utilize the 4GB better?

Thanks

---

### Post by empty_spaces on 2009-01-27
Bump.

On further research, it appears that the Intrepid display is more sluggish compared to Hardy and Gutsy, at least for the Intel X3100 card.
But I would still be interested in knowing why the ram increase should affect the FPS.

---

### Post by mb_webguy on 2009-01-28
GLXGears shouldn't be used as a [benchmark]("http://wiki.cchtml.com/index.php/Glxgears_is_not_a_Benchmark").  Actually, I believe you used to have to type "glxgears -iacknowledgethatthistoolisnotabenchmark" in order to display the framerate...

---

### Post by fragos on 2009-01-28
The glxgears frame rate changes when you change anything. Boosting the size of the glxgears window lowers the frame rate. Other applications running at the same time also lower the frame rate reported by glxgears. The implication is that by adding more memory the operating system needs more CPU cycles. Linux will allocate buffer space in all available memory -- more resources to manage. Does this impact the glxgears reported frame rate? The real question is, what does that frame rate really mean. Did you really loose 38% of your true system performance by adding memory -- I doubt it.

---

### Post by empty_spaces on 2009-01-28
Thanks for the explanation.

I have noticed that the figures reported by glxgears do vary depending on other applications that may be running. And I have read a lot about why glxgears should not be considered a benchmark, and I agree.

The reason I started experimenting with the glxgears command was that ever since I moved to **Intrepid 64bit** from **Hardy 32bit**, I could tell that everything was a lot slower in **Intrepid** compared to **Hardy**. The compiz cube was stuttering, vlc video would tear up slightly, etc, etc. 
And the figures provided by glxgears seemed to support my observations. **So if not a benchmark,** **glxgears can at the very least, be an indicator of possible issues** if run in a controlled environment.

Anyway, as of yesterday, I have wiped out **Intrepid 64bit** and installed **Hardy 64bit**. **Everything runs very smooth now**. Cube is smooth and vlc is crystal clear. Fyi, **350 fps with Intrepid(64)** has now changed to **1143 fps with Hardy(64)** using glxgears and no other apps running.

**_Just as a fun experiment_**, I ran the LiveCDs of the following Ubuntu versions and took screenshots of the glxgears output.

**In a nutshell, here are my results:** (Jaunty is still alpha, so maybe it will get better, but I'm not very optimistic)

**OS Version ---------------- Max FPS Reading**

[B]Gutsy 7.10    (32bit) ---------- 1147 FPS
Hardy 8.04.1  (32bit) -------- 1143 FPS
Hardy 8.04.2  (64bit) -------- 1143 FPS
Intrepid 8.10 (64bit) -------- 356 FPS
Jaunty 9.04a  (64bit) -------- 188 FPS[/B]

**Again, I understand that glxgears is not a benchmark, and I'm only using the numbers for comparison between the different versions, but it seems to be a good indicator of "sluggishness"**

It kinda makes me think I'll be sticking with Hardy for a while.

We'll see.

---

### Post by sdowney717 on 2009-01-28
scott@scott-desktop:~$ glxgears
13073 frames in 5.0 seconds = 2614.115 FPS
12806 frames in 5.0 seconds = 2561.122 FPS
13122 frames in 5.0 seconds = 2624.341 FPS
12853 frames in 5.0 seconds = 2570.561 FPS
13286 frames in 5.0 seconds = 2657.087 FPS
13017 frames in 5.0 seconds = 2603.376 FPS
12650 frames in 5.0 seconds = 2529.994 FPS


I get this with 1gb mem 2.4ghz single core X1300 ati card
running Intrepid 32bit

---

### Post by empty_spaces on 2009-01-28
Those are pretty good readings on the X1300 ati. Of course, our ram is different (1gb vs 4gb) which may or may not have a bearing on the readings, as mentioned in Fragos's post.

It looks like the drivers for my Intel X3100 graphics card are becoming progressively worse with each release.

---

### Post by fragos on 2009-01-28
I just ran glxgears on my Dell 1420n which has an X3100 video chip and found that the reported fps is a little less than halh of what I remember. I ran it on my desktop with an FX5200 and found my fps had degaded about 10% where the X3100 lost 50%. At one time they were virtualy identical. The hardware configuration of both has stayed the same. Only Ubuntu has been upgraded. When I purchased the laptop they were both on 7.04 and now both run 8.10.

---

### Post by sdowney717 on 2009-01-31
the driver right before the latest
scott@scott-desktop:~$ glxgears
13073 frames in 5.0 seconds = 2614.115 FPS
12806 frames in 5.0 seconds = 2561.122 FPS
13122 frames in 5.0 seconds = 2624.341 FPS
12853 frames in 5.0 seconds = 2570.561 FPS
13286 frames in 5.0 seconds = 2657.087 FPS
13017 frames in 5.0 seconds = 2603.376 FPS
12650 frames in 5.0 seconds = 2529.994 FPS

updated to latest driver 9.1
scott@scott-desktop:~$ glxgears
17470 frames in 5.0 seconds = 3488.695 FPS
17926 frames in 5.0 seconds = 3585.181 FPS
17567 frames in 5.0 seconds = 3513.341 FPS
17480 frames in 5.0 seconds = 3495.912 FPS
16527 frames in 5.0 seconds = 3303.349 FPS
16233 frames in 5.0 seconds = 3246.584 FPS
18159 frames in 5.0 seconds = 3631.671 FPS
17784 frames in 5.0 seconds = 3556.788 FPS
18189 frames in 5.0 seconds = 3637.616 FPS

pretty good increase

---

### Post by fragos on 2009-01-31
Last update had a major effect on my X3100 video laptop almost double. A small increase was also seen with my FX5200 video desktop. Just curious, sdowney717, what video hardware do you have?

---

### Post by crjackson on 2009-01-31
> **fragos said:**
> Last update had a major effect on my X3100 video laptop almost double. A small increase was also seen with my FX5200 video desktop. Just curious, sdowney717, what video hardware do you have?

Okay,I just purchased a new HP lappy today with the Intel Graphics Accelerator X3100. With compiz on I get 179 FPS, with compiz off I get 339 FPS.


Are we talking about the same video card? If so, where can I get this driver that nearly doubles the FPS?  Intrepid is really sluggish on the lappy when it comes to graphics.

---

### Post by fragos on 2009-01-31
My Dell 1420n Ubuntu 8.10 with Intel Core Duo T5250 @ 1.5Ghz, X3100 and 1GB memory runs glxgears at 580fps with Compiz on and 650fps without. Clearly the CPU has an impact on the test results. I've disabled the servers I don't need or want like Tracker. Note that Tracker runs in the background and may have been using CPU cycles when you ran your test. There are so many variables that is difficult to make a meaningfull comparison of different machines. Glxgears can give a picture of the trend when you make a change to your system.

---

### Post by crjackson on 2009-01-31
I have a core 2 duo with 4 GB ram. It an HP Pavilion dv6929nr.

I just booted hardy 8.04.2 Live CD and jumped to 1149 FPS. Clearly something isn't well with Intrepid. I want to run Intrepid for the better network manager and the ability to install OOo 3.0 but it's just not worth the performance trade off.

I sure hope Jaunty has better performance.

---

### Post by empty_spaces on 2009-02-01
crjackson, I completely agree with your post. It is pretty much why I started this thread. 

I have a Toshiba Core2Duo with 4gb ram and Intel X3100, and I was getting 350fps and a generally sluggish system with Intrepid64. The only reasons I had upgraded to Intrepid64 was because of the better network manager.

But the poor performance was too much of a trade-off, so now I'm running 8.04.2(64bit) which gives me 1143fps and much better graphics response overall.

---

### Post by fragos on 2009-02-01
It would appear that the 32bit Intrepid outperforms the 64bit for this driver.

---

### Post by crjackson on 2009-02-01
> **fragos said:**
> It would appear that the 32bit Intrepid outperforms the 64bit for this driver.

My results were based on 32bit. I can't understand how a video card this new runs so much slower than my OLD lappy with a slower processor, 1/4 the ram, and an old ATI 9600 card that's barely supported.

Can one hopefully expect to see truly accelerated performance in future versions?

---

