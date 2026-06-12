---
title: "compiz fusion slow?"
date: 2007-07-05
forum: Desktop Effects &amp; Customization
---

### Post by KubuntuKilledMe on 2007-07-05
Hi, i've used beryl a lot in the past and recently "upgraded" to compiz fusion on the same hardware, and compiz fusion feels incomparably slower. Animations where i would get fluid movement in beryl (minimize with zoom effect) are extremelly jerky in compiz fusion. This specific example (minimize with zoom) will often render a SINGLE frame before it ends. I put this example, but i notice it in almost all animations. Cube rotation does seem fluid, but that's pretty much the only one.

I understand that early optimization is not good practice, but i'd like to know if other people are experiencing the same pains or if maybe there is something wrong in my setup.

Best regards.

---

### Post by number3pencil on 2007-07-05
on my laptop,

1.86 core 2 duo
2 gig ram
geforce go 7600

Beryl runs much worse than compiz fuision.  CF is fuid where as bery is a little glitchy with speed and rendering.

---

### Post by KubuntuKilledMe on 2007-07-05
I have and AMD64 4600+ with 2 gig ram and a GF7600GS.

---

### Post by usergentoo on 2007-07-07
Ive asked about the same thing curios to know why its sluggish. Im glad to hear Im not the only one with this problem. Beryl was always fast and slick and never had any problems with speed issues. Fusion running it can take several seconds just for the animations to respond. 
AMD64x2  ati 1150 2gigs ram

---

### Post by KubuntuKilledMe on 2007-07-07
Thank you usergentoo. From my observations, all the users with this problem seem to be dual core users.

Regarding dual core, i'm already running irqbalance, which was the only way to make vmware server usable.

---

### Post by usergentoo on 2007-07-07
Now we just need a solution.

---

### Post by clayts on 2007-07-08
Hey guys,
I've got this sluggishness problem too - even the 'fade' animation is (very) jerky... but i'm not on dual core.  i've got a P4 and a GeForce 7600 GS.  As other people have reported, beryl is completely smooth.  Can't wait to see the end of this glitch :)

---

### Post by KubuntuKilledMe on 2007-07-09
Fellow Linux users, i believe i may have some more insight into the situation. My tests of animation smoothness were inconsistent across different runs, suggesting changing conditions. What changing conditions could we have? First that crossed my mind was that there could be disk activity in some of the runs and not others. But Beryl also had to live with disk activity, and it did not slowdown.

But now i've found this slashdot post: [http://linux.slashdot.org/comments.pl?sid=247219&cid=19797955](http://linux.slashdot.org/comments.pl?sid=247219&cid=19797955)

It links to a large gentoo forum discussion and a kernel bug that say disk I/O is broken on AMD64. I personally changed to compiz-fusion with the change to feisty, which might just have upgraded me past the 2.6.17 kernel which is mentioned in the discussion as the last good kernel (wrt this bug). 

The kernel discussion evolves to suggesting 2 or more different bugs at work here, because it is showing in very different hardware configurations. As such, the situation may be much more complex that i've been able to gather so far.

---

### Post by gianpa on 2007-07-13
Ok, I've got the solution for you!

The problem is that my compizconf is in italian so I don't really know what's the english name of the plugins i'm talking about, btw I'll literally translate them from italian.

Go to the compizconfig settings manager, Go to the Effects category. Find two plugins named fading windows and minimize wiondows (or something like that) and DISABLE them. Now your animations should look ok.

