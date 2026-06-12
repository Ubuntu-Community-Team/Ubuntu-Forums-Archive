---
title: "Nexuiz FPS - What do you get?"
date: 2007-03-02
forum: Gaming &amp; Leisure
---

### Post by ahaslam on 2007-03-02
Hi there,

I've recently built a new PC & still get frustrated with the frame rate in some Nexuiz maps. 
My specs are as follows:

[LIST]
[*]Intel E6300 @ 2562MHz
[/LIST]
[LIST]
[*]1G of DDR2-5400 @ 732MHz @ 4-4-4-12
[/LIST]
[LIST]
[*]Nvidia 7950GT @ 622, 751
[/LIST]


With the resolution set to 1440x900 & all settings turned on and set to maximim, Nexuiz timedemo gives me the following:
[B]
result 1909 frames 38.5338482 seconds 49.5408606 fps min/avg/max: 12.9187021/49.5408606/257.2618657[/B]

So what do you guys get? Post your specs & results (with any different settings).

To run the benchmark: start Nexuiz & open the console (`) issuing: *timedemo demos/demo1.dem* The results will be stored in: *~/.nexuiz/data/benchmark.log*

Have fun ;)

---

### Post by ahaslam on 2007-03-03
Don't be shy ;)

---

### Post by jordanmthomas on 2007-03-03
Pentium M 1.5 GHz
512 MB 
Intel i915 (128 shared memory)

I even started fluxbox to save memory....and yes my 3D acceleration works (though you wouldn't be able to tell from the benchmark)

```
1412 frames 828.7501196 seconds 1.7037705 fps
min/avg/max: 1.0000000/1.7037705/55.4261754
```
^^ on the default settings
I can hardly play enemy territory in Linux.  In Windows, I get 90 fps pretty much always in et but in Linux I get like 20.

**edit** I just played Nexuiz in Windows and I still only got ~25 fps

---

### Post by ahaslam on 2007-03-03
My previous computer had a similar spec, but with less graphics memory. It couldn't even run Nexuiz, so your score aint bad ;)

It would be interesting to here from Nvidia users who dual boot. Is it faster in Windows for you too (can't check that myself)?

Tony ;)

---

### Post by Perfect Storm on 2007-03-03
Just because it's you Anthony Anthony Haslam, I'm gonna give it a roll so you can get your FPS compare-ness :popcorn: 
(Even though I'm not much into first person shooter).

---

### Post by ahaslam on 2007-03-04
;)

---

### Post by AJB2K3 on 2007-03-04
Ive got the universal pack and noticed it looks dreadful on windows xp .
IS it any better on linux?

---

### Post by ahaslam on 2007-03-04
Not got Windows, so I don't know. All I can say is that it looks awsome with every option turned on & set to maximum @ your highest resoloution ;) 

Unfortunatly even with a 7950GT I have to turn things down on some maps :(

Let us know if you find it any better/faster or not & what you're running ;)

Tony.

---

### Post by Phenax on 2007-03-04
World lighting is what's going to kill you. It uses lighting similar to Quake 4, only Quake 4 fakes a lot of values for the sake of speed, and has professional developers working to optimize the code.

Nexuiz uses the Darkplaces engine, which is based off of Quake 1. You can play Quake 1 through Darkplaces, it's pretty funny.

[img]http://icculus.org/twilight/darkplaces/pics/dpflashye1m1_5.jpg[/img]

---

### Post by ahaslam on 2007-03-04
I've come to a compromise, turning off:

[LIST]
[*]High Dynamic Range
[/LIST]
[LIST]
[*]Real Time World Shadows
[/LIST]
[LIST]
[*]Real Time Dynamic Light Shadows.
[/LIST]
[LIST]
[*]Bloom
[/LIST]

Which has allowed me to return the graphics card back to stock settings (565/715), as it made little difference at the new levels.

Everything else is still turned on and set to maximum where there's an option. This now gives me:
> **1909 frames 23.7302239 seconds 80.4459329 fps** min/avg/max: 19.4643331/80.4459329/293.1770022

At 1440x900, which makes online fragging much easier ;)

Tony.

PS. AI, how's your benchmark coming?

---

### Post by Perfect Storm on 2007-03-04
Downloaded but not installed :)

---

### Post by ahaslam on 2007-03-10
Anyone else up for testing their system, it'll really put it through its paces ;)

While playing online, many Windows users report 500+ FPS... surely they've turned off or reduced every option :confused: 

:popcorn:

---

### Post by Perfect Storm on 2007-03-10
Here's mine atlast:

P4 2.4 Ghz 1024 mb ram (800mhz)
GF 6600 GT 256 mb

Ran nexuiz in full 1600x1200. Max graphic.




result 1909 frames 52.0335663 seconds 36.6878562 fps min/avg/max: 3.6938398/36.6878562/117.0430710

---

### Post by ahaslam on 2007-03-10
Your GF 6600 GT seems to be coping very well at maximum levels (and huge resoloution), is it overclocked?

;)

---

### Post by Perfect Storm on 2007-03-10
Nope. No tweaks whatso ever. I don't have the guts to do so LOL.

---

### Post by ahaslam on 2007-03-10
That's very impressive. 

I wonder what you'd get if you turnd off:

    * High Dynamic Range

    * Real Time World Shadows

    * Real Time Dynamic Light Shadows.

    * Bloom

Leaving everything else on max, I find this to be a good compromise ;)

---

### Post by Perfect Storm on 2007-03-10
I'll try that next time. (I'm messing with NWN and some extra modules.).

---

### Post by Perfect Storm on 2007-03-10
I was thinking.....Have you tried GL O.B.S. on your system for tests?

---

### Post by ahaslam on 2007-03-10
I'll try it out soon. I'd never heard of it before, but Googling brought up your blog ;)

NVN looks good, though maybe a little dated. Are there any new developments within the RPG genera?

Keep us informed of further benchmarking ;)

---

### Post by Perfect Storm on 2007-03-10
NWN is old (in game sense) but there's so much stuff out there, you'll never get bored.[size=1]...well I don't[/size]
Not much is happening on the RPG front for linux at the moment. I'm still dissapointed that we don't get NWN2 to linux, but I've heard it aren't such a big success (could it be because they didn't released it for linux and Mac?). Again the NWN(1) community is still going strong.


For anyone who's interested in Globs check here: [http://polarbeardk.blogspot.com/2006/11/gl-obs-gl-open-benchmark-suite-on.html](http://polarbeardk.blogspot.com/2006/11/gl-obs-gl-open-benchmark-suite-on.html)

---

### Post by ahaslam on 2007-03-17
I got some new cooling yesterday & my rig runs cool & quiet. This has allowed me to bump up a few clocks ;)

Below are timedemo results from the default settings, maximum settings & my preferred compromise respectively:

> 1909 frames 13.8402261 seconds 137.9312726 fps min/avg/max: 42.7587336/137.9312726/669.7962994
1909 frames 35.3877464 seconds 53.9452266 fps min/avg/max: 14.1304782/53.9452266/236.0247316
1909 frames 20.3245356 seconds 93.9258854 fps min/avg/max: 22.8743794/93.9258854/404.5361227

As you can see there's quite an improvement, I just wish it didn't drop below 25fps. Maybe I'll have to reach a compromise with nvidia-settings also.

Tony ;)

PS. Setting the image quality to 'performance' in nvidia-settings gets me very close to my target:
> 1909 frames 18.8270705 seconds 101.3965500 fps min/avg/max: 24.1451973/101.3965500/390.1745484

---

### Post by Faytz on 2007-03-17
> **jordanmthomas said:**
> Pentium M 1.5 GHz
512 MB 
Intel i915 (128 shared memory)

I even started fluxbox to save memory....and yes my 3D acceleration works (though you wouldn't be able to tell from the benchmark)

```
1412 frames 828.7501196 seconds 1.7037705 fps
min/avg/max: 1.0000000/1.7037705/55.4261754
```
^^ on the default settings
I can hardly play enemy territory in Linux.  In Windows, I get 90 fps pretty much always in et but in Linux I get like 20.

**edit** I just played Nexuiz in Windows and I still only got ~25 fps
how did you get 3d acceleration working?
I have a Intel Solo 1.66ghz
i945gm at 128 mb because my bios wont let me change it.
1gb of ram

---

### Post by jordanmthomas on 2007-03-17
> **Faytz said:**
> how did you get 3d acceleration working?
I have a Intel Solo 1.66ghz
i945gm at 128 mb because my bios wont let me change it.
1gb of ram

3D acceleration for my card is provided by the i810 driver.  
I'm not sure what you need for an i945 but I believe it's the same.
```
cat /etc/X11/xorg.conf | grep Driver
```
(in my xorg.conf, it's the last Driver declaration)

If you're using the i810 driver you should have acceleration.
what happens if you try to run glxgears?

**edit**  If you think it's not enabled because 
```
glxinfo | grep direct
```
returns **direct rendering:  No** you might not be right.  Mine says No as well.  I believe it has to do with using AIGLX.  
Most stuff I've read says you need direct rendering to make sure your 3D stuff is working but all mine works fine (with the exception of nexuiz) and I even run beryl with no troubles.

---

### Post by ahaslam on 2007-04-09
Increased my OC a bit, this is the result using my prefered settings mentioned previously:
> 
result 1909 frames 17.7680674 seconds 107.4399346 fps min/avg/max: 26.1158149/107.4399346/371.8917886
Target exceeded :guitar:

---

### Post by ahaslam on 2007-05-04
Damn Feisty is quick ;)

It matches the performance of Zenwalk In games, anyone got any proud benchmarks?

---

### Post by dmcdante on 2007-05-15
howdy - fun to see how an opensource game can draw your hardware down :)

stock core 2 duo conroe, 2,4ghz
2 gb of kingston 6400 4-4-4-15 ram,
stock nvidia geforce XFX 8800GTX
debian unstable 4.0 kernel 2.6.21,
newest nvidia drivers

results: 

result 1909 frames 38.6511359 seconds 49.3905277 fps min/avg/max: 15.8145526/49.3905277/307.7710596
50fps average on 1680x1050, all maxed out, text detail max, antisotropic filtering 16x

background: kde, second monitor in twinview (whole res of desktop: 2960x1050, nex windowed), firefox, superkaramba, xmms, pidgin, irssi and some other stuff...

:)

EDIT:

lol i just figured i ran a crashed ut2004-demo in the background which used all of one core XD
all the same as before but ut killed:

 result 1909 frames 37.8289759 seconds 50.4639619 fps min/avg/max: 17.4185677/50.4639619/335.8129704


greets, dante_2core

---

### Post by ahaslam on 2007-05-18
Cool rig, it should totally anhiliate mine, with twice the ram & l2 cache along with that killer vga.
I wonder what result you'd get with my preferred settings mentioned earlier in this post? They allow far greater FPS, while keeping the detail & quality ;)

Turn off:

    * High Dynamic Range

    * Bloom

    * Real Time World Shadows

    * Real Time Dynamic Light Shadows.

Setting everything else on & at max under video, effects & audio, I find this to be the best compromise ;)

---

### Post by dmcdante on 2007-05-20
hmm... good settings, truly.

result 1909 frames 20.3069251 seconds 94.0073396 fps min/avg/max: 25.1207072/94.0073396/460.4065862

really cranks up the fps, you're right. i wonder what SLI 8800-ers can do with those games, anyone being blessed with such a rig?

greets, dante

---

### Post by ahaslam on 2007-05-21
Now that looks more like it :)

I'm guessing that you've not tweaked the OpenGL settings from *nvidia-settings*? Try it on performance. I don't notice any difference in quality & it's worth a minimum of +5 to your average fps.

Nexuiz 2.3 will be out soon & it offers far greater performance (+20 fps av for me). If those Q3 maps are bogging you down (like me), there's not long to wait. I'll post some bench's between 2.2 & 2.3 when I get my new PSU later this week ;)

PS. It'd be great to hear from *any* SLI'er.

---

### Post by dmcdante on 2007-05-21
no - you're right, i got the opengl settings on "quality" in nvidia-settings, i did not think that that actually changes the performance a lot. i'd even go that far and say that my bottleneck is the cpu atm, coz it's only at 2.4ghz stock!

i'll do the other benchmark tomorrow and post the results, too!

greets

---

### Post by ahaslam on 2007-05-21
> i'd even go that far and say that my bottleneck is the cpu **atm**, coz it's only at 2.4ghz stock!

At the moment ;)

Games certainly respond nicely at 3GHz & the C2D's OC brilliantly.

I may try pushing my clocks further when I get my new psu at the end of the week, but I think my pc2-5400 ram has reached it's limit at 900MHz, watch this space. ;)

---

### Post by timzak on 2007-05-22
Well, I've only had time to run it "out of the box" with default settings at 800x600 and 1280x1024:

800x600:
```
27.7777778/103.4893801/1000.0000000
```

1280x1024:
```
10.0000000/68.6345006/200.0000000
```

Interestingly, when I set my res to 1600x1200, the in-game menu said 1600x1200 but when I checked my monitor's OSD, it still said 1280x1024.  Not sure why.  I haven't tried any other detail settings.  What would you like to see?

I'm dual-booting with Windows 2000, so if you'd like, I can try it in Win2k too and compare results.

My system:
C2D E4300 @ 2.6Ghz
1 gig DDR1 400
Geforce 6800GS AGP @ 400/1000

In Windows, I use a program called RivaTuner that lets me unlock pixel processors from 12 to 16 and vertex processors from 5 to 6, basically turning the card into a 6800 Ultra.  I'm not sure if I could do the same in Ubuntu, but right there that gives an immediate advantage to Windows in any cross-OS comparison.  I'd like to test in Windows with RivaTuner disabled for an apples-to-apples comparison.

---

### Post by ahaslam on 2007-05-22
> when I set my res to 1600x1200, the in-game menu said 1600x1200 but when I checked my monitor's OSD, it still said 1280x1024
Does your desktop display properly at that res & is there a visual difference in game when changed? If not you nay want to run nvidia-settings as root, set up your display & save to X conf.

> I'm dual-booting with Windows 2000, so if you'd like, I can try it in Win2k too and compare results.
That would be an interesting benchmark. Try it with my preferred settings at 1280x1024.

> In Windows, I use a program called RivaTuner that lets me unlock pixel processors from 12 to 16 and vertex processors from 5 to 6, basically turning the card into a 6800 Ultra
NVclock does a similar thing in Linux, it should work well with your card ;)

---

### Post by timzak on 2007-05-22
```
result 1909 frames 50.8420000 seconds 37.5476968 fps min/avg/max: 8.5470085/37.5476968/166.6666667
```

I think I did this right.  I maxed out everything as you said (including aniso filtering at 16x and texture quality at best), then turned off the 4 items you said.

This is at 1280x1024.  Haven't had a chance yet to mess with the video settings, but my monitor can display 1600x1200 quite nicely, but the icons are too small for me (19" monitor).  So I know the resolution works, just wasn't working under this game.

Will write more later...off to work.

---

### Post by timzak on 2007-05-22
Pretty fun game.  Easy to get in and out of online matches (unlike ET).  I have found the minimum framerate must occur during 1 or 2 frames because I cannot notice the pace slow down at all during the timedemo, despite minimum readings sometimes in the single digits.  Also, there were times when the minimum was worse at a lower resolution, all other settings being equal.  The average seems like a good measure to go by.

Here are a few more results on my system.  nvidia-settings is at Quality.  I turned off anisotropic filtering and dropped texture quality back to default (good).

> default-640x480
date 2007-05-22 19:10:22 | enginedate 23:49:57 Feb  7 2007 | demo demos/demo1.dem | commandline /usr/lib/games/nexuiz/nexuiz.bin -basedir /usr/share/games/nexuiz  | result 1909 frames 18.1830000 seconds 104.9881758 fps min/avg/max: 33.3333333/104.9881758/500.0000000
default-800x600
date 2007-05-22 19:11:13 | enginedate 23:49:57 Feb  7 2007 | demo demos/demo1.dem | commandline /usr/lib/games/nexuiz/nexuiz.bin -basedir /usr/share/games/nexuiz  | result 1909 frames 18.6700000 seconds 102.2495983 fps min/avg/max: 20.4081633/102.2495983/500.0000000
default-1024x768
date 2007-05-22 19:12:02 | enginedate 23:49:57 Feb  7 2007 | demo demos/demo1.dem | commandline /usr/lib/games/nexuiz/nexuiz.bin -basedir /usr/share/games/nexuiz  | result 1909 frames 21.7520000 seconds 87.7620449 fps min/avg/max: 20.0000000/87.7620449/333.3333333

And here is my preferred settings.  Basically, default, but with bloom and decals turned off:

> custom-640
date 2007-05-22 19:18:41 | enginedate 23:49:57 Feb  7 2007 | demo demos/demo1.dem | commandline /usr/lib/games/nexuiz/nexuiz.bin -basedir /usr/share/games/nexuiz  | result 1910 frames 17.1490000 seconds 111.3767567 fps min/avg/max: 20.8333333/111.3767567/500.0000000
custom-800
date 2007-05-22 19:19:59 | enginedate 23:49:57 Feb  7 2007 | demo demos/demo1.dem | commandline /usr/lib/games/nexuiz/nexuiz.bin -basedir /usr/share/games/nexuiz  | result 1909 frames 17.3350000 seconds 110.1240265 fps min/avg/max: 20.4081633/110.1240265/500.0000000
custom-1024
date 2007-05-22 19:21:09 | enginedate 23:49:57 Feb  7 2007 | demo demos/demo1.dem | commandline /usr/lib/games/nexuiz/nexuiz.bin -basedir /usr/share/games/nexuiz  | result 1909 frames 18.0700000 seconds 105.6447150 fps min/avg/max: 31.2500000/105.6447150/500.0000000
custom-1600
date 2007-05-22 19:45:25 | enginedate 23:49:57 Feb  7 2007 | demo demos/demo1.dem | commandline /usr/lib/games/nexuiz/nexuiz.bin -basedir /usr/share/games/nexuiz  | result 1910 frames 27.9820000 seconds 68.2581660 fps min/avg/max: 20.0000000/68.2581660/200.0000000

I got 1600x1200 working by changing my desktop to 1600 prior to starting the game.

---

### Post by timzak on 2007-05-24
Finally got around to testing in Windows.  Tested at 1280x1024, game defaults (decals, bloom, coronas, deluxe mapping, realtime dynamic lights, OpenGL2.0 all on, the rest off):

Windows 2000 two runs:
11.5/70.9/250 both runs (rounded to nearest tenth)

Ubuntu 7.04 two runs:
13.0/69.6/250
19.6/70.1/200

Ubuntu had a higher minimum framerate (but fluctuated more); Windows 2000 eeked out a tiny victory in average.  Basically, performance was identical between the two platforms.

---

### Post by ahaslam on 2007-05-24
Thanks for the comparison, it's nice to know :) 

Many MS fanboys have been boasting ridiculous frame rates. They're probably referring to the max fps which means very little. 

Did you have any luck with Nvclock (it's in the repo's)?

---

### Post by timzak on 2007-05-24
> **Anthony Haslam said:**
> Thanks for the comparison, it's nice to know :) 

Many MS fanboys have been boasting ridiculous frame rates. They're probably referring to the max fps which means very little. 

Did you have any luck with Nvclock (it's in the repo's)?

Haven't had a chance yet.  What's the difference between the standard, gtk and qt versions?  I have no idea which to try.  Keep in mind I'm a relative newbie, so one with a GUI would be nice.  

Thanks.

---

### Post by ahaslam on 2007-05-24
Nvclock itself is a cli utility, the gtk & qt packages are its gui frontends. You should choose what's native to your de, ie. qt=kde & gtk=gnome/xfce. Whatever your choice, it should pull in nvclock as a dep. I don't believe that it'll create a menu entry, so you'll have to start it with a command such as 'nvclock_gtk'.

---

### Post by chrisLACHCIK5084 on 2007-05-24
I have a Dell Dimension 4550 loaded with 640MB of RAM, a 2ghz processor, and a 128MB Video Card.

I'm running Ubuntu 6.10 Edgy (the best of them all!) and everytime I try to start Nexuiz I get about a few seconds into the game and it just goes black and I'm back to my desktop. I'm wanting to know how to fix this or if anyone knows how to.

---

### Post by timzak on 2007-05-24
> **Anthony Haslam said:**
> Nvclock itself is a cli utility, the gtk & qt packages are its gui frontends. You should choose what's native to your de, ie. qt=kde & gtk=gnome/xfce. Whatever your choice, it should pull in nvclock as a dep. I don't believe that it'll create a menu entry, so you'll have to start it with a command such as 'nvclock_gtk'.

Do you know how to edit the Pipelines?  It shows me my disabled pixel and vertex pipes, but won't let me enable them.  The only things that it lets me change are overclock and fan speed.  I guess I'd like a manual or howto for this program.  I'd like to be able to set fan speeds according to 2D or 3D.  Mine's locked at 53%.  In Windows I can set the speed for 2D and 3D separately.  I'm sure it can be done in Linux, I just don't know how.

Can you point me in the right direction?

Thx.

---

### Post by ahaslam on 2007-05-25
Personally I don't use Nvclock, as I have a 7 series card where these are locked & coolbits allows me to overclock. However, a quick look at the man page suggests that you'll need to enable these pipelines via the cli with something like 'nvclock -P / -V' and your parameters.

>   -P, --Punit mask
              The  Geforce6/7  are  designed in such a way that one single GPU
              can be used for creating different types of boards. For instance
              they  produce  a NV40 (6800-class) GPU and when the GPU is func-
              tioning properly they turn it into a 6800GT/Ultra or when  some-
              thing is damaged or when it can't reach high clocks they call it
              a 6800NU/LE. The same is  the  case  for  NV43  based  6200/6600
              cards.  A  6800LE  card  ships with 8 disabled pixel units and 2
              disabled vertex units. On various cards it is  possible  to  re-
              enable  those  units  and  if  it works correctly it can greatly
              improve 3D performance. The problem is that some  units  can  be
              broken  which  results  in artifacts or instability. Further not
              all GPU models can be unlocked either because  Nvidia  protected
              the  GPUs against modding or because there are no extra units to
              enable.

              Using this option you can enable extra pixel units. First  check
              using  the  -i  switch which pixel units are masked. If none are
              masked it means that none can be unlocked. For an explanation  I
              will  take  a 6800LE as an example which by default has 8 of its
              16 pixel units disabled. The -i option showed  the  mask  '1100'
              which  means  that the first and second block of pixel units are
              disabled. One block of pixel unit contains 4 pipelines  in  case
              of most boards with the exception of NV44/NV46 which use 2 pipe-
              lines for each pixel unit. To enable the first and second  pipe-
              line  use -P 1111 (binary) or i you prefer hex 0xf. NVClock will
              then try to unlock the pipelines note that even when  there  are
              masked  pipelines  some  can  be locked in hardware so that they
              can't be enabled.


>  -V, --Vunit mask
              This  option  can  be  used  to enable disabled vertex pipelines
              which can appear on Geforce6/7 cards.  For  an  introduction  to
              pipeline modding check the -P option first. The syntax and work-
              ing option is the same as the pixel unit one with the difference
              that  one bit corresponds to 1 vertex pipeline instead of multi-
              ple. Again check -i to see which vertex units are locked.  On  a
              6800LE  you  might  see  '001111' which means that the fifth and
              sixth unit are  locked.  To  enable  all  units  use  -V  111111
              (binary)  or  0x3f (hex). Note that it isn't certain that a unit
              can be enabled as on some cards units are locked.

PS. on a different note, my psu turned up... I wish I spent the money on beer... It's turned my quiet rig into a wind tunnel & offers no extra current for overclocking :(

---

### Post by timzak on 2007-05-25
> **Anthony Haslam said:**
> Personally I don't use Nvclock, as I have a 7 series card where these are locked & coolbits allows me to overclock. However, a quick look at the man page suggests that you'll need to enable these pipelines via the cli with something like 'nvclock -P / -V' and your parameters.





PS. on a different note, my psu turned up... I wish I spent the money on beer... It's turned my quiet rig into a wind tunnel & offers no extra current for overclocking :(

I'm sorry to hear that.  Are you going to keep the psu?

Thanks for the help on the pipelines.  I'll try it out as soon as I can.  I'm not a huge gamer anymore (marriage and fatherhood do that, you know), but I'd like to be able to know how to do everything I can in Windows.  I'm not crazy about having to use the cli for this (how would one set this up to automatically be done on startup?) but it'll be an educational experience.

Thanks again.

---

### Post by ahaslam on 2007-05-25
You can make a simple script including your desired settings, make it executable & add it to your autostarted applications/services.

For example, I use the following to raise the clocks:
> #!/bin/bash
nvidia-settings -a GPUOverclockingState=1 -a GPU2DClockFreqs=650,775 -a GPU3DClockFreqs=650,775

You'd just be substituting 'nvidia-settings' for 'nvclock' & specifying your desired parameters as already discussed. 

Am I going to keep the psu? Not installed, that's for sure, I've contacted the manufacturer, I'll wait to hear what they've got to say about their ultra silent, high efficiency product...

---

### Post by Sockerdrickan on 2007-05-25
1440x900
Highest texture quality
No effects

Around 30 fps often over

Integrated GeForce 6150

Damn, integrated GPUs really are evolving

Edit: Over 70 fps at small maps

---

### Post by ahaslam on 2007-05-25
Even though I've not managed to increase my clocks due to my disapointing psu, here's a comparison between Nexuiz 2.2.3 & the 2.3 RC. This is using my preferred settings mentioned earlier @ 1440x900 (my max res) under Arch 64 (worth a couple of fps).

_2.2.3:_
> date 2007-05-25 17:24:44 | enginedate 10:43:21 Jan 23 2007 | demo demos/demo1.dem | commandline ./nexuiz-linux-x86_64-glx  | result 1909 frames 17.0910890 seconds **111.6956327 fps** min/avg/max: 26.5083109/111.6956327/368.1797753
_2.3 RC:_
> 
date 2007-05-25 21:41:51 | enginedate 23:40:01 May 23 2007 | demo demos/demo1.dem | commandline ./nexuiz-linux-x86_64-glx  | result 1910 frames 14.4394379 seconds **132.2766175 fps**, one-second min/avg/max: 90 133 166

So that's 18% better performance & the frame rate is much more consistent, with less drastic slowdowns. 

To be honest I think they've taken a step back with the visual quality. It almost reminds me of playing Quake 2 with a Voodoo VGA - very smooth, but sometimes too smooth, lighting effects can hide the detail of the environment.

I'm sure that many would appreciate the extra speed & fewer slowdowns, though I'm left craving detail and enabling HDR, Bloom & realtime shadows won't help my cause. At least it should make online fragging easier & more accessible, which I guess is what this game is all about.

;)

PS. Hardware specs are  as follows:

Intel C2D E6300 @ 3.15GHz
BFG 7950GT 512 @ 650/1550MHz
Corsair 2x512 XMS2-5400 @ 900MHz C4

---

### Post by ahaslam on 2007-05-27
I thought I'd show the difference that your OpenGL settings make. The screenshots attached are named in relation to their setting, you'll notice the slight differences in quality & large differences in frame rate. For me it's an easy choice & that's the 'Performance' setting, have a look & you should see why.

---

### Post by ahaslam on 2007-06-02
Nexuiz 2.3 was released a couple of days ago, the performance/visuals should be much improved. It also has convenient quality settings, I find ultra minus bloom to offer the best visual/speed compromise (this adds real-time shadows to my previous settings, while offering a few extra fps over 2.2.3). 

Here's my bench at 1440x900 set to ***ultra -bloom***:
> result 1910 frames 16.5899138 seconds 115.1301940 fps, one-second min/avg/max: 77 116 153
PS. The timedemo can also be run with '*tdem demo1*' ;)

---

### Post by timzak on 2007-06-03
> **ahaslam said:**
> You can make a simple script including your desired settings, make it executable & add it to your autostarted applications/services.

For example, I use the following to raise the clocks:


You'd just be substituting 'nvidia-settings' for 'nvclock' & specifying your desired parameters as already discussed. 

Am I going to keep the psu? Not installed, that's for sure, I've contacted the manufacturer, I'll wait to hear what they've got to say about their ultra silent, high efficiency product...

Hi again,

Can you help me with this?  Where do you type > #!/bin/bash
nvidia-settings -a GPUOverclockingState=1 -a GPU2DClockFreqs=650,775 -a GPU3DClockFreqs=650,775?  Is that in a text file?  I think I know how to add things to autostarted apps, but do I need to do anything else to make it executable?  Or does your command do that already?  Sorry, I'm still a big noob.

I was able to enable the vertex and pixel pipelines through the command line by:  ```
nvclock -f -P 1111 -V 111111
```  Interestingly, the effects stay even if you restart X by CTRL-ALT-backspace.  So using my command, could you give me a step-by-step to autostart it with Feisty?

Thanks,
Tim

---

### Post by ahaslam on 2007-06-04
No probs, nice to see it working for you ;)

Make a new file, naming it what you wish. Paste the following & save:
```
#!/bin/bash
nvclock -f -P 1111 -V 111111
```
Open a terminal & cd to the directory where your new file is located, then issue: 
```
chmod +x *newfile*
```
Then it's just a case of adding it to your auto started apps.

Don't forget to try out Nex 2.3 & share your new results ;)

---

### Post by timzak on 2007-06-04
Thanks for your help.  I got it working.  Just one problem:

> Pipeline modding can't be used while the Nvidia driver is active (exit X and unload the kernel module).
If you don't follow these instructions there's a big chance that your computer will freeze.
When you are ready and know what you are doing enable this option using the -f switch.


This is from nvclock.  While my system doesn't freeze, I get graphical corruption on my desktop that hangs around until I restart X.  It's a little inconvenient to do a CTRL-ALT-backspace immediately after my computer boots into Feisty, every time I reboot.  Do you have any idea how to do the suggestion above and have it load while the Nvidia driver is inactive?  I'm having a heck of a time finding any information on how to use nvclock on the internet.  The websites I find (such as [http://www.linuxhardware.org/nvclock/](http://www.linuxhardware.org/nvclock/)) don't seem to have any detailed information, just very basic stuff that doesn't help me.  I've gotten more out of the program itself (from the command line) than from anywhere on the web.  

Thanks again.  I'll check out the new Nexuiz when I get a chance.

---

### Post by ahaslam on 2007-06-05
Try adding a path to your script to rc.local & remove it from your autostarted apps. This should execute the script before X is started.

If this doesn't work you may need to edit your new script to resemble something like:
```
#!/bin/bash
modprobe -r nvidia
nvclock -f -P 1111 -V 111111
modprobe nvidia
```
I've not done this myself, there's probably a much more elegant solution. Please double check the commands as X may not start if this fails.

---

### Post by ObiWan2001 on 2007-06-05
Dualcore Opteron 2,8 Ghz
2GB RAM
GF 8800 GTS
Res: 1680x1050
Nexus 2.3
All Settings at Max.

> Linux:
result 1911 frames 36.4649991 seconds 52.4064184 fps, one-second min/avg/max 25 52 87

Windows:
result 1911 frames 39.5340000 seconds 48.3381393 fps, one-second min/avg/max 24 48 83

Edit:
at 1280x1024 avg is 50 (Windows) and 55 (Linux)

Edit2:
with HDR, Bloom, Real Time World Shadows and Real Time Dynamic Light Shadows set to off its:
>  Linux:
 result 1910 frames 22.8980052 seconds 83.4133795 fps, one-second min/avg/max 53 84 116

 Windows: 
result 1910 frames 23.89520000 seconds 80.1190676 fps, one-second min/avg/max 47 81 106

(res 1680x1050)

---

### Post by ahaslam on 2007-06-05
Nice to see a 10% improvement over Windows there :)

Monster screen btw ;)

PS. It'd be interesting to see what it's like set to ultra -bloom @ 1280x1024 (should be more comparable to others settings).

---

### Post by ObiWan2001 on 2007-06-06
1280x1024 Ultra -Bloom
Linux:
1911 frames 20.0202701 seconds 95.4532577 fps, one-second min/avg/max: 62 96 133

Windows XP:
1911 frames 22.7890000 seconds 83.8562464 fps, one-second min/avg/max: 45 84 117

Windows Vista:
1911 frames 26.3230000 seconds 72.6981081 fps, one-second min/avg/max: 41 73 103

---

### Post by ahaslam on 2007-06-06
Thanks for the comparison, very reassuring. 

I hope that the near future release of OpenGL 3.0 will prevent the need for XP gamers to upgrade to Vista when next-gen games are released. If developers choose this over DX10 maybe we'd see a few more games as well (we can but hope).

PS. Do you have the 320 or 640 MB GTS (I suspect the 320)?

---

### Post by ObiWan2001 on 2007-06-06
Nope the 640, when I bought it last year the 320 wasn't even available.

I tried to Overclock it a littlebit, but nvclock doesn't work well with the 8800.

---

### Post by Sockerdrickan on 2007-06-06
I can't wait for my 640 :P

---

### Post by ahaslam on 2007-06-06
> **ObiWan2001 said:**
> Nope the 640, when I bought it last year the 320 wasn't even available.

I tried to Overclock it a littlebit, but nvclock doesn't work well with the 8800.
Nvclock isn't too good on newer cards, only SVN (semi) supports my 7950. I use Coolbits, it's a simple xorg option that enables clock frequency adjustments with nvidia-settings.

---

### Post by ObiWan2001 on 2007-06-06
> **ahaslam said:**
> Nvclock isn't too good on newer cards, only SVN (semi) supports my 7950. I use Coolbits, it's a simple xorg option that enables clock frequency adjustments with nvidia-settings.

Thanks for the hint.
It seems the 95fps are CPU limited, I got exacly the same results with an overclocked GPU.

---

### Post by Moustacha on 2007-06-12
Athlon64 3400+ 2.4GHz, 1.5GB DDR 333, 6600GT AGP
1024x768 2xAF, HDR Off, Dynamic Shadows Off
Feisty:result 1910 frames 40.7170000 seconds 46.9091534 fps, one-second min/avg/max: 27 47 64
WXP:result 1910 frames 38.2220000 seconds 49.9712208 fps, one-second min/avg/max: 30 50 67

Not sure if WXP settings are exactly the same as Feisty...

---

### Post by weblordpepe on 2007-06-13
Little :(
On my 1.6Ghz Pentium M with 9600 pro graphics card 128mb.

It umm...well with shadows off it runs great. But yeah when I turn on all the cool stuff it goes slow. Like 20fps slow.  This is with official ATi drivers.

---

### Post by greaTT on 2007-10-10
hi, i have problem when i try get more pipeline in my leadtek 6200, in windows its work fine, here i dont know how do it, i try 
this:
nvclock -f -P 1111 -V 111111
 
But the error is:
Error: Illegal mask 'f', can't enable more pixel units than your card contains ('3')!


My nvclock -i is:
-- General info --
Card:           nVidia Geforce 6200
Architecture:   NV43 A2
PCI id:         0xf3
GPU clock:      299.250 MHz
Bustype:        AGP (BR02)

-- Pipeline info --
Pixel units: 1x4 (10b)
Vertex units: 3x1 (111b)
HW masked units: None
SW masked units: pixel 00b       vertex 000b

-- Memory info --
Amount:         128 MB
Type:           128 bit DDR
Clock:          548.437 MHz

-- Sensor info --
Sensor: GPU Internal Sensor
GPU temperature: 30C

Plz help me!! :) tnx!

---

### Post by fadastic on 2007-10-11
AMD Athlon FX-57
Nvidia 7800GTX
2 gigs of Corsair XMS memory

Running at 1600x1200, AF 4x, not sure about AA, HDR on, Coronas on, yada yada:
```
 result 1909 frames 48.1720000 seconds 39.6288300 fps min/avg/max: 10.8695652/39.6288300/166.6666667
```

---

### Post by wj32 on 2007-10-14
Intel Q6600 (quad core)
Nvidia GeForce 8500GT (pretty crappy)
2 gigs of RAM

At 1680x1050, AF 16x, AA 0x, all effects except for HDR on, Particle quality 1.0:

1910 frames 87.5044195 seconds 21.8274689 fps, one-second min/avg/max: 10 22 33

---

### Post by wj32 on 2007-10-14
overclocked just a bit:

1911 frames 89.8656775 seconds 21.2650709 fps, one-second min/avg/max: 10 21 30

even worse than before!

---

### Post by ahaslam on 2007-10-29
> **wj32 said:**
> even worse than before!

Either power or bandwidth saturation. Try raising your PCI-E frequency to 110.

---

### Post by ahaslam on 2008-03-01
**2.4 is out** :)

I've ran some performance benches between this & the previous 2.3 release. Some will be very happy & others will be slightly disappointed.

I've scrapped my favorite/custom settings & gone with the presets for easier comparison. I've also clocked my poor old 7950GT to its highest benchable speed (725/1700MHz), hopefully enabling it to compete your newer GPU's. ;)


[COLOR="Navy"]1024x768, *normal *quality:[/COLOR]
[LIST]2.3: 1910 frames 9.9498260 seconds [COLOR="DarkRed"]191.9631559 fps[/COLOR][/LIST]
[LIST]2.4: 1910 frames 9.5607200 seconds [COLOR="DarkRed"]199.7757498 fps[/COLOR][/LIST]
[COLOR="Navy"]1024x768, *ultimate* quality:[/COLOR]
[LIST]2.3: 1910 frames 25.5537291 seconds [COLOR="DarkRed"]74.7444725 fps[/COLOR][/LIST]
[LIST]2.4: 1910 frames 19.8623669 seconds [COLOR="DarkRed"]96.1617519 fps[/COLOR][/LIST]
[COLOR="Navy"]1440x900, *normal* quality:[/COLOR]
[LIST]2.3: 1910 frames 10.3004189 seconds [COLOR="DarkRed"]185.4293526 fps[/COLOR][/LIST]
[LIST]2.4: 1910 frames 12.4173491 seconds [COLOR="DarkRed"]153.8170494 fps[/COLOR][/LIST]
[COLOR="Navy"]1440x900, *ultimate* quality:[/COLOR]
[LIST]2.3: 1910 frames 30.4542651 seconds [COLOR="DarkRed"]62.7169952 fps[/COLOR][/LIST]
[LIST]2.4: 1910 frames 34.6376250 seconds [COLOR="DarkRed"]55.1423489 fps[/COLOR][/LIST]

Personally I class this as a regression, very disappointing. :(

It'd be nice to see what other cards are capable of & any other comparisons would be great.


*PS. The demo can't be ran with '[I]tdem demo1*', '*timedemo demos/demo1.dem*' has to be issued, luckily they've implemented tab-complete. ;)[/I]

---

### Post by ahaslam on 2008-03-02
I think I was simply too eager to put them through their paces. 

Settings:

OpenGL Shaders: on
Vertex Buffer Objects: on
Show FPS: on
Bits/Pixel: 32
Fullscreen: on
Vertical Sync: off
Anistropic Filtering: 16x
Texture Quality: Best
Particle Quality: 1.0
Texture Compression: off
4x Multisampling: off
Decals: on
Bloom: off
HDR: off
Coronas: on
Deluxemapping: on
Offset Mapping: on
R/T lightbumpmaps: off
R/T World Lights: off
R/T World Shadows: off
R/T Dyn Lights: on
R/T Dyn Shadows: on
Reflections: off

Best of 3 runs @ 1024x768, 2.3 & 2.4 respectively:
```
date 2008-03-02 07:02:01 | enginedate 16:39:22 May 30 2007 | demo demos/demo1.dem | commandline ./nexuiz-linux-x86_64-glx  | result 1910 frames 13.5327880 seconds 141.1386918 fps, one-second min/avg/max: 95 142 185
date 2008-03-02 07:04:51 | enginedate 11:33:17 Feb 29 2008 | demo demos/demo1.dem | commandline ./nexuiz-linux-x86_64-glx  | result 1910 frames 13.6389658 seconds 140.0399430 fps, one-second fps min/avg/max: 73 156 442
```

Best of 3 runs @ 1440x900, 2.3 & 2.4 respectively:
```
date 2008-03-02 07:00:16 | enginedate 16:39:22 May 30 2007 | demo demos/demo1.dem | commandline ./nexuiz-linux-x86_64-glx  | result 1910 frames 16.4150732 seconds 116.3564720 fps, one-second min/avg/max: 70 116 151
date 2008-03-02 07:03:56 | enginedate 11:33:17 Feb 29 2008 | demo demos/demo1.dem | commandline ./nexuiz-linux-x86_64-glx  | result 1910 frames 15.5801110 seconds 122.5921944 fps, one-second fps min/avg/max: 61 135 318
```

With the settings manually set to sane levels there's little difference at 1024x768, though gains are actually noticeable at my native resolution of 1440x900. The presets must be quite different, whatever the difference may be it certainly causes slowdowns at higher resolutions. 

 :oops:

---

### Post by Melcar on 2008-03-02
There seems to be something really wrong at the high resolutions (1280x1024 and up).  Even at "normal" levels the game suffers from low frames.  What's even worse, even if the game is running at 60fps, I can notice frequent "stutters".  
Right now, with 4xAA and 16xAF forced in the driver, I'm playing at 1680x1050 with everything set to high, except for real time lights/shadows to off.  Excepting for the "stutters", most of the time the game is at 50-60fps, with the lowest being 10-18fps (with 15+ people on screen going crazy with rocket launchers).

HD2900XT with 8.2 drivers.

---

### Post by ahaslam on 2008-03-02
> **Melcar said:**
> There seems to be something really wrong at the high resolutions (1280x1024 and up).  Even at "normal" levels the game suffers from low frames.  What's even worse, even if the game is running at 60fps, I can notice frequent "stutters".  
Right now, with 4xAA and 16xAF forced in the driver, I'm playing at 1680x1050 with everything set to high, except for real time lights/shadows to off.  Excepting for the "stutters", most of the time the game is at 50-60fps, with the lowest being 10-18fps (with 15+ people on screen going crazy with rocket launchers).

HD2900XT with 8.2 drivers.

I also noticed the stuttering, even at 300fps on Aggressor. I turned off some options & enabled vsync to no avail. It only seems to occur when I have firefox open in the background. I can have OO.o, GIMP, Inkscape & Audacious all running along with Nexuiz without problems though...

PS. I can have FF open in addition to those other app's, just not by it self :-k

---

### Post by ahaslam on 2008-03-02
Time to see your benchmarks ;)

I've found the 'High' quality preset to be quite good. Even though there's something about it that doesn't like high resolutions, it certainly provides the eye-candy at reasonable frame rates.

So here's my benchmark for Nexuiz 2.4, using the 'High' quality effects preset @ 1440x900:
```
date 2008-03-02 11:14:04 | enginedate 11:33:17 Feb 29 2008 | demo demos/demo1.dem | commandline ./nexuiz-linux-x86_64-glx  | result 1910 frames 15.0072789 seconds **127.2715734 fps**, one-second fps min/avg/max: 61 140 281 (90 seconds)
```
My 7950GT was at 700/1680 for this, 725/1700 was too much for constant use ;)

---

### Post by Melcar on 2008-03-02
Here's mine with the following settings:

4xAA forced in driver

[[IMG]http://img219.imageshack.us/img219/5873/nexuiz000005ht6.th.jpg[/IMG]](http://img219.imageshack.us/my.php?image=nexuiz000005ht6.jpg)

[[IMG]http://img98.imageshack.us/img98/9855/nexuiz000006vh4.th.jpg[/IMG]](http://img98.imageshack.us/my.php?image=nexuiz000006vh4.jpg)



```
date 2008-03-02 07:26:19 | enginedate 11:33:17 Feb 29 2008 | demo demos/demo1.dem | commandline /home/principe/.nexuiz/nexuiz-linux-x86_64-glx  | result 1910 frames 78.7146931 seconds 24.2648472 fps, one-second fps min/avg/max: 19 25 38 (90 seconds)
```


Specs:

AMD X2 4000+ (Brisbane) @ 3GHz
4GB DDR2 1000
HD2900XT w/ fglrx 8.2 (common ATI, I need overclocking)
Audigy2 Value

---

### Post by ahaslam on 2008-03-02
Please use one of the preset quality settings to make it easier for comparison, disable Vsync too :p
> I need overclocking
Can they not be flashed/modded? Nothing beats a hard mod followed by a quick flash ;)

---

### Post by Melcar on 2008-03-02
> **ahaslam said:**
> ...

Can they not be flashed/modded? Nothing beats a hard mod followed by a quick flash ;)



That would entail having to dual boot into Windows for proper stability testing before flashing the BIOS with custom clocks, and honestly, I couldn't be bothered with Windows anymore.

---

### Post by ahaslam on 2008-03-02
I simply set Nexuis to ultimate quality & made a script to run the the timedemo for x# of passes. As the results are logged, you can easily see if there's been a problem. Another option is to simply play for an hour or two. ;)

PS. If you're interested:
```
#!/bin/bash
i=0
while [ $i -lt 100 ]; do
    ~/games/nexuiz/nexuiz-linux-glx.sh -benchmark demos/demo1 +forceqmenu 1;
    i=$((i + 1))
done
```
^ Try it with fewer than 100 passes tbw, that'd take me a around an hour at ultimate quality. ;)

---

### Post by ahaslam on 2008-03-24
Got a new G92 GTS ;)

1440x900 @ High:

```
date 2008-03-24 21:14:12 | enginedate 11:33:17 Feb 29 2008 | demo demos/demo1.dem | commandline ./nexuiz-linux-x86_64-glx  | result 1910 frames 11.0103931 seconds 173.4724615 fps, one-second fps min/avg/max: 87 193 536 (90 seconds)
```

:biggrin:

---

### Post by Melcar on 2008-03-24
Ultra @ 1680x1050

```
date 2008-03-24 16:30:21 | enginedate 11:33:17 Feb 29 2008 | demo demos/demo1.dem | commandline /home/principe/.nexuiz/nexuiz-linux-x86_64-glx  | result 1910 frames 32.8199739 seconds 58.1962680 fps, one-second fps min/avg/max: 29 64 172 (90 seconds)
```

Specs:
Asus M2R32-MVP
AMD X2 @ 3GHz
2x2GB DDR2 1000
HD2900XT
Audigy2 Value

---

### Post by Wobedraggled on 2008-03-24
High @ 1280x1024
```

date 2008-03-24 20:07:47 | enginedate 11:32:13 Feb 29 2008 | demo demos/demo1.dem | commandline ./nexuiz-linux-686-glx  | result 1910 frames 98.9266733 seconds 19.3072297 fps, one-second fps min/avg/max: 10 21 52 (90 seconds)
```

AMD 3000 @2Ghz
2gb ram
Nvidia 7800GS 256mb.

---

### Post by Melcar on 2008-03-25
Ultimate @ 1680x1050 (with HDR)

```
date 2008-03-24 22:25:29 | enginedate 11:33:17 Feb 29 2008 | demo demos/demo1.dem | commandline /home/principe/.nexuiz/nexuiz-linux-x86_64-glx  | result 1910 frames 48.8300691 seconds 39.1152426 fps, one-second fps min/avg/max: 21 41 70 (90 seconds)
```

Same specs as before.

---

### Post by Wobedraggled on 2008-03-25
And the laptop
1680x1050 @ high

```

date 2008-03-25 07:39:58 | enginedate 11:32:13 Feb 29 2008 | demo demos/demo1.dem | commandline ./nexuiz-linux-686-glx  | result 1910 frames 145.1001097 seconds 13.1633257 fps, one-second fps min/avg/max: 6 15 31 (90 seconds)
```

Intel T2500 @ 2Ghz
1gb ram
Ati X1600 mobile.

---

### Post by lackofcreativity on 2008-04-10
1646 frames 347.3144453 seconds 4.7392213 fps, one-second fps min/avg/max: 3 5 9 (77 seconds)

Yes, I know my amazing Ubuntu gaming rig is so much better than yours ;)  You're just jealous..... (see sig)

My settings: everything on low or off except for textures, at highest possible. Resolution is 1024x768, my monitor's max.

---

### Post by anjilslaire on 2008-04-11
Anyone else notice that Nexuiz data & music got updated in th repos, but not Nexuiz itself?

nexuiz 2.3.2
nexuiz data 2.4.1~gutsy1
nexuiz music 2.4.1~gutsy1
nexuiz server 2.3.2

Makes upgrading unplayable, as apt-get updating removes the nexuiz package.

---

### Post by dvh on 2008-04-13
I can confirm that

---

### Post by soxs on 2008-04-14
I never use .deb packages for games, its simpler to keep them on a seperate partition and compile it/unpack it yourself, so you still own it after a fresh install
And you always can donwload the latest version yourself, without the hassle of packaging and or having to wait for up-to-date .debs

---

### Post by theproc64 on 2008-05-19
Take a guess at what FPS I'm going to get with the "new" computer i'm getting soon.  I'm hoping its playable at 1280x1024 and high settings with some graphics overclocking.

3.0 Ghz pentium 4 prescott
8500GT pci e with 128bit gddr2 at 800 mhz, 450mhz core clock
512 mb ddr2

its an old dell with a new video card that i'm getting for free.

---

### Post by ahaslam on 2008-05-20
3GHz seems to be the magic number for games ;)
The graphics card? I honestly don't know, but it'll overclock with coolbits. One weak area may be the memory & with it being so cheap there's little reason not to add another 512MB. ;)

It'll certainly play well, how well? You'll have to let us know ;)

PS. A little tidbit for you:
```

nvidia-settings -a OpenGLImageSettings=3
```
;)

---

### Post by theproc64 on 2008-05-20
do you really think that nexuiz itself uses more that 512 mb of ram?  If you're running the game and you don't have much ram the os just moves the desktop code into swap.  
This seems like a stupid question but how are you guy getting the fps readings from in the terminal?

---

### Post by ahaslam on 2008-05-21
It'll actually take full advantage of a whole Gig it you have it, in addition to a little swap. The problem with swap is speed & you don't want to be slowed down intermittently while playing on-line, lag is enough to contend with.

It'll play with 512MB, but RAM's so cheap it seems silly not to get more. Not to mention multitasking, have it do something else while you're playing...

FPS readings? My 1st post tells all ;)

---

### Post by soxs on 2008-05-21
Everything pimped to ultimate 1280x1024:
date 2008-05-21 08:31:56 | enginedate 11:33:17 Feb 29 2008 | demo demos/demo1.dem | commandline ./nexuiz-linux-x86_64-glx  | result 1910 frames 61.8532350 seconds 30.8795490 fps, one-second fps min/avg/max: 15 34 98 (90 seconds)

Phenom/RadeonHD3870-OC OWNS 8)

Note: lol, I was running Amarok and Opera at the same time

---

### Post by theproc64 on 2008-05-23
Here are the results with my new computer (specs above).

> result 1910 frames 52.4851100 seconds 36.3912736 fps, one-second fps min/avg/max: 19 39 63 (90 seconds)

That's at 1280x1024 resolution and the default high settings with the nvidia opengl image quality settings at performance.  It usually get better than that while playing online though.  I'm looking into getting more ram (I'm broke right now, need some for free).  It runs a lot better than my old desktop did, (around the same fps with 800x600 and effects on low.

---

### Post by ahaslam on 2008-05-25
That's not bad, you can lower those settings a little with out detracting too much eye candy ;)

---

### Post by Cresho on 2008-05-25
result 1910 frames 43.1397201 seconds 44.2747425 fps, one-second fps min/avg/max: 26 47 80 (90 seconds)

1920x1200 resolution
EVERYTHING TURNED UP HIGH(oops, i mean Ultimate setting)! using HDR and all shadows allowable.

amd64 black edition 6400
BFG nvidia 8800gt OC
2gb ddr 800
quality on nvidia settings

---

### Post by theproc64 on 2008-05-28
I'm so jealous of you Cresho.  Although my desktop runs it great, my lappy doesn't run it so well.
> date 2008-05-28 17:46:29 | enginedate 15:47:05 May 11 2008 | demo demos/demo1.dem | commandline /home/proctopus/Desktop/Nexuiz/nexuiz-linux-686-glx  | result 1910 frames 187.8976941 seconds 10.1651061 fps, one-second fps min/avg/max: 6 11 30 (90 seconds)
This is at 1280x800 res with all effects turned as low as they go.
It has a t2300 at 1.6ghz, 1gig ram and intel 945gm graphics.
the game runs decently when there's nobody else around but as you can see, when the gameplay gets fun, it all goes to the shitter (6fps baby!!!!!).

---

### Post by doorknob60 on 2008-05-28
I don't know what I get (my motherboard broke, upgrading CPU, mobo, and vid card soon :D), but it's so slow that I can barely get out of tyhe menu, it seems like 2 fps moving the mouse in the menu lol :P Even with my nvidia 5200...oh well most other games ran fine.

---

### Post by theproc64 on 2008-05-28
If you can't get past the menu with your specs I think their might be something wrong...  My old desktop with an 1.6 Athlon XP and fx5200 could run it at 800x600 res at low quality with 40-60 fps, in fact, it was quite playable.  Also, if I oced my graphics card I could run it at 50-70 fps.

---

### Post by Cresho on 2008-05-29
I can honestly say that nexuiz runs and looks between unreal tournament 2004 and Unreal 3 in terms of looks.  I preffer playing nexuiz over unreal 2004 for some odd reason.:popcorn:  probably because of the HDR

---

### Post by theproc64 on 2008-06-20
I upgraded my ram to 1.5 gigs (still running at 400 mhz) and got > date 2008-06-05 21:53:49 | enginedate 15:47:05 May 11 2008 | demo demos/demo1.dem | commandline /home/proctopus/Desktop/Nexuiz/nexuiz-linux-686-glx  | result 1910 frames 38.5539751 seconds 49.5409357 fps, one-second fps min/avg/max: 23 55 125 (90 seconds)
Then, I upgraded to an 8600gt from my 8500gt (got it for $50.00 off of ebay) and got > date 2008-06-05 22:36:09 | enginedate 15:47:05 May 11 2008 | demo demos/demo1.dem | commandline /home/proctopus/Desktop/Nexuiz/nexuiz-linux-686-glx  | result 1910 frames 32.1766517 seconds 59.3598120 fps, one-second fps min/avg/max: 29 66 165 (90 seconds)
Then, I upgraded my 3.0 ghz p4 to a 3.4 ghz p4 and got > date 2008-06-20 18:47:11 | enginedate 15:47:05 May 11 2008 | demo demos/demo1.dem | commandline /home/proctopus/Desktop/Nexuiz/nexuiz-linux-686-glx  | result 1910 frames 29.7276892 seconds 64.2498644 fps, one-second fps min/avg/max: 32 70 168 (90 seconds)
This benchmark doesn't seem to be that correct because when I'm playing online it hardly ever drops below 100 fps.

---

### Post by jbcola on 2008-08-31
I got these results (Settings Ultimate):

Res: 1440x900 32bit

Server: Nexuiz build 04:31:17 Jun  8 2006 (progs 36282 crc)
1910 frames 37.2050000 seconds 51.3371859 fps, one-second fps min/avg/max: 22 58 153 (90 seconds)

OS: 
   Hardy 64bit
Hardware: 
   ASUS P5K/EPU / Q6700 Quad core
   4Gb 2chan. DDR-1066
   Saphire HD 4870 DDR-5 512 Mb

---

### Post by eragon100 on 2008-08-31
I have upgraded my video card from a geforce 7 7500 le with only 64 mb memory (rest was shared) to a 512 mb dedicated memory geforce 8 8600 GT,
and I have upgraded from 1 to 3 GB RAM. With everything in low at 800 x 600, I first had:

date 2008-08-29 10:42:57 | enginedate 21:39:39 Jun 15 2008 | demo demos/demo1.dem | commandline /usr/games/nexuiz  | result 1910 frames 44.1030000 seconds 43.3077115 fps, one-second fps min/avg/max: 29 45 75 (90 seconds)

And now:

date 2008-08-29 13:54:24 | enginedate 21:39:39 Jun 15 2008 | demo demos/demo1.dem | commandline /usr/games/nexuiz  | result 1910 frames 20.0960000 seconds 95.0437898 fps, one-second fps min/avg/max: 55 102 210 (90 seconds)

I can run it at 1280 x 1024 with all the effects on maximum and bloom and hdr enabled. I only have to set reflections to good, and have to turn dynamic lightning off, all other things are maxed out, and I get between 30 and 60 fps consistently :popcorn:

---

### Post by eragon100 on 2008-08-31
Alright, I have replaced ubuntu with vista ultimate. On the low settings, in the first demo, I now get an average fps of 128 instead of 102 (on ubuntu it's 102). Same hardware :KS

The whole system runs and responds 4 to 5 times faster BTW. Literally. nd it's just as stable I am giving this vista installation 30 days to prove there are no major problems. If I haven't run into a single one by then, I will (offcourse) keep it. I am a bit doubtful about that however, let's see! :lolflag:

---

### Post by BigBananaMan on 2009-02-10
With an AMD phenom 9850, two Nvidia 8800GT in SLI,4GB RAM, and everything at highest settings will give me around 40fps and at lowest settings around 47fps stable but with a bad jitter so I can't even kill the bots.  Always a horrible jitter/shaking and my footsteps sound like popping sounds.  I could have sworn it ran perfectly before with the framerate in the hundreds.:confused:  The only change I've made is to turn off 4x multisampling because it just started flickering today until I turned multisampling off.  This game has serious problems.

---

### Post by Bios Element on 2009-02-11
> **BigBananaMan said:**
> With an AMD phenom 9850, two Nvidia 8800GT in SLI,4GB RAM, and everything at highest settings will give me around 40fps and at lowest settings around 47fps stable but with a bad jitter so I can't even kill the bots.  Always a horrible jitter/shaking and my footsteps sound like popping sounds.  I could have sworn it ran perfectly before with the framerate in the hundreds.:confused:  The only change I've made is to turn off 4x multisampling because it just started flickering today until I turned multisampling off.  This game has serious problems.

No, Your setup has serious problems. Nexuiz is perfectly fine. Do you have the latest drivers and such for NVidia?

---

### Post by t4thfavor on 2009-04-03
date 2009-04-03 17:08:43 | enginedate 10:01:33 May 11 2008 | demo demos/demo1.dem | commandline C:\Nexuiz\nexuiz.exe  | result 1910 frames 16.4890000 seconds 115.8347990 fps, one-second fps min/avg/max: 60 125 284 (90 seconds)
date 2009-04-03 17:10:59 | enginedate 10:01:33 May 11 2008 | demo demos/demo1.dem | commandline C:\Nexuiz\nexuiz.exe  | result 1910 frames 15.4030000 seconds 124.0018178 fps, one-second fps min/avg/max: 66 137 408 (90 seconds)
date 2009-04-03 17:11:20 | enginedate 10:01:33 May 11 2008 | demo demos/demo1.dem | commandline C:\Nexuiz\nexuiz.exe  | result 1910 frames 15.5040000 seconds 123.1940144 fps, one-second fps min/avg/max: 65 136 412 (90 seconds)


With SLI enabled 9600GT's


W/O SLI

date 2009-04-03 17:08:43 | enginedate 10:01:33 May 11 2008 | demo demos/demo1.dem | commandline C:\Nexuiz\nexuiz.exe  | result 1910 frames 16.4890000 seconds 115.8347990 fps, one-second fps min/avg/max: 60 125 284 (90 seconds)
date 2009-04-03 17:10:59 | enginedate 10:01:33 May 11 2008 | demo demos/demo1.dem | commandline C:\Nexuiz\nexuiz.exe  | result 1910 frames 15.4030000 seconds 124.0018178 fps, one-second fps min/avg/max: 66 137 408 (90 seconds)
date 2009-04-03 17:11:20 | enginedate 10:01:33 May 11 2008 | demo demos/demo1.dem | commandline C:\Nexuiz\nexuiz.exe  | result 1910 frames 15.5040000 seconds 123.1940144 fps, one-second fps min/avg/max: 65 136 412 (90 seconds)
date 2009-04-03 17:14:23 | enginedate 10:01:33 May 11 2008 | demo demos/demo1.dem | commandline C:\Nexuiz\nexuiz.exe  | result 1910 frames 17.2690000 seconds 110.6028143 fps, one-second fps min/avg/max: 60 121 311 (90 seconds)
date 2009-04-03 17:15:13 | enginedate 10:01:33 May 11 2008 | demo demos/demo1.dem | commandline C:\Nexuiz\nexuiz.exe  | result 1910 frames 16.2030000 seconds 117.8794050 fps, one-second fps min/avg/max: 63 133 420 (90 seconds)
date 2009-04-03 17:16:21 | enginedate 10:01:33 May 11 2008 | demo demos/demo1.dem | commandline C:\Nexuiz\nexuiz.exe  | result 1910 frames 16.1110000 seconds 118.5525417 fps, one-second fps min/avg/max: 64 133 426 (90 seconds)


I guess SLI isn't as good as its supposed to be (at least on this game). I should also note that level 4 on the single player crashes the game while in SLI mode.

Guess I shoulda saved my money on the second card, or buy a third :)

EDIT:
Everything on stock settings :( 

I set them to ultimate, and got around 60fps @1280x1024 w/0 sli
AND 33FPS with SLI Guess I won't using that anymore for nex!!

---

### Post by cruiseoveride on 2009-11-13
2.3Ghz Phenom X3
512mb HD4870 
Ubuntu 9.10 X86_64
Open source radeon driver.

15fps @ 1280x1024, max detail.

---

