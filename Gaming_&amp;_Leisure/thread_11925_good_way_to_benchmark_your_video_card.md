---
title: "good way to benchmark your video card?"
date: 2005-01-20
forum: Gaming &amp; Leisure
---

### Post by jdodson on 2005-01-20
i got my nvidia card geforce 5700LE 256M the other day in my new computer.   it plays ut2004 demo totally fine.  i am wondering if anyone knows of a good way to benchmark the card to see if i am getting the desired results.... actually i have no idea what the desired results are.  program i could use, website resource?

just wondering.

---

### Post by mendicant on 2005-01-20
For a quick overview, you can run ut2004 and just check out the average frame rate in game by pressing
'~', which pulls down a console, and then type:

stat fps

And it should display on the top right.  You can also run this on various standard demos that websites use, and compare your performance to theirs.

---

### Post by jdodson on 2005-01-20
[QUOTE=mendicant]For a quick overview, you can run ut2004 and just check out the average frame rate in game by pressing
'~', which pulls down a console, and then type:

stat fps

And it should display on the top right.  You can also run this on various standard demos that websites use, and compare your performance to theirs.[/QUOTE]

thanks.

---

### Post by AndersAA on 2005-01-20
you could also run quake3/doom3 timedemo's, should be fairly simple to get something to compare it to.

---

### Post by valadil on 2005-01-20
I generally go with glxgears.  Probably not the most accurate but it tells me if something is wrong most of the time.  I get about 500fps if glx is messed up, 3000 if agpgart isn't working quite right, and 6000-7000 if all is working correctly.  This is on a GeForce5900fx btw.

---

### Post by mendicant on 2005-01-20
Also check out:

[http://www.linux-gamers.net/modules/wfsection/article.php?articleid=40](http://www.linux-gamers.net/modules/wfsection/article.php?articleid=40)

which tells you how to run the built in benchmarking from the command line.

---

### Post by Tichondrius on 2005-01-24
Another widely used benchmark is Doom 3, which allows you to record and playback a "timedemo" . You can also download pre-recorded [timedemos](http://www.techreport.com/reviews/2005q1/geforce6600gt-sli/index.x?pg=3)   (unzip/untar the demo files, and place them in your ~/.doom3/base/demos directory). To play a demo, enter the doom 3 console by pressing ctrl-shift-~, and type timedemo <demofilename> (e.g. "timedemo trhaze"). btw, to record your own demo, use the command "recorddemo <filename>" and "recorddemo" to stop recording.

btw, for doom 3 the results are somewhat lower than what you get in windows with the same hardware. Did anyone else notice that ?

---

### Post by Buffalo Soldier on 2005-01-25
[QUOTE=valadil]I generally go with glxgears.  Probably not the most accurate but it tells me if something is wrong most of the time.  I get about 500fps if glx is messed up, 3000 if agpgart isn't working quite right, and 6000-7000 if all is working correctly.  This is on a GeForce5900fx btw.[/QUOTE]Ran glxgears. Got around 2800 fps on GeForce2 GTS.

---

### Post by flygmaskin on 2005-01-29
[QUOTE=Buffalo Soldier]Ran glxgears. Got around 2800 fps on GeForce2 GTS.[/QUOTE]

Weird, I can't get over ~850fps on my geforce fx5200 (amd 2400+, 768mb ram). Any ideas on what might be wrong?

---

### Post by dhonn on 2005-02-02
[QUOTE=Tichondrius]btw, for doom 3 the results are somewhat lower than what you get in windows with the same hardware. Did anyone else notice that ?[/QUOTE]

It could be the video drivers or it could be xwindow networking behavior.  Or it could be that ubuntu's kernel has CONFIG_PREEMPT on.  Ive heard Linus say that its great for the desktop helps average response times but it lowers performance.  Normally everything is scheduled then excuted in a batch every few milliseconds.  Windows has the same behavior.

I still think it could be the xwindow and drivers.

---

### Post by AndersAA on 2005-02-02
it's neither... carmack has stated multiple times the windows client is far more optimized than the linux one.  The linux one for example does not have sse instructions at all if I remember correctly (brought up as an example).

---

### Post by dhonn on 2005-02-02
That makes sense but you can compile with -msse -msse2 with gcc and see noticeable performance improvements.  But in 3d graphics the biggest bottlenecks are video related.  It would be interesting to see how many bogoframes per seconds you would get if the rendering was turned off.

---

### Post by Tichondrius on 2005-02-02
[QUOTE=dhonn]It could be the video drivers or it could be xwindow networking behavior.  Or it could be that ubuntu's kernel has CONFIG_PREEMPT on.  Ive heard Linus say that its great for the desktop helps average response times but it lowers performance.  Normally everything is scheduled then excuted in a batch every few milliseconds.  Windows has the same behavior.

I still think it could be the xwindow and drivers.[/QUOTE]

Yeah, actually I do have CONFIG_PREEMPT=y, I guess I will try recompiling the kernel without this setting. Actually, one definite difference is that in Windows I'm running my 6800GT at overclocked speed of 400 MHz core/1100 MHz mem, but in Linux it's running at default speed of 350/1000. So that's a 10-15% difference right there.  I'm getting 104.1 fps in Linux vs 129 fps in windows using the [trdelta1](http://www.techreport.com/reviews/2004q3/geforce-6600gt/trdelta1.zip)   timedemo at 1280x1024 with high quality setting. So if I could overlcock the card in Linux, I'd probably be looking at around 115 fps, which is still 10-15% slower then Windoze ! This brings me to my next question - the nvidia-settings package doesn't work (crashes) with the 6629 driver, and anyway it doesn't have an overclocking option like the Nvidia's windows utility. Does anyone know how to overclock Nvidia cards in Linux ?

---

### Post by AndersAA on 2005-02-02
nvclock can do it, but I'm not sure it can overclock the latest cards yet.

---

### Post by darkoptix on 2005-02-02
I get like 40 fps in glxgears on my MATROX G400!

---

### Post by piedamaro on 2005-02-02
nvclock doesn't work with GeForce > 4 cards, matrox doesn't have 3d acceleration, IIRC.

---

### Post by Tichondrius on 2005-02-02
[QUOTE=darkoptix]I get like 40 fps in glxgears on my MATROX G400![/QUOTE]

I get 12800 in glxgears

---

### Post by dhonn on 2005-02-16
I've tested q3demo on Linux in window mode and q3demo on wine in window mode. I did a time demo test and found out that q3demo under wine performed frame wise better than the linux version.  Only by a couple fps.  Carmack did mention that I the linux version was not optimized, a good reason for the slightly lower fps.  However, game play under wine was not as good as it is under native linux.  In fullscreen mode the fps was much more in linux than on wine. The difference between fullscreen and window mode was around 6 fps.

I was using 800x600x16 bit for full screen and in window. 

My system:
kernel 2.6.11-rc4 with CONFIG_PREEMPT + CONFIG_PREEMPT_BKL(NEW)
1800mhz pentium4m
256mb ram, geforce2 go 16mb
demo001 = 69.0fps
demo002 = 72.0fps

During gameplay with "~/cg_drawfps 1"  it hovers around 90fps.


EDIT:
The drivers I was using is 6629. with Con Kolivas nvidia patch 2.6.11-rc4
[http://ck.kolivas.org/patches/2.6/2.6.11-rc4/NVIDIA_kernel-1.0-6629-1201042.diff](http://ck.kolivas.org/patches/2.6/2.6.11-rc4/NVIDIA_kernel-1.0-6629-1201042.diff)

nvidia driver 6111 performs poorly,  about 20 fps slower.

---

### Post by Tichondrius on 2005-02-16
that is right, if only nvidia can pull another such improvement in their next driver update.

---

### Post by rlwelch on 2005-02-16
In Doom 3 you can type "timedemo demo1" in the console and it will run a benchmark for you. Run it 3 times and take the third run for most accurate results. This is pretty useful for comparing Linux to Windows performance. 

I have Windows XP and Ubuntu installed on my Geforce 6800 system with Doom 3 on both. I ran the timedemo on 1024*768, high quality settings in both OSes, and - guess what - I got 45fps in Ubuntu compared to 39 in Windows. Solid. 8-)

---