The REAL problem is that compiz really is SLOOOOOOWER if I just open firefox the cube framerate goes down under 30 fps :(

---

### Post by Espreon on 2007-07-13
I have used Beryl in the past (latest SVN version}. But not too long ago I switched to Comipiz-Fusion and for me it is not any slower or faster. And I have:

1 GB or RAM
ATI Radeon Mobility X1400 256 MB of Video RAM

---

### Post by KubuntuKilledMe on 2007-07-13
Oh bullshit free Beryl, how we miss ye!

---

### Post by KubuntuKilledMe on 2007-07-13
> **gianpa said:**
> 
Go to the compizconfig settings manager, Go to the Effects category. Find two plugins named fading windows and minimize wiondows (or something like that) and DISABLE them. Now your animations should look ok.

The REAL problem is that compiz really is SLOOOOOOWER if I just open firefox the cube framerate goes down under 30 fps :(

I already had these 2 plugins disabled. I'm getting daily updates on compiz and i'm pretty sure its even been going slower the last couple days. Additionally, the compiz config util has been broken for what, 3 or 4 days? Cant even change settings.

---

### Post by usergentoo on 2007-07-13
Ive disabled almost everything and its still too slow to be of any use.

---

### Post by slush1000 on 2007-07-15
My system is a Toshiba A70 with a P4 3.06Ghz and ATI Mobility9000 chipset. Beryl ran beautifully with no choppiness ever but Compiz-fusion is running at a horrible frame rate. As others have pointed out earlier, some of the animations take a second or two to activate and often end up only displaying one or two frames.

I actually have Beryl running quite smooth on a Desktop PII Celeron 300Mhz with a AGP GF5200. I wouldn't even attempt to run Compiz-fusion after seeing the poor performance on my laptop machine.

Just thought I would add that.

I switched back to Beryl on the laptop for the mean time. I'll give Compiz-fusion another go in the future.

---

### Post by marsmissionaries on 2007-07-15
Quit bitching. 

CF is in DEVELOPMENT and NOT stable, yes, it will have bugs. if you have a problem all we can say is "duh"..

---

### Post by SkiesOfAzel on 2007-07-15
Fot those of you that have nvidia cards, you ca try this :
Open Gedit , paste this
```
#!/bin/sh
__GL_YIELD="NOTHING" compiz --replace --loose-binding -c emerald &
```
and save it in your home dir as compiz.sh , then type this in the terminal :
```
chmod a+x compiz.sh
```
 Hit Alt+F2 and ```
bash compiz.sh
```
If everything works better you can set it to autostart that way :
Goto system -> preferences -> sessions and create a new session named compiz and set this command :
```
bash compiz.sh
```
Logout and relogin.

---

### Post by Dimitriid on 2007-07-15
I didn't have this problems until maybe 2 or 3 updates ago and now the repository is not working but this does fix many of my performance drops now thanks.

I

---

### Post by SkiesOfAzel on 2007-07-15
The latest builds are indeed very buggy and leak like crazy but that's life on the bleeding edge ;) . Vorian's repo also seems to have more stable packages (although they still leak most of the time) , you can find instructions [here]("http://vorian.org/?p=82")

 As for compiz fusion being slower than beryl , with a good snapshot and the right starting parameters compiz fusion is extremely fast and smooth on my pc. I would go as far as to say that it's not only smoother then beryl but it's also smoother then vista's aero and osx's quartz and i've used them both. The stable version integrated in Gutsy along with xorg 7.3  may make every other operating system's desktop look prehistoric. If you wan to see what's in store in the near future for compiz and xorg 7.3 you should check [this]("http://cdn.novell.com/cached/video/bs_07/keynotes/friday_1.OGG") out (the compiz presentation is at around the 26th minute mark) , your jaw will drop.

---

### Post by mikaelsnavy on 2007-07-15
SkiesOfAzel, I LOVE YOU!!!!!!

---

### Post by UMDGaara on 2007-07-27
Yeah that made things much better for me as well. Thanks!

---

### Post by ASPCartman on 2007-07-27
How i see every one who has this problem use xgl. To solve this u must patch xgl. Question - HOW?! I have ****.patch and original file in source. I patch it ($ patch 'orig' 'patch' ) and..... i cannot install! After hours of downloading stupid sources of dependses and compilling it - it asks me for package that i already have! Its crazy! Why it needs ***proto packages if xserver-xgl precompiled dont need it? How to solve this **** now - i dont know :confused:

---

### Post by briguy on 2007-07-29
Worked for me, SkysOfAzel.  Thanks!

---

### Post by hidden_leaf_sasuke on 2007-07-30
mine is
Pentium 2.0 mobile
512 mb of RAM
ATI X700 mobility radeon 128 mb

run like charm...and much more faster than beryl

---

### Post by kojimoto on 2007-08-02
> **SkiesOfAzel said:**
> Fot those of you that have nvidia cards, you ca try this :
Open Gedit , paste this
```
#!/bin/sh
__GL_YIELD="NOTHING" compiz --replace --loose-binding -c emerald &
```
and save it in your home dir as compiz.sh , then type this in the terminal :
```
chmod a+x compiz.sh
```
 Hit Alt+F2 and ```
bash compiz.sh
```
If everything works better you can set it to autostart that way :
Goto system -> preferences -> sessions and create a new session named compiz and set this command :
```
bash compiz.sh
```
Logout and relogin.

WTF???!!!

What the f*ck this do? I dont understand why i gain again such performance after some painfully weeks with the slowest performance since the first compiz

Nvidia 6600GT
P4 2.8 Ghz 
1Gb Ram

---

### Post by psyopper on 2007-08-02
Try disabling (unchecking) the "Fade Windows" plugin. 

I just did it and CF now feels almost as good as it did in early July!

---

### Post by Myzrael on 2007-08-13
Although I'm currently a Gentoo Linux user I do sneak around here every now and then. 
What helps for me is to enable loose binding in Compiz Fusion. I have a core2duo 1gb 1,83hgz pc and it just ran slow.....screen was jerky and with such high-end specs it shouldn't be.

The trick is the following. Right click at the fusion icon and then "Compiz Options" and enable "Loose Bindings". That will fix it most likely! :)

---

### Post by Myzrael on 2007-08-14
> **Myzrael said:**
> Although I'm currently a Gentoo Linux user I do sneak around here every now and then. 
What helps for me is to enable loose binding in Compiz Fusion. I have a core2duo 1gb 1,83hgz pc and it just ran slow.....screen was jerky and with such high-end specs it shouldn't be.

The trick is the following. Right click at the fusion icon and then "Compiz Options" and enable "Loose Bindings". That will fix it most likely! :)

