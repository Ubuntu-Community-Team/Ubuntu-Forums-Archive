---
title: "Ubuntu and Nvidia frustration"
date: 2007-07-09
forum: Desktop Environments
---

### Post by backdoc on 2007-07-09
I love ubuntu.  And, I really appreciate all of the hard work that so many people have put into making a fine product.  But, I get so frustrated at times with the way upgrades break X.

At work, I have a dual screen setup that took me a day to two get working with Ubuntu.  I have the Geforce 4 integrated video card.  And, it requires the legacy glx support.  Ubuntu kept trying to upgrade to the newer version of glx.  And, I kept holding it back.  Then, in a weak moment, I didn't catch it.  I rebooted (because I have to dual boot) and on restart BAM! no more X.  Son of a Bitch!  This frustrates the hell out of me.  If getting X working is not already the most annoying thing in the world, getting dual monitors set up is.

So, when will Ubuntu stop breaking X?  That's my question.

---

### Post by QCompson on 2007-07-09
I feel your pain.  Although this issue (for me) has improved tremendously in the past few years, I still cringe when I receive a new glx or kernel update.  I have had too many experiences where I reboot after an update and get spit onto a command line, or suddenly can't use certain programs because they depend on the kernel version.  

Again, it has gotten better, but it has happened enough times in the past to me that I dread seeing that little update symbol in my tray.

I don't think this is an ubuntu-specific issue.

---

### Post by Nythain on 2007-07-10
dont know... ubuntu has never broke x for me... i install the package nvidia-glx-new (you would need nvidia-glx-legacy) and it only updates that package when i get a new kernel or they decide to update the driver they use (not to damn often on that one seein as how they've been using 9755 since feisty came out, and nvidia is already up to the 10's)... and since it updates the package when it updates teh kernel i never get a mismatch (the most common x "brake", when users compile thier own drivers downloaded from nvidia site, not reading that they are going to have to recompile every time they upgrade thier kernel, then they get a kernel upgrade and are like WTF)

wish i could help you... theoretically if you installed the glx-legacy package it shouldnt ever try to install a different package, and i dont know how long its been since they've updated the driver used in that package since its there for legacy support i would assume it has been a looooooong time

