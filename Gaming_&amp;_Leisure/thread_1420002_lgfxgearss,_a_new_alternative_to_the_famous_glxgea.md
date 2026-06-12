---
title: "lgfxgearss, a new alternative to the famous glxgears demo"
date: 2010-03-02
forum: Gaming &amp; Leisure
---

### Post by Geri_lgfx on 2010-03-02
Most linux users should know glxgears. It is a classical old benchmark program, but is not a realy benchmark, becouse it using old graphics pipeline, and deprecated features. But here is the new alternative, the **lgfxgears**.

[IMG]http://legend.uw.hu/projects/stuffingz/lgfxgears.jpg[/IMG]

lgfxgears looks cool, runs fast, and speed depends on the power of graphics card and drivers.
Currently win32 and linux are supported.

download: 
**[http://legend.uw.hu/lgfxgears.zip](http://legend.uw.hu/lgfxgears.zip)**
**[ftp://lgfx.no-ip.org/lgfxgears.zip](ftp://lgfx.no-ip.org/lgfxgears.zip)**

So, i think it would be cool if ppls would copypaste they fps here.

i start:

ATi Technologies inc.
[B]Radeon 9800 PRO
55 fps[/B]

---

### Post by Melcar on 2010-03-02
Radeon Xpress 200M:

UMS: 1fps
KMS: 10fps

Well, that's one thing where KMS is clearly better ;), though with it on I don't get any graphical output for the benchmark.

Edit: Running it with WINE yields 18fps :lol:.

---

### Post by hikaricore on 2010-03-02
I'm still a fan of glxdragon personally.
Will have to post my results later as I'm not on my home system.

---

### Post by Geri_lgfx on 2010-03-02
btw i just mistyped the program name, i hope a moderator will correct it.

here is a few result:

    [CENTER]nVidia GeForce 9800+ 180 fps win[/CENTER]
            [CENTER]ATi Radeon 9800 pro 62 fps win[/CENTER]
            [CENTER]ATi Radeon 9800 pro 76 fps linux[/CENTER]
            [CENTER]nVidia GeForce FX 5200 pci 5 fps win[/CENTER]
            [CENTER]ATi Radeon HD4830 205 fps win[/CENTER]
            [CENTER]nVidia Geforce 7025 38 fps win[/CENTER]
            [CENTER]VIA S3 Chrome 9 9 fps win[/CENTER]
            [CENTER]ATi Radeon HD 4850 260 fps win[/CENTER]
            [CENTER]nVidia GeForce GO 6600 73 fps win[/CENTER]
            [CENTER]ATi Radeon HD3650 (antialias) 167 fps win[/CENTER]
            [CENTER]ATi Radeon HD2600XT 180 fps win[/CENTER]
            [CENTER]ATi Radeon HD4890 (antialias) 220 fps win[/CENTER]
            [CENTER]nVidia GeForce 7600 GT 100 fps win[/CENTER]
            [CENTER]nVidia GeForce 6150SE 29 fps win[/CENTER]

---

### Post by portets on 2010-03-02
for me it jumps between 42fps and 99fps on a consistent basis. about every one and a half seconds. geforce 9600m gs.

is it under the gpl? some people won't take it seriously if it's not. some distributions also.

---

### Post by Geri_lgfx on 2010-03-03
some new results:

              [CENTER]ATi Radeon Xpress 200M 12 fps lin
ATi Radeon Mobility 3650 110 fps win[/CENTER]

---

### Post by hikaricore on 2010-03-03
corp: NVIDIA Corporation
gpu:  GeForce 8600 GT/PCI/SSE2/3DNOW!
icd:  3.2.0 NVIDIA 195.36.08
_______________________________________
163 fps

---

### Post by Geri_lgfx on 2010-03-03
[CENTER]ATi  Rage 128  1 fps  win :biggrin: 

[/CENTER]

---

### Post by Nevon on 2010-03-03
```
corp: Tungsten Graphics, Inc
gpu:  Mesa DRI Mobile Intel® GM45 Express Chipset GEM 20090712 2009Q2 RC3 x86/MMX/SSE2
icd:  2.1 Mesa 7.6
_______________________________________
glxgears: brw_draw_upload.c:412: brw_prepare_vertices: Assertion `input->offset < input->bo->size' failed.
Aborted
```

Sweet!

And on my girlfriend's computer:
```
corp: ATI Technologies Inc.
gpu:  ATI Radeon HD 4800 Series
icd:  2.1.9016
_______________________________________
34 fps
```

---

### Post by Geri_lgfx on 2010-03-03
That 34 fps seems very slow to me on that config.

---

### Post by Nevon on 2010-03-03
> **Geri_lgfx said:**
> That 34 fps seems very slow to me on that config.

Yup. That's Linux ATi drivers for you.

---

### Post by Geri_lgfx on 2010-03-03
btw, on most computers, where i was able to use fglrx (e.g. on those computers where X was to able to start after install :D ) 3d acceleration was very fast.

---

### Post by handy on 2010-03-03
I think that the Phoronix Test Suit is the truest benchmark that we have available for Linux systems these days:

[http://www.phoronix-test-suite.com/](http://www.phoronix-test-suite.com/)

---

### Post by portets on 2010-03-03
> **handy said:**
> I think that the Phoronix Test Suit is the truest benchmark that we have available for Linux systems these days:

[http://www.phoronix-test-suite.com/](http://www.phoronix-test-suite.com/)

and PTS can now even compare image quality! by the way, can any windows benchmark programs do that? because i've never heard of any benchmarking software do that.

---

### Post by Nevon on 2010-03-03
> **Geri_lgfx said:**
> btw, on most computers, where i was able to use fglrx (e.g. on those computers where X was to able to start after install :D ) 3d acceleration was very fast.

I just installed the latest drivers from amd.com, and now the result is a bit better.

```
corp: ATI Technologies Inc.
gpu:  ATI Radeon HD 4800 Series
icd:  3.2.9252 Compatibility Profile Context
_______________________________________
67 fps
```

---

### Post by handy on 2010-03-03
I guess the biggest problem with pts is that it takes up about 2 gigs of HDD space (download).

That is the price for the best test it seems.

Here are my results, I named my test 1st.phoronix.test when I still thought it was just for me & my HDD, the name could be somewhat embarrassing to someone else I suppose. :)

[http://global.phoronix-test-suite.com/index.php?k=profile&u=anon-15774-26987-2834](http://global.phoronix-test-suite.com/index.php?k=profile&u=anon-15774-26987-2834)

Though my speeds may look low on the quake engine games, they were smokingly fast to view, with LOTS of other players & all moving very fast, without skipping a frame. Only Nexuis was sh*t.

---

### Post by Geri_lgfx on 2010-03-03
[]("http://ubuntuforums.org/member.php?u=338254")Nevon, are you using xgl/compiz/beryl on that computer?

---

### Post by nerdy_kid on 2010-03-03
hit 61 fps with the linux binary and 70 fps with wine -- ??????

---

### Post by Nevon on 2010-03-03
> **Geri_lgfx said:**
> []("http://ubuntuforums.org/member.php?u=338254")Nevon, are you using xgl/compiz/beryl on that computer?

I am using Compiz, yes.

---

### Post by Geri_lgfx on 2010-03-03
Then probably that cause the very low fps on your computer.

---

### Post by Melcar on 2010-03-03
I get 137fps on my HD4850 and fglrx.  KDE4 with desktop effects on.  It's overclocked though (750/1100).

---

### Post by Nevon on 2010-03-03
> **Geri_lgfx said:**
> Then probably that cause the very low fps on your computer.

On the same computer, but in Windows 7 (using Aero), I get this:
```
corp: ATI Technologies Inc.
gpu: ATI Radeon HD 4800 Series
icd: 3.2.92.32
----------------------------------
125 fps
```

In Ubuntu with compiz disabled, I get 128fps. So yeah, killing compiz definitely improved my fps.

---

### Post by Melcar on 2010-03-03
Does not worh with open source drivers and my HD4850; falls back to software rendering.  Also, is there a reason the program runs slightly faster with WINE?  With my HD4850 and fglrx I get 148fps.  My 200M using the radeon driver also gets a higher frame rate.

---

### Post by Geri_lgfx on 2010-03-03
Are you using a 64-bit or a 32-bit kernel?

---

### Post by handy on 2010-03-03
> **Melcar said:**
> Does not worh with open source drivers and my HD4850; falls back to software rendering.  Also, is there a reason the program runs slightly faster with WINE?  With my HD4850 and fglrx I get 148fps.  My 200M using the radeon driver also gets a higher frame rate.

Hang in there for the OSS drivers, they are working fine on more recent versions of the kernel, mesa et al than Ubuntu is using.

Really good 2D/3D performance & power management will be yours in Ubuntu, in stable packages this year, for your R700 GPU.

---

### Post by Melcar on 2010-03-03
64bit.  
Not worried about the open source drivers.  Lots of changes being done with Mesa that are causing more performance regression on r6/7xx hardware, so it's no surprise it doesn't work that well.

---

### Post by Geri_lgfx on 2010-03-03
Melcar: well, the binary is a 32 bit one, so may this is why ,,native'' version isnt faster than wine. But i cant yet tell this for sure. I not yet has a 64 bit machine to test it.

---

### Post by dearingj on 2010-03-03
I'm running this on a Macbook Pro 5,3 with the 64-bit version of Ubuntu Karmic.

My results using the native Linux binary:
> corp: NVIDIA Corporation
gpu:  GeForce 9600M GT/PCI/SSE2
icd:  3.0.0 NVIDIA 185.18.36
_______________________________________
198 fps

My results running with Wine (wine1.2 just installed from Ubuntu's repositories, version 1.1.39~0ubuntu1~karmic5):
> corp: NVIDIA Corporation
gpu:  GeForce 9600M GT/PCI/SSE2
icd:  3.0.0 NVIDIA 185.18.36
_______________________________________
187 fps

---

### Post by Geri_lgfx on 2010-03-03
Well, according to Dearingj's result, the 64 bit isnt a problem. :-k

---

### Post by Bölvaður on 2010-03-03
corp: NVIDIA Corporation
gpu:  GeForce 8800 GTS/PCI/SSE2
icd:  3.0.0 NVIDIA 185.18.36
_______________________________________
249 fps



disabling compiz did not do anything much to my fps. perhaps the average fps but not the one that the test showed.

---

### Post by Melcar on 2010-03-03
> **Geri_lgfx said:**
> Well, according to Dearingj's result, the 64 bit isnt a problem. :-k

Some weird interaction with ATI drivers?  Then again, I'm experiencing similar behavior with both fglrx and radeon drivers.

Edit: With composition off I get 170fps with the linux binary and 145fps with the windows one.  Must be some strange interaction with composition.

Edit2: Laptop with 200M using radeon driver.  Compiz off I get linux/18fps and windows/18fps; Compiz on I get linux/12fps windows/20fps.

---

### Post by Geri_lgfx on 2010-03-03
Probably application should detect the running composite tools, and must temporally shut down them until the benchmark runs. But maybee this is not possible.

---

### Post by zliefer on 2010-03-03
Ran both programs but only get 8 fps :D
1. engine386.lnx
2. glxgears

I have no hardware accelerated graphics card  :)  Neat program though. :KS

---

### Post by handy on 2010-03-03
> **Melcar said:**
> 64bit.  
Not worried about the open source drivers.  Lots of changes being done with Mesa that are causing more performance regression on r6/7xx hardware, so it's no surprise it doesn't work that well.

I'm using -git packages (a couple of weeks old) & it works fine for me, though I'm obviously not changing versions often.  

I'll be staying where I am until the word is out that it is well worth while changing. ;)

Here are my results from the PST (1st.phoronix.test):

[http://global.phoronix-test-suite.com/index.php?k=profile&u=anon-15774-26987-2834](http://global.phoronix-test-suite.com/index.php?k=profile&u=anon-15774-26987-2834)

---

### Post by Geri_lgfx on 2010-03-04
[IMG]http://legend.uw.hu/adatok.jpg[/IMG]

---

### Post by Geri_lgfx on 2010-03-04
1.13 out, SSE version out.

---

### Post by ricsi-pontaz on 2010-03-08
Nice work! Great app.

Ubuntu Lucid Lynx
GeForce GTS 250 512MB
[[COLOR="Blue"]Picture[/COLOR]]("http://ricsipontaz.hogyan.org/files/2010/03/lgfxgears.png")
292 fps

---

### Post by Geri_lgfx on 2010-03-09
> **ricsi-pontaz said:**
> Nice work! Great app.

Ubuntu Lucid Lynx
GeForce GTS 250 512MB
[[COLOR=Blue]Picture[/COLOR]]("http://ricsipontaz.hogyan.org/files/2010/03/lgfxgears.png")
292 fps

Thank you Ricsi, örülök hogy tetszik.

Your result is very good for a GTS250. What CPU do you use?

---

### Post by Shazaam on 2010-03-09
Nvidia GeForce 7800GS 256 MB, agp4x, Nvidia driver 190.42.
80 fps.  :)

---

### Post by ricsi-pontaz on 2010-03-10
> **Geri_lgfx said:**
> Thank you Ricsi, örülök hogy tetszik.

Your result is very good for a GTS250. What CPU do you use?

An AMD Phenom II X3 710 2,6 GHz

---

### Post by Geri_lgfx on 2010-03-10
Ricsi: thanks

Shazaam: that seems low for me on that card. It should be run far above 80 fps. I suggest you to supervise this situation.

---

### Post by hessiess on 2010-03-11
Runs at 59 FPS on my nvidia GeForce 7600GS, Q6600 machine.

There's one problem with the application, its resolution dependent, whereas the original GLXGears is resolution independent. This application wont run full screen on my 1920*1080 monitor ;)

Is the source code available? If it is people using a 64 bit OS can compile there own 64 bit version;)

---

### Post by Geri_lgfx on 2010-03-13
hessiess: thanks for your result. the application is using fix resolution, becouse of the postprocess. To do the postprocess, a ,,power of two'' sized texture needed: like 512x512. Using non_power_of_two textures to postprocess is not supported on graphics cards below SM4 - it results fps to drop with 10-20x. Original glxgears can be resized without limitation, becouse it has no postprocess algorythms. Of course, resizing the window dinamically would be a possible solution, but that not would result the res to be highered, the final image would be just rescaled to the new window sizes, this is why this is not available.

---

### Post by Shazaam on 2010-03-17
> **Geri_lgfx said:**
> 
Shazaam: that seems low for me on that card. It should be run far above 80 fps. I suggest you to supervise this situation.


"agp4x"
That's the problem. My ancient Soyo KT600 motherboard refuses to run videocards at 8x even though it is supposedly supported. And don't worry, I have already researched the issue a long time ago. :)

---

### Post by cascade9 on 2010-03-18
129Fps, 8600 GT (190.53 driver, 64bit OS, kernel 2.6.33) with a AMD 4800+ Dualcore. 

I might have to try this on some of the other computers I have hanging around here.  

> **Shazaam said:**
> "agp4x"
That's the problem. My ancient Soyo KT600 motherboard refuses to run videocards at 8x even though it is supposedly supported. And don't worry, I have already researched the issue a long time ago. :)

From what I remember, the difference between 4x and 8x wasnt that much. No idea how much difference it would make on this test though.

---

### Post by fooman on 2010-03-18
i top out @ 210fps with my 512mb 8800gt.  using the 190.53 drivers, karmic 64bit and the 2.6.32 kernel.

---

### Post by Geri_lgfx on 2010-03-27
thanks for the results.

agp 4x should not be so huge problem for this app, it does not depends on its bandwith so much to explain this low fps.

---

### Post by natetheskate on 2010-04-14
My GTX 260 was cranking out 300+ fps on Ubuntu 10.04 64-bit Beta 2.

---

### Post by Geri_lgfx on 2010-04-15
thankyou, thats seems a good result.

---

### Post by kamatschka on 2010-04-27
My Configuration

[LIST]
[*]Ubuntu 10.04 RC 64bit
[*]Nvidia Driver 195.36.15
[*]Intel Core2Duo T7300 (2GHz)
[*]Geforce 8600m GT
[/LIST]
its running lgfxgearss with ~132fps...

---

### Post by khelben1979 on 2010-05-29
Debian Lenny with kernel 2.6.26-2
nVidia driver version 177.82
P4 2.8ghz + 1 GB of RAM
Gainward **nVidia Geforce7800GS** 256 MB GDDR 3

Result before computer froze (heat problems): max 129fps and min 114fps

---

### Post by cwwilson721 on 2010-06-01
AMD 5200+
Lucid 64-bit
```
corp: NVIDIA Corporation
gpu:  GeForce 9600 GS/PCI/SSE2
icd:  3.2.0 NVIDIA 195.36.24
_______________________________________
227 fps

```Actually, I'm fairly impressed....lol. Actually beat an 8800GT?

---

### Post by Geri_lgfx on 2010-06-15
cwwilson721: graphics performance is also sightly depends on the power of the CPU and the quality of the motherboard's chipset, depends on the used display driver too ;)

---

### Post by formaldehyde_spoon on 2010-06-16
lgfxgears is a minibenchmark, v1.13, (c)Kovacs Gergo
corp: NVIDIA Corporation
gpu:  GeForce GT 240/PCI/SSE2
icd:  3.2.0 NVIDIA 195.36.15
_______________________________________
302 fps

 10.04 64 bit

---

### Post by Geri_lgfx on 2010-06-16
corp: Intel
gpu: Intel Bear Lake B
10 fps
winxp



corp: nVidia
gpu: nVidia GeForce Ti4200
45 fps
winxp (with a VIA ezra 800 mhz cpu)

---

### Post by fooman on 2011-02-20
core 17 950
12gb ram
gtx480

---