Did some more testing......Loose Bindings does not fix the problem. It DOES improve performance but there is still some loading time when turning the code for example. The first seconds or 2 it will lag and after that will run fine. The only thing that really fixes it ,is to disable direct rendering. But that.....sound like pretty silly when you have a nice video card and does stop things like pixmaps from running. This really is a compiz fusion or nvidia driver problem that has to be fixed.

Some more toying around. I compilled the new kernel 2.6.22 instead of 21 and tweaked it a lot more and set some options differently. At the moment it really is ultrasmooth so I'll keep you updated since it might have something to do with a kernel option.

---

### Post by screaminj3sus on 2007-08-14
> **Myzrael said:**
> Did some more testing......Loose Bindings does not fix the problem. It DOES improve performance but there is still some loading time when turning the code for example. The first seconds or 2 it will lag and after that will run fine. The only thing that really fixes it ,is to disable direct rendering. But that.....sound like pretty silly when you have a nice video card and does stop things like pixmaps from running. This really is a compiz fusion or nvidia driver problem that has to be fixed.

Some more toying around. I compilled the new kernel 2.6.22 instead of 21 and tweaked it a lot more and set some options differently. At the moment it really is ultrasmooth so I'll keep you updated since it might have something to do with a kernel option.

same here loose binding improves performance on my 7600GS but it is still laggy, I think it may be something to do with the kernel also. Because I have tried manyu distros and nvidia drivers to no avail, but it works PERFECTLY in gutsy, which has a bleeding edge kernel.

---

### Post by Myzrael on 2007-08-15
> **screaminj3sus said:**
> same here loose binding improves performance on my 7600GS but it is still laggy, I think it may be something to do with the kernel also. Because I have tried manyu distros and nvidia drivers to no avail, but it works PERFECTLY in gutsy, which has a bleeding edge kernel.

Been testing some more lately. The new kernel DOES improve performance (and it sure as hell boots faster since I tweaked it some more) as does loose binding but the problem is still not totally fixed. It also has nothing to do with CPU usage because with direct rendering on and loose bindings on it only comsumes 3% max on the cube rotate even though the first two seconds at time can still be sluggish. It's not an Ubuntu problem or something like that because it happens on a lot of distros and I personally hear Nvidia everytime I hear about this problem. I'm quite sure something is wrong with those drivers. I'll try and find some beta drivers (if they exists) to see if that helps.

---