ok, a little googling and i found that the nvidia-glx-legacy is using driver number 7184... and here's 7184's supported cards
```

(app-a) APPENDIX A: SUPPORTED NVIDIA GRAPHICS CHIPS

  NVIDIA CHIP NAME                     DEVICE PCI ID

  RIVA TNT                             0x0020
  RIVA TNT2/TNT2 Pro                   0x0028
  RIVA TNT2 Ultra                      0x0029
  Vanta/Vanta LT                       0x002C
  RIVA TNT2 Model 64/Model 64 Pro      0x002D
  GeForce 6800 Ultra                   0x0040
  GeForce 6800                         0x0041
  GeForce 6800 GT                      0x0045
  Quadro FX 4000                       0x004E
  Aladdin TNT2                         0x00A0
  GeForce 6800                         0x00C1
  GeForce 6800 LE                      0x00C2
  GeForce Go 6800                      0x00C8
  GeForce Go 6800 Ultra                0x00C9
  Quadro FX Go1400                     0x00CC
  Quadro FX Go1400                     0x00CC
  Quadro FX 3450/4000 SDI              0x00CD
  Quadro FX 1400                       0x00CE
  GeForce 6800/GeForce 6800 Ultra      0x00F0
  GeForce 6600/GeForce 6600 GT         0x00F1
  GeForce 6600                         0x00F2
  GeForce 6200                         0x00F3
  GeForce 6200                         0x00F3
  Quadro FX 3400                       0x00F8
  GeForce 6800 Ultra                   0x00F9
  GeForce PCX 5750                     0x00FA
  GeForce PCX 5900                     0x00FB
  Quadro FX 330/GeForce PCX 5300       0x00FC
  Quadro NVS 280 PCI-E/Quadro FX 330   0x00FD
  Quadro FX 1300                       0x00FE
  GeForce PCX 4300                     0x00FF
  GeForce 256                          0x0100
  GeForce DDR                          0x0101
  Quadro                               0x0103
  GeForce2 MX/MX 400                   0x0110
  GeForce2 MX 100/200                  0x0111
  GeForce2 Go                          0x0112
  Quadro2 MXR/EX/Go                    0x0113
  GeForce 6600 GT                      0x0140
  GeForce 6600                         0x0141
  GeForce Go 6600                      0x0144
  GeForce 6610 XL                      0x0145
  GeForce Go 6600 TE/6200 TE           0x0146
  GeForce Go 6600                      0x0148
  Quadro FX 540                        0x014E
  GeForce 6200                         0x014F
  GeForce2 GTS/GeForce2 Pro            0x0150
  GeForce2 Ti                          0x0151
  GeForce2 Ultra                       0x0152
  Quadro2 Pro                          0x0153
  GeForce 6200 TurboCache(TM)          0x0161
  GeForce 6200SE TurboCache(TM)        0x0162
  GeForce Go 6200                      0x0164
  GeForce Go 6250                      0x0166
  GeForce Go 6200                      0x0167
  GeForce Go 6250                      0x0168
  GeForce4 MX 460                      0x0170
  GeForce4 MX 440                      0x0171
  GeForce4 MX 420                      0x0172
  GeForce4 MX 440-SE                   0x0173
  GeForce4 440 Go                      0x0174
  GeForce4 420 Go                      0x0175
  GeForce4 420 Go 32M                  0x0176
  GeForce4 460 Go                      0x0177
  Quadro4 550 XGL                      0x0178
  GeForce4 440 Go 64M                  0x0179
  Quadro NVS                           0x017A
  Quadro4 500 GoGL                     0x017C
  GeForce4 410 Go 16M                  0x017D
  GeForce4 MX 440 with AGP8X           0x0181
  GeForce4 MX 440SE with AGP8X         0x0182
  GeForce4 MX 420 with AGP8X           0x0183
  GeForce4 MX 4000                     0x0185
  Quadro4 580 XGL                      0x0188
  Quadro NVS with AGP8X                0x018A
  Quadro4 380 XGL                      0x018B
  Quadro NVS 50 PCI                    0x018C
  GeForce2 Integrated GPU              0x01A0
  GeForce4 MX Integrated GPU           0x01F0
  GeForce3                             0x0200
  GeForce3 Ti 200                      0x0201
  GeForce3 Ti 500                      0x0202
  Quadro DCC                           0x0203
  GeForce 6800                         0x0211
  GeForce 6800 LE                      0x0212
  GeForce 6800 GT                      0x0215
  GeForce4 Ti 4600                     0x0250
  GeForce4 Ti 4400                     0x0251
  GeForce4 Ti 4200                     0x0253
  Quadro4 900 XGL                      0x0258
  Quadro4 750 XGL                      0x0259
  Quadro4 700 XGL                      0x025B
  GeForce4 Ti 4800                     0x0280
  GeForce4 Ti 4200 with AGP8X          0x0281
  GeForce4 Ti 4800 SE                  0x0282
  GeForce4 4200 Go                     0x0286
  Quadro4 980 XGL                      0x0288
  Quadro4 780 XGL                      0x0289
  Quadro4 700 GoGL                     0x028C
  GeForce FX 5800 Ultra                0x0301
  GeForce FX 5800                      0x0302
  Quadro FX 2000                       0x0308
  Quadro FX 1000                       0x0309
  GeForce FX 5600 Ultra                0x0311
  GeForce FX 5600                      0x0312
  GeForce FX 5600XT                    0x0314
  GeForce FX Go5600                    0x031A
  GeForce FX Go5650                    0x031B
  Quadro FX Go700                      0x031C
  GeForce FX 5200                      0x0320
  GeForce FX 5200 Ultra                0x0321
  GeForce FX 5200                      0x0322
  GeForce FX 5200LE                    0x0323
  GeForce FX Go5200                    0x0324
  GeForce FX Go5250                    0x0325
  GeForce FX 5500                      0x0326
  GeForce FX 5100                      0x0327
  GeForce FX Go5200 32M/64M            0x0328
  Quadro NVS 280 PCI                   0x032A
  Quadro FX 500/FX 600                 0x032B
  GeForce FX Go53xx                    0x032C
  GeForce FX Go5100                    0x032D
  GeForce FX 5900 Ultra                0x0330
  GeForce FX 5900                      0x0331
  GeForce FX 5900XT                    0x0332
  GeForce FX 5950 Ultra                0x0333
  GeForce FX 5900ZT                    0x0334
  Quadro FX 3000                       0x0338
  Quadro FX 700                        0x033F
  GeForce FX 5700 Ultra                0x0341
  GeForce FX 5700                      0x0342
  GeForce FX 5700LE                    0x0343
  GeForce FX 5700VE                    0x0344
  GeForce FX Go5700                    0x0347
  GeForce FX Go5700                    0x0348
  Quadro FX Go1000                     0x034C
  Quadro FX 1100                       0x034E

```
it was release feb. 7 2006 so its safe to say its not a recent update
in fact nvidia themselves are up to 7185, just to show you how not often ubuntu updates nvidia drivers in teh repos

