---
title: "Catalyst 14.12 for Linux"
date: 2014-12-09
forum: Gaming &amp; Leisure
---

### Post by DanglingPointer on 2014-12-09
Gonna Phoronix bench this on the weekend!  Hopefully I'm not disappointed!

AMD now has Ubuntu specific page!...
[http://support.amd.com/en-us/download/desktop?os=Ubuntu%20x86%2064](http://support.amd.com/en-us/download/desktop?os=Ubuntu%20x86%2064)

This is generic Linux...
[URL="http://support.amd.com/en-us/download/desktop?os=Linux%20x86_64"]http://support.amd.com/en-us/download/desktop?os=Linux%20x86_64


[/URL]

---

### Post by oldrocker99 on 2014-12-09
Good. Grief. ATI is actually acting as though Linux users are important, and apparently the vicious criticism (some deserved) has actually penetrated, not to mention all the "buy nVidia, not ATI" statements on a plethora of Linux forums, gaming or not. It should be mentioned that the FOSS radeon drivers were developed with help from ATI, and they're pretty damn good these days, especially after five years.

Good for ATI. I'm going to stick with nVidia, though.

---

### Post by R33D3M33R on 2014-12-09
The description of the generic installer is wrong, the version of Xorg supported is actually Xorg/Xserver 7.4 and above (up to 1.16). The driver works on Kubuntu 14.10.

[**[COLOR=#000000]oldrocker99[/COLOR]**]("http://ubuntuforums.org/member.php?u=565288"): Yeah, nVidia Linux drivers might be good, but the company is really OSS unfriendly (PhysX, GSync, etd.), disturbingly greedy (TitanZ for $3000 or Titan for $1000 is an absurd price) and unethical (GameWorks cripple competitor performance). Because these reasons and the fact that AMD is lightyears in front of nVidia when it comes to OSS support, I'm staying with AMD  :).

---

### Post by oldrocker99 on 2014-12-09
> **R33D3M33R said:**
> 
[**[COLOR=#000000]oldrocker99[/COLOR]**]("http://ubuntuforums.org/member.php?u=565288"): Yeah, nVidia Linux drivers might be good, but the company is really OSS unfriendly (PhysX, GSync, etd.), disturbingly greedy (TitanZ for $3000 or Titan for $1000 is an absurd price) and unethical (GameWorks cripple competitor performance). Because these reasons and the fact that AMD is lightyears in front of nVidia when it comes to OSS support, I'm staying with AMD  :).

I agree that the high-end nVidia cards are ridiculously expensive, but I have a GeForce 750ti, which uses half the power, and doesn't need a separate power input like my old 650ti did, and is twice as fast. Besides, it cost ~$140, and is more than sufficient for my needs. I also (PhysX notwithstanding) am happy with nVidia's Linux support. I'm a gamer, and, while I'm not a FPS fanatic, I am able to play everything I want, including Borderlands 2 and Metro:Last Light, and Trine 2 (which is one resource-hungry program that will really put a graphics card through its paces). That is, IMHO, a real bargain.

---

### Post by DanglingPointer on 2014-12-10
Well I couldn't get the deb packages provided on the website to work, but I believe that's due to my tinkering too much around in ubuntu.  But I used the automatic install of the generic one and it worked!  Geez!  It is even much much more simpler now that we can use the built in automatic installer and it all just works!  Unbelievable!  I no longer have to go through the rigmaroll of following everything here... [http://askubuntu.com/questions/124292/what-is-the-correct-way-to-install-proprietary-ati-catalyst-video-drivers-fglrx/126513#126513](http://askubuntu.com/questions/124292/what-is-the-correct-way-to-install-proprietary-ati-catalyst-video-drivers-fglrx/126513#126513)
All I have to do is double click on the installer and choose "run" just like in M$ Windows, apply sudo password, choose automatic and Bob's your uncle!  It works!

I ran Phoronix valley and unigine suite (no valley).  The unigine suite has a large improvement, while the more modern valley only increased 2 FPS.  I have uploaded the new results.  The old ones should be at the website but I'm not sure at the moment how to search for it.  It may need a paid subscription.  
The new ones...
[http://openbenchmarking.org/result/1412090-SO-UNIGINESU36](http://openbenchmarking.org/result/1412090-SO-UNIGINESU36)
[http://openbenchmarking.org/result/1412096-SO-UNIGINEVA76](http://openbenchmarking.org/result/1412096-SO-UNIGINEVA76)

In a nutshell though...
suite results:
[TABLE="class: grid, width: 500, align: left"]
[TR]
[TD]FGLRX Driver version[/TD]
[TD]14.09[/TD]
[TD]14.12[/TD]
[TD]14.12 with 
lastest Kernel
HWE[/TD]
[/TR]
[TR]
[TD]Tropics[/TD]
[TD]97.52 FPS[/TD]
[TD]101.02 FPS[/TD]
[TD]159.12[/TD]
[/TR]
[TR]
[TD]Sanctuary[/TD]
[TD]95.78 FPS[/TD]
[TD]101.38 FPS[/TD]
[TD]167.96[/TD]
[/TR]
[TR]
[TD]Heaven[/TD]
[TD]40.98 FPS[/TD]
[TD]45.34 FPS[/TD]
[TD]67.77[/TD]
[/TR]
[TR]
[TD]Valley[/TD]
[TD]49.77 FPS[/TD]
[TD]52.65 FPS[/TD]
[TD]57.54[/TD]
[/TR]
[/TABLE]

Would have been awesome if there was some sort of scripted benchmark for The Witcher 2, perhaps the Dragon sequence on the first Act.  In my humble opinion, The Witcher 2 still has by far the best graphics fidelity of all the games released for Linux.  And all glitches have been fixed, so nay sayers should really try it out again before responding that it is broken!  Because I'm on Act 3 now with near Uber settings (Custom High) with an R9-290X and it has worked flawlessly without breaking a sweat!  

On a separate note, Empire Total War is now out... got so many games to play and not enough time in my life!  grrr

UPDATE: Added a new column for benchmark results with the latest ubuntu official hardware enablement stack for 12.04.5.  MASSIVE improvement! Benchmark published... [http://openbenchmarking.org/result/1412127-SO-UNIGINESU12](http://openbenchmarking.org/result/1412127-SO-UNIGINESU12)

---

### Post by dannyboy79 on 2014-12-10
i'm really wanting to test these drivers out on my system which has an A8 Series APU but I can't figure out how to install them. I try to download the *.deb and it fails right away saying i have a dependency issue because it can't find fglrx-core. I'm very weary about using the .run in fear that it will mess up my system. Why did AMD go thru the trouble of making 14.04 .deb packages if they don't even work. LOL  Right now i'm just using the default radeon driver by default. I'd love to do some benchmarks for my youtube channel and even create a video showing how to get these damn things installed.

---

### Post by DanglingPointer on 2014-12-10
I ran the installer on automatic and it just worked mate!  benchmarks up above.

If this is for a test for your channel and if you have another spare drive lying around, just quickly fire up an ubuntu or clone your existing one to the spare and run the automatic installer.  On my system it just worked effortlessly.

---

### Post by R33D3M33R on 2014-12-10
[**[COLOR=#000000]dannyboy79[/COLOR]**]("http://ubuntuforums.org/member.php?u=108777"): just run the .run installer and it will provide you a way to create custom *.deb packages. Then install them with sudo dpkg -i *.deb. If dependency errors come up, just run ```
sudo apt-get install -f
``` Don't forget about ```
sudo amdconfig --initial
```

---

### Post by DanglingPointer on 2014-12-12
I just updated the table above post #5.

I updated ubuntu 12.04.5 to the latest official hardware enablement stack then reinstalled FGLRX using the automatic installer and voila!  MASSIVE improvement!

Well back to the Witcher 2 for me!  :D

---

### Post by dannyboy79 on 2014-12-12
> **DanglingPointer said:**
> I just updated the table above post #5.

I updated ubuntu 12.04.5 to the latest official hardware enablement stack then reinstalled FGLRX using the automatic installer and voila!  MASSIVE improvement!

Well back to the Witcher 2 for me!  :D
so which kernel are you using please do tell?  also, i need to know which mesa/libgl libraries you're using as well.

---

### Post by DanglingPointer on 2014-12-13
Hi dannyboy79,
cat /proc/version says this...
> Linux version 3.13.0-43-generic (buildd@toyol) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #72~precise1-Ubuntu SMP Tue Dec 9 12:14:18 UTC 2014

Synaptic Package Manager says this for mesa/libgl...
> 8.0.4-0ubuntu0.7

Important to note that I did nothting special to get the latest HWE, it came automatically through Update Manager.  I simply had to reinstall FGLRX using the auto-installer from the command line and chose Recommended.  It was all seamless and didn't have to tinker around much, just like the user experience in Windows.

On another note on the performance increase but on a different tangent;... I upgraded an X11 darkcoin miner rig of mine which has 2x R9-290s and there was a significant jump in hash rate as well!  X11 mining uses OpenCL. 
Check out the image underneath around 3 a.m. after the Kernel update and FGLRX update!...
[ATTACH=CONFIG]258538[/ATTACH]

---

### Post by dannyboy79 on 2014-12-13
> **DanglingPointer said:**
> Hi dannyboy79,
cat /proc/version says this...


Synaptic Package Manager says this for mesa/libgl...


Important to note that I did nothting special to get the latest HWE, it came automatically through Update Manager.  I simply had to reinstall FGLRX using the auto-installer from the command line and chose Recommended.  It was all seamless and didn't have to tinker around much, just like the user experience in Windows.

On another note on the performance increase but on a different tangent;... I upgraded an X11 darkcoin miner rig of mine which has 2x R9-290s and there was a significant jump in hash rate as well!  X11 mining uses OpenCL. 
Check out the image underneath around 3 a.m. after the Kernel update and FGLRX update!...
[ATTACH=CONFIG]258538[/ATTACH]WOW, that's impressive!  good to know AMD is thinking about more than just their openGL drivers. openCL is EPIC!

---

### Post by DanglingPointer on 2014-12-14
Just finished the Witcher 2 with the new driver in the final Act.  What an awesome game, arguably one of the best modern RPGs of our time.

So I've fired up Total War and maxed out all the settings including unit size (largest most realistic armies), and it looks beautiful!  I've just finished the Tutorial.  The new driver is working beautifully hopefully it doesn't let me down once I get into the Global Campaign.  I have a feeling this game is going to easily suck away some 300hrs of my life at least!

Its been a good end to 2014 for Linux gaming!  Coming soon... Civ Beyond Earth!

Looking forward to 2015 Linux gaming and adoption!

---