### Post by ekred on 2007-08-15
Anyone having difficulties with the "unofficial" release of Compiz Fusion should definitely try out the first public one ([[COLOR="DarkRed"]v0.5.2[/COLOR]](http://forum.compiz-fusion.org/showthread.php?t=3154)). I had the same problems as you guys on my Core Duo laptop. It was almost unusable and would even freeze for a couple of seconds every now and then. I just "upgraded" to 0.5.2 using [[COLOR="DarkRed"]this guide[/COLOR]](http://ubuntuforums.org/showthread.php?t=481314&highlight=compiz+fusion) and everything works like a charm. I did lose some plugins in the process tho... but most of them are still there.

Cheers!

---

### Post by screaminj3sus on 2007-08-15
> **Myzrael said:**
> Been testing some more lately. The new kernel DOES improve performance (and it sure as hell boots faster since I tweaked it some more) as does loose binding but the problem is still not totally fixed. It also has nothing to do with CPU usage because with direct rendering on and loose bindings on it only comsumes 3% max on the cube rotate even though the first two seconds at time can still be sluggish. It's not an Ubuntu problem or something like that because it happens on a lot of distros and I personally hear Nvidia everytime I hear about this problem. I'm quite sure something is wrong with those drivers. I'll try and find some beta drivers (if they exists) to see if that helps.

I've Used the nvidia 100.xx drivers in sabayon and if anything it was worse (Even with loose bindings). The strange thing is I use the same driver (9631) in feisty and gutsy yet feisty is laggy as hell whereas gutsy is not. I've also used newer drivers in PCLOS with the same problem. Same thing here very little cpu usage but it lags like hell doing certain things.More instensive things like cube ect.. go fast for me but it can hardly do the damn zoom animation without lagging it's *** off. I'm not sure what gutsy is doing different to actualy have it run smooth, I hope you can find the problem. I also notice it happens with nvidia and strangly enough everyone I've seen with this problem has a 7600GS... :( People are running compiz smoother than me with Geforce 4's.

---

### Post by Myzrael on 2007-08-16
Funny you mention that. I also have a 7600 Nvidia in the GO version (running on a laptop). I also notice that 3D performance is behind compared to WIndows XP for example. I really suspect the drivers to the problem...

---

### Post by X3n0n on 2007-09-03
I found out that another plugin causing slowdown is the "Window Previews" in "Extras" section. Since I disabled it I've seen dramatic changes in performance...

---

### Post by kojimoto on 2007-09-10
Everybody, try disabling only this plugins:

[LIST]
[*]Motion Blur
[*]Blur Windows
[*]Benchmark
[*]Reflection
[/LIST]

Without this plugins, Compiz works very fine for me with the amaranth repository

You can try it with the Fade Windows, Loose Bindings and Window Previews turned on

Only the expo plugins seems sometimes slow

Nvidia 6600 GT 128M
Driver 100.14.11

---

### Post by Mongoose.wa on 2007-09-14
> **SkiesOfAzel said:**
> Fot those of you that have nvidia cards, you ca try this :
Open Gedit , paste this
```
#!/bin/sh
__GL_YIELD="NOTHING" compiz --replace --loose-binding -c emerald &
```
and save it in your home dir as compiz.sh , then type this in the terminal :
```
chmod a+x compiz.sh
```
 Hit Alt+F2 and ```
bash compiz.sh
```
If everything works better you can set it to autostart that way :
Goto system -> preferences -> sessions and create a new session named compiz and set this command :
```
bash compiz.sh
```
Logout and relogin.

This works for me, however it disables Emerald. And when I turn Emerald back on, my animations are slow again. Is emerald the problem?

I'm running a brand new laptop (Santa Rosa T7500, 8600M GT, 2GB RAM), so I don't think it's a hardware issue. If I can run Bioshock at max settings, I'm pretty sure I can handle magic lamp minimization animations...


EDIT: Expo is really slow too. I'm running the latest driver (100.14.11), so I don't know what the problem is.

Also, compiz-core is incessantly saying it needs to be updated. Constant update manager popups are getting annoying..

---

### Post by Sain on 2007-09-14
I've recently tried Gutsy Tribe 5, and I'm not impressed with compiz fusion performance. Beryl indeed seemed smoother in animation, while new compiz is choppy even with simplest effects.

Furthermore, I don't like the configuration tool + you have to install it yourself (for now). I really miss beryl's taskbar icon... 
Hope Compiz gets improved by the time of Gutsy's release.

BTW, my config is: P4 3.GHz, Nvidia 8600GT, 2 GB  RAM,

---

### Post by siralphred on 2007-09-18
thanks a lot SkiesOfAzel  the bash seem to have solved it

---

### Post by Mongoose.wa on 2007-09-18
Unless I'm mistaken, all SkiesOfAzel's script does is load Compiz Fusion with loose binding, and then load emerald. Compiz Fusion Icon does this too, along with adding a handy icon to your menu panel that lets you easily access CF and Emerald settings.

The package is fusion-icon.

---

### Post by siralphred on 2007-09-19
By the way a new nvidia driver just came out today  there is a lot of fixes for the 8 series... "Fixed a performance regression on GeForce 8 GPUs. Fixed stability problems with some GeForce 8 GPUs. Added support for bridgeless SLI with GeForce 8 GPUs. Fixed a RENDER acceleration bug that was causing 2D rendering corruption in Eclipse with GeForce 8 GPUs." so you guys can try that [http://www.nvidia.com/object/linux_display_ia32_100.14.19.html](http://www.nvidia.com/object/linux_display_ia32_100.14.19.html) i am going to try it and see if it solves the sluggish compiz will report later

---

### Post by Mongoose.wa on 2007-09-20
Ubuntu is still embarrassingly slow compared to WinXP with the new driver. Compiz animations are choppy (if they render at all) and switching/loading tabs in Firefox taking seconds.

I'm using Windows right now and tabs switch and load instantaneously.

---

### Post by GnarusLeo on 2007-09-20
Its still slow as hell ... even with the .19 driver ... anyone got any good twaks to improve performance?

---

### Post by siralphred on 2007-10-21
there is new NVIDIA beta driver out 2 days ago(100.14.23) and it seemed to have solved my slow compiz fusion, those with nvidia graphic card can try it out, i have GeForce 8400M [http://www.nvidia.com/object/linux_display_ia32_100.14.23.html](http://www.nvidia.com/object/linux_display_ia32_100.14.23.html) GT

---

### Post by bluenova on 2007-10-21
Mine is slow when running more than one monitor, but if I load compiz with compiz --replace --only-current-screen it then works perfectly.

---

### Post by bcrom on 2007-10-22
SkiesofAzel your solution worked for me in Gutsy!  Thanks!

---

### Post by GnarusLeo on 2007-10-22
Same here ... on two monitors its slightly slower, but usable :) The new driver certanly fixes some issues ... I have a 8400m as well .. (great card btw!)

You could also try indirect rendering:

```
compiz --replace --indirect-rendering ccp
```

This works even better (everything seems to be smoother), though I'm not sure what it does/disables ... any of you know?

---

### Post by nickless on 2007-10-22
Ok let me be the idiot who asks :D Where can I find loose bindings? I guess I should work myself into Compiz Fusion a bit more...
By the way, my Compiz doesn't work too bad, but it takes nearly 40s to load the Desktop after logging in... :(
(With script everything feels a bit faster, but loading takes longer)

---

### Post by LantagoniE on 2007-10-28
hey there.  I installed Ubuntu 7.10 a few days ago and kept having lag problems with compiz-fusion.  It would work perfectly for a little while (like 15, 20 minutes) and then would start to lag terribly to the point where when i was moving windows around, it would only show 1 frame every 2 or 3 seconds.  I even stopped using compiz altogether because it was too much of a hassle.

i followed this thread today and tried disabling the fading windows option, like a few persons mentionned here, and it SEEMS to have fixed my problem.  I've been running with compiz for quite a while, now, and that lagging problem thankfully seems to be fixed.

Here's my computer config for the record

AMD64 3200+
ATI X800 256meg
1gig RAM 

Cheers y'all

---

### Post by technomagik on 2007-12-21
GPUCurrentClockFreqs decreases to GPU2DClockFreqs when no intensive 3D is taking place. When some 3D processing is required, it jumps up to GPU3DClockFreqs again, but for compiz, it sometimes lags behind a few seconds, or doesn't increase at all.

Solution:

In Terminal as root:

# while true; do nvidia-settings -q all > /dev/null; sleep 25; done

---

### Post by lviggiani on 2008-04-21
Hi, your script run perfectly, thanks.
I have improved it a little bit so that it only activates when you're not running with battery (thus saving power).
I also discovered that some other settings help a lot.
Have a look at what I posted here, if you like.

[http://ubuntu-utah.ubuntuforums.org/showthread.php?t=555844&page=6](http://ubuntu-utah.ubuntuforums.org/showthread.php?t=555844&page=6)

Ciao!

---

### Post by chyneymon on 2008-07-11
ONce again - I have no idea why this works but the tweak recommended by SkiesofAzel works!!! damn - thanks. COmpiz is smooth now. Core2Due 2.4 Ghz 8600gt. What a magic trick.

---