---

### Post by backdoc on 2007-07-10
First of all, my apologies for the rant.  Fixing X again just wasn't what I had in mind to do yesterday.  And, knowing I would be faced with the daunting task, I got annoyed. 

> **Nythain said:**
> dont know... ubuntu has never broke x for me... i install the package nvidia-glx-new (you would need nvidia-glx-legacy) and it only updates that package when i get a new kernel or they decide to update the driver they use (not to damn often on that one seein as how they've been using 9755 since feisty came out, and nvidia is already up to the 10's)... and since it updates the package when it updates teh kernel i never get a mismatch (the most common x "brake", when users compile thier own drivers downloaded from nvidia site, not reading that they are going to have to recompile every time they upgrade thier kernel, then they get a kernel upgrade and are like WTF)

<snipage />


Yeah.  The more I think about it, the more I think that's what I finally had to do to get X working last time (installed it from nVidia).  I probably got a new kernel in the upgrade.  I don't typically like building from source and getting unsupported packages for reasons like this.  Sometimes though, you have to.  And, it was the only way I could figure out how to get X working.  Still, regardless of how it happens, maybe there is a way to avoid the whole problem.

Oh well.  I'll figure it out again. 

Thanks for listening to me vent.

---

### Post by backdoc on 2007-07-10
> **backdoc said:**
> First of all, my apologies for the rant.  Fixing X again just wasn't what I had in mind to do yesterday.  And, knowing I would be faced with the daunting task, I got annoyed. 



Yeah.  The more I think about it, the more I think that's what I finally had to do to get X working last time (installed it from nVidia).  I probably got a new kernel in the upgrade.  I don't typically like building from source and getting unsupported packages for reasons like this.  Sometimes though, you have to.  And, it was the only way I could figure out how to get X working.  Still, regardless of how it happens, maybe there is a way to avoid the whole problem.

Oh well.  I'll figure it out again. 

Thanks for listening to me vent.

I'm back at work now and have had time to work on the problem a little more.  I don't see any evidence that the way I got it working last time was by downloading the driver from nVidia.  So, I'm not sure what I did.  The "evidence" I am referring to is that I don't see the NVIDIA*.run file lying around /usr/local/src (which is where I would have put it).

But, I have tried installing the driver from nVidia this morning, which hasn't worked yet.  It compiled the module against my current kernel.  But, the module fails to load.  A quick look at the forums on the nVidia site suggests to me that the Xen kernel might be a problem.  I believe while I was working on this problem yesterday that I noticed my kernel now includes Xen (see attached screenshot).  But, if that was the problem, you would have thought it would have affected everyone with an nVidia card.  So, I'm suspicious that I'm barking up the wrong tree.  The link where the screenshot came from is:  [http://www.nvnews.net/vbulletin/showthread.php?t=72490]("http://www.nvnews.net/vbulletin/showthread.php?t=72490")

I think I may be lucky enough to have a recent image of my computer.  So, I may be able to restore Ubuntu from an image.  I may give that a try.

I'm open to suggestions.

---

### Post by Wraukon on 2007-07-11
Talk about frustration.

I'm a n00buntu user (for ease of backups among other reasons), and I'm having the following problem:

Running Feisty Dawn 7.4 i686 (i386) trying to set up a system for my daughter.  I gave her my GeForce Ti
4600, which is a respectable graphics card, but the system insists on using legacy 2d drivers rather than
accelerating 3d.  When I downloaded the RUN file from nVidia, it told me:

"This GPU will not use the updated driver"

but it didn't tell me *why* or what's going on :confused:

I'd like her to be able to make full use of the acceleration.  I've googled for it and come up fairly sparse,
if not empty.

While I'm at it, I'm getting ready to upgrade my WinXP box to ubuntu:
AMD Athlon 64 x2 (dual core)
D-Link DGE-560T ethernet
Realtek 8169 or something ethernet
nVidia GeForce 7900 KO graphics card

...will ubuntu choke on this card, too?

Please help?

---

### Post by backdoc on 2007-07-11
> **Wraukon said:**
> Talk about frustration.

I'm a n00buntu user (for ease of backups among other reasons), and I'm having the following problem:

Running Feisty Dawn 7.4 i686 (i386) trying to set up a system for my daughter.  I gave her my GeForce Ti
4600, which is a respectable graphics card, but the system insists on using legacy 2d drivers rather than
accelerating 3d.  When I downloaded the RUN file from nVidia, it told me:

"This GPU will not use the updated driver"

but it didn't tell me *why* or what's going on :confused:

I'd like her to be able to make full use of the acceleration.  I've googled for it and come up fairly sparse,
if not empty.

While I'm at it, I'm getting ready to upgrade my WinXP box to ubuntu:
AMD Athlon 64 x2 (dual core)
D-Link DGE-560T ethernet
Realtek 8169 or something ethernet
nVidia GeForce 7900 KO graphics card

...will ubuntu choke on this card, too?

Please help?

I don't have an answer for you.  I haven't gotten my own working yet.  However, with a stand alone card, I've never had a lot of trouble.  Then again, if I see the nVidia logo pop up, I'm happy.  So, I don't really care if it's the legacy drivers or not.  I found a list somewhere when I was working on getting my card working the first time that tells you exactly which cards a driver works with.  See if you can find that.  If your card is listed as not being supported by the latest drivers, then I don't guess you'll have much choice.

Something that seems to be relevant when trying different things is using the purge option with aptitude.  Maybe you're using Synaptic.  If so, I don't know how to pass the purge option to it.  Most of the time I use the aptitude from the command line.  And, to remove the config files, you need to use the purge.  I learned that from the link to the nvidia site in my previous post.  Another useful tip for using the command line is to use "search" like this:  aptitude search nvidia.  This will show you what's installed and what's not.  I haven't figured out all of the legend information.  But, I think "i" == installed, "p" == package, "c" == means the config files are installed (turns into a "p" after using purge) and "v" == virtual package (not too sure what virtual means --- I guess it's a package but just virtual . . . hmmm).

I'll keep this thread updated with my progress.

---

### Post by phidia on 2007-07-11
Because the forums here are so large people can get a little lost-I think that's what's happening and perhaps too it would be helpful if the grahics card section had it's own thread, but disregarding all that there is a thread here to help in setting up your gpu [http://ubuntuforums.org/showthread.php?t=301499](http://ubuntuforums.org/showthread.php?t=301499)
BTW I'm pretty sure the geforce 7900 is supported.

---

