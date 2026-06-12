---
title: "What's wrong with RKWard in 8.10?"
date: 2008-11-18
forum: Education &amp; Science
---

### Post by Benic on 2008-11-18
I upgraded to 8.10 and now, RKWard is just not working. It opens, but if I ever dare to do something, two crash messages appear:

1-Popup window: The support file "/home/../rkward/phpfiles/common.php" could not be found or is not readable. Please check your installation. 

2-Fatal mistake window: The application RKWard (rkward) crashed and caused the signal 11 (SIGSEGV).


I did uninstall and install R version 2.8 and 2.7.2, RKWard version 0.5. R works fine, but RKWard is a mess. Am I missing some KDE packages that the upgrade didn't install? Or is it just a problem of compatibility with 8.10?

---

### Post by hzambran_cl on 2008-11-19
If you update all your system to Ubuntu 8.10 you should have R 2.8.0. If this is your case, the problem is that according to the RKWard site:

"Most importantly RKWard now compiles with R 2.7.0 (which is due to be release, officially, soon)."

So, the problem is not the 8.10 version, but the compatibility between RKWard 0.49a, 0.5b and R 2.8.0.

I hope this be useful for you.

Regards,

Mauricio

---

### Post by earlycj5 on 2008-11-19
[http://ubuntuforums.org/showthread.php?t=894434](http://ubuntuforums.org/showthread.php?t=894434)

---

### Post by Benic on 2008-11-19
> **hzambran_cl said:**
> If you update all your system to Ubuntu 8.10 you should have R 2.8.0. If this is your case, the problem is that according to the RKWard site:

"Most importantly RKWard now compiles with R 2.7.0 (which is due to be release, officially, soon)."

So, the problem is not the 8.10 version, but the compatibility between RKWard 0.49a, 0.5b and R 2.8.0.

I hope this be useful for you.

Regards,

Mauricio


I tried 2.8.0 and 2.7.2 and both don't work.

---

### Post by Benic on 2008-11-19
> **earlycj5 said:**
> [http://ubuntuforums.org/showthread.php?t=894434](http://ubuntuforums.org/showthread.php?t=894434)

I tried everything in that post, but it didn't change anything. By the way, I found out that the problem with the pluginmap link is that instead of being /usr/share/apps/rkard/allplugin.map it shows /usr/share/apps//rkard/allplugin.map (two slahes before rkward). I'm really puzzled right now...

---

### Post by Benic on 2008-11-19
I just realized that one of the error message was about php (home/.../rkward/phpfiles/common.php couldn't be found or is not readable). There's no such file. Common.php is located in /usr/share/apps/rkward/ so how can I change the path?


Well, it seems impossible to recompile RKWard (keeps on crashing...) and after more than 10 hours spent on this issue I give up. I'll try [_R Commander_]("http://socserv.mcmaster.ca/jfox/Misc/Rcmdr/") instead.

---

### Post by ahmatti on 2008-11-20
You might also give ESS ([http://ess.r-project.org/](http://ess.r-project.org/)) a try! It's a great choice if you use R frequently :) It's also in the repos.

---

### Post by earlycj5 on 2008-11-20
> **Benic said:**
> I just realized that one of the error message was about php (home/.../rkward/phpfiles/common.php couldn't be found or is not readable). There's no such file. Common.php is located in /usr/share/apps/rkward/ so how can I change the path?

Like I said in that post create a symlink.

That doesn't fix all my problems with RKward in 8.10 though either.  There's missing icons in the toolbar, I can't create a new script file.

Irritating to say the least, RKward is my favorite IDE for R and I'm too grouchy and set in my ways to learn something new.  :D

---

### Post by Benic on 2008-11-20
> **earlycj5 said:**
> Like I said in that post create a symlink.

That doesn't fix all my problems with RKward in 8.10 though either.  There's missing icons in the toolbar, I can't create a new script file.

Irritating to say the least, RKward is my favorite IDE for R and I'm too grouchy and set in my ways to learn something new.  :D

I understand your point. RKWard is convenient and user-friendly. But to me, it seems that it's not quite ready for 8.10. I hope the issues will be fix in a new release of RKWard. I've been using it for less than two months, so I don't mind changing. It won't be the first time (SPSS to STATA to R). I'm already confused and clueless, so a bit more or less won't make a big difference :)

---

### Post by Benic on 2009-01-21
Well, well, well! This morning, I had to reinstall R after a fresh install of 8.10. I decided to give rkward a try. I don't know how, but now it's finally working! 

This is what I did. I first installed R in synaptic. Then installed Rkward in synaptic. It wouldn't load, so I uninstalled and installed the rkward_0.5.0b-1_i386_sid deb package instead. Did a little update in update manager. So now rkward would work. Few problems still: the top menu was messy. So I followed earlycj5 advice and changed the all.pluginmap path in the configuration menu. Then I, as proposed by earlycj5 and asdir in this [_post_]("http://ubuntuforums.org/showthread.php?t=894434&highlight=rkward&page=2") I created two symlinks:

```
sudo ln -s .rkward rkward
sudo ln -s /usr/share/apps/rkward/phpfiles rkward
```

Now rkward is working, but I still have this message in the terminal:
QFSFileEngine::open: No file name specified

It doesn't seem to affect rkward yet. I will try to find a fix.

---

### Post by UbuWu on 2009-01-21
Did you file a bug?

---

### Post by Benic on 2009-01-21
> **UbuWu said:**
> Did you file a bug?

If you're talking about the missing plugin bug, it's [_bug #272527_]("https://bugs.launchpad.net/ubuntu/+source/rkward/+bug/272527").

About the QSF issue, it's mentionned in [_bug #294610_]("https://bugs.launchpad.net/ubuntu/+source/rkward/+bug/294610").

---

### Post by Benic on 2009-02-03
Hmmm... Top menu is still a mess. A lot of functions are missing. But at least no more crashing issue.

---

### Post by earlycj5 on 2009-02-03
> **Benic said:**
> Hmmm... Top menu is still a mess. A lot of functions are missing. But at least no more crashing issue.

Depending on how adventurous you are you can compile it yourself too.

That's what I've done on all of my machines.

I've compiled R and then RKWard.  R is pretty straightforward, this post in the RKWard forum is instructive for compiling and installing RKWard.
[https://sourceforge.net/forum/message.php?msg_id=5508112](https://sourceforge.net/forum/message.php?msg_id=5508112)

---

### Post by Benic on 2009-02-03
I downloaded the rkward-0.5.0b source. I compiled it using checkinstall (it's easier to remove). Now Rkward is fully functional. The menu bar is complete.

The only thing I had to change was the path to all.pluginmap, now located in /usr/local/share/apps/rkward/

---

### Post by earlycj5 on 2009-02-04
> **Benic said:**
> I downloaded the rkward-0.5.0b source. I compiled it using checkinstall (it's easier to remove). Now Rkward is fully functional. The menu bar is complete.

The only thing I had to change was the path to all.pluginmap, now located in /usr/local/share/apps/rkward/

Glad to hear it's working properly now.

---

### Post by Benic on 2009-02-04
Is there a tar.gz for the latest version Rkard 0.5.0b-2? I can't find it on sourceforge. Or do I need to patch 0.5.0b-1? If I update it via synaptic or the repo, it's broken.

---

### Post by earlycj5 on 2009-02-05
> **Benic said:**
> Is there a tar.gz for the latest version Rkard 0.5.0b-2? I can't find it on sourceforge. Or do I need to patch 0.5.0b-1? If I update it via synaptic or the repo, it's broken.

I'm just using the SVN version per the post I linked to in their forums.  The last tarball I used had issues with later releases of R.

---

### Post by Benic on 2009-04-14
The new 0.5.0c version is out. I decided to give it a try: bad idea! I downloaded the deb package and I also tried to compile it, without success. The dependencies required are installed, still the program tells me that some dependencies are missing. There's bug _[354037]("https://bugs.launchpad.net/ubuntu/+source/rkward/+bug/354037")_, but there's not much about it.

Has anyone successfully installed this version?

---

### Post by earlycj5 on 2009-04-14
Still succesfully using the SVN version with my own compilation of R, no issues on two computers with 8.10.

---

### Post by NikoC on 2009-04-15
> **earlycj5 said:**
> Still succesfully using the SVN version with my own compilation of R, no issues on two computers with 8.10.

+1 on the rkward svn version!

---

### Post by Benic on 2009-04-15
> **earlycj5 said:**
> Still succesfully using the SVN version with my own compilation of R, no issues on two computers with 8.10.

I've (finally!) decided to try the SVN version. So far, so good!

---

### Post by Benic on 2009-11-09
I had some trouble with Karmic and RKward. Here's the first problem I ran through:

```
*** stack smashing detected ***: rkward terminated
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(__fortify_fail+0x48)[0xb55fade8]
/lib/tls/i686/cmov/libc.so.6(__fortify_fail+0x0)[0xb55fada0]
/usr/lib/R/lib/libR.so[0xb6b08534]
/usr/lib/R/lib/libR.so[0xb69e288b]
rkward[0x8140b0f]
rkward[0x8139e62]
rkward[0x813a66e]
/usr/lib/libQtCore.so.4[0xb57e3e32]
/lib/tls/i686/cmov/libpthread.so.0[0xb53a880e]
/lib/tls/i686/cmov/libc.so.6(clone+0x5e)[0xb55e67ee]
======= Memory map: ========
08048000-08177000 r-xp 00000000 08:03 650325     /usr/local/bin/rkward.bin
08177000-08178000 r--p 0012e000 08:03 650325     /usr/local/bin/rkward.bin
08178000-0817a000 rw-p 0012f000 08:03 650325     /usr/local/bin/rkward.bin
0817a000-0817b000 rw-p 00000000 00:00 0 
09c96000-0ad7c000 rw-p 00000000 00:00 0          [heap]
b13ea000-b1433000 r-xp 00000000 08:03 579121     /usr/lib/libjasper.so.1.0.0
b1433000-b1434000 r--p 00048000 08:03 579121     /usr/lib/libjasper.so.1.0.0
b1434000-b1437000 rw-p 00049000 08:03 579121     /usr/lib/libjasper.so.1.0.0
b1437000-b143d000 rw-p 00000000 00:00 0 
b143d000-b14fd000 r-xp 00000000 08:03 579436     /usr/lib/libIlmImf.so.6.0.0
b14fd000-b14ff000 r--p 000bf000 08:03 579436     /usr/lib/libIlmImf.so.6.0.0
b14ff000-b1500000 rw-p 000c1000 08:03 579436     /usr/lib/libIlmImf.so.6.0.0
b1500000-b15df000 rw-p 00000000 00:00 0 
b15df000-b1600000 ---p 00000000 00:00 0 
b1636000-b1646000 r-xp 00000000 08:03 837424     /usr/lib/kde4/plugins/imageformats/kimg_xcf.so
b1646000-b1647000 r--p 0000f000 08:03 837424     /usr/lib/kde4/plugins/imageformats/kimg_xcf.so
b1647000-b1648000 rw-p 00010000 08:03 837424     /usr/lib/kde4/plugins/imageformats/kimg_xcf.so
b1648000-b164c000 rw-p 00000000 00:00 0 
b164c000-b1654000 r-xp 00000000 08:03 837420     /usr/lib/kde4/plugins/imageformats/kimg_pcx.so
b1654000-b1655000 r--p 00007000 08:03 837420     /usr/lib/kde4/plugins/imageformats/kimg_pcx.so
b1655000-b1656000 rw-p 00008000 08:03 837420     /usr/lib/kde4/plugins/imageformats/kimg_pcx.so
b1656000-b1698000 r-xp 00000000 08:03 577475     /usr/lib/libHalf.so.6.0.0
b1698000-b1699000 r--p 00041000 08:03 577475     /usr/lib/libHalf.so.6.0.0
b1699000-b169a000 rw-p 00042000 08:03 577475     /usr/lib/libHalf.so.6.0.0
b169a000-b16fc000 r-xp 00000000 08:03 622698     /usr/lib/R/library/stats/libs/stats.so
b16fc000-b16fd000 ---p 00062000 08:03 622698     /usr/lib/R/library/stats/libs/stats.so
b16fd000-b16fe000 r--p 00062000 08:03 622698     /usr/lib/R/library/stats/libs/stats.so
b16fe000-b16ff000 rw-p 00063000 08:03 622698     /usr/lib/R/library/stats/libs/stats.so
b16ff000-b1700000 rw-p 00000000 00:00 0 
b1700000-b1900000 rw-p 00000000 00:00 0 
b1900000-b1a00000 rw-p 00000000 00:00 0 
b1a02000-b1a07000 r-xp 00000000 08:03 179930     /usr/lib/qt4/plugins/imageformats/libqgif.so
b1a07000-b1a08000 r--p 00004000 08:03 179930     /usr/lib/qt4/plugins/imageformats/libqgif.so
b1a08000-b1a09000 rw-p 00005000 08:03 179930     /usr/lib/qt4/plugins/imageformats/libqgif.so
b1a09000-b1a0e000 r-xp 00000000 08:03 837423     /usr/lib/kde4/plugins/imageformats/kimg_tga.so
b1a0e000-b1a0f000 r--p 00004000 08:03 837423     /usr/lib/kde4/plugins/imageformats/kimg_tga.so
b1a0f000-b1a10000 rw-p 00005000 08:03 837423     /usr/lib/kde4/plugins/imageformats/kimg_tga.so
b1a10000-b1a16000 r-xp 00000000 08:03 579017     /usr/lib/libIlmThread.so.6.0.0
b1a16000-b1a17000 r--p 00005000 08:03 579017     /usr/lib/libIlmThread.so.6.0.0
b1a17000-b1a18000 rw-p 00006000 08:03 579017     /usr/lib/libIlmThread.so.6.0.0
b1a18000-b1aa4000 r--p 00000000 08:03 692620     /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans-Bold.ttf
b1aa4000-b1ab1000 r--p 00000000 08:03 692258     /usr/share/fonts/truetype/ttf-bitstream-vera/VeraMono.ttf
b1ab1000-b1b9d000 r--s 00000000 08:03 16773      /home/bureau/.kde/cache-bureau-bm/ksycoca4
b1b9d000-b1bc1000 r-xp 00000000 08:03 620717     /usr/lib/R/library/grDevices/libs/grDevices.so
b1bc1000-b1bc2000 r--p 00023000 08:03 620717     /usr/lib/R/library/grDevices/libs/grDevices.so
b1bc2000-b1bc3000 rw-p 00024000 08:03 620717     /usr/lib/R/library/grDevices/libs/grDevices.so
b1bc3000-b1bc7000 r-xp 00000000 08:03 837425     /usr/lib/kde4/plugins/imageformats/kimg_xview.so
b1bc7000-b1bc8000 r--p 00003000 08:03 837425     /usr/lib/kde4/plugins/imageformats/kimg_xview.so
b1bc8000-b1bc9000 rw-p 00004000 08:03 837425     /usr/lib/kde4/plugins/imageformats/kimg_xview.so
b1bc9000-b1bcd000 r-xp 00000000 08:03 578608     /usr/lib/libImath.so.6.0.0
b1bcd000-b1bce000 r--p 00003000 08:03 578608     /usr/lib/libImath.so.6.0.0
b1bce000-b1bcf000 rw-p 00004000 08:03 578608     /usr/lib/libImath.so.6.0.0
b1bcf000-b1be5000 r-xp 00000000 08:03 577473     /usr/lib/libIex.so.6.0.0
b1be5000-b1be7000 r--p 00015000 08:03 577473     /usr/lib/libIex.so.6.0.0
b1be7000-b1be8000 rw-p 00017000 08:03 577473     /usr/lib/libIex.so.6.0.0
b1bea000-b1bf4000 r-xp 00000000 08:03 837422     /usr/lib/kde4/plugins/imageformats/kimg_rgb.so
b1bf4000-b1bf5000 r--p 00009000 08:03 837422     /usr/lib/kde4/plugins/imageformats/kimg_rgb.so
b1bf5000-b1bf6000 rw-p 0000a000 08:03 837422     /usr/lib/kde4/plugins/imageformats/kimg_rgb.so
b1bf6000-b1bfa000 r-xp 00000000 08:03 837421     /usr/lib/kde4/plugins/imageformats/kimg_psd.so
b1bfa000-b1bfb000 r--p 00003000 08:03 837421     /usr/lib/kde4/plugins/imageformats/kimg_psd.so
b1bfb000-b1bfc000 rw-p 00004000 08:03 837421     /usr/lib/kde4/plugins/imageformats/kimg_psd.so
b1bfc000-b1c00000 r-xp 00000000 08:03 837419     /usr/lib/kde4/plugins/imageformats/kimg_jp2.so
b1c00000-b1c01000 r--p 00003000 08:03 837419     /usr/lib/kde4/plugins/imageformats/kimg_jp2.so
b1c01000-b1c02000 rw-p 00004000 08:03 837419     /usr/lib/kde4/plugins/imageformats/kimg_jp2.so
b1c02000-b1c07000 r-xp 00000000 08:03 837418     /usr/lib/kde4/plugins/imageformats/kimg_exr.so
b1c07000-b1c08000 r--p 00004000 08:03 837418     /usr/lib/kde4/plugins/imageformats/kimg_exr.so
b1c08000-b1c09000 rw-p 00005000 08:03 837418     /usr/lib/kde4/plugins/imageformats/kimg_exr.so
b1c09000-b1c10000 r-xp 00000000 08:03 837417     /usr/lib/kde4/plugins/imageformats/kimg_eps.so
b1c10000-b1c11000 r--p 00006000 08:03 837417     /usr/lib/kde4/plugins/imageformats/kimg_eps.soKCrash: Application 'rkward' crashing...

```

Solution: I tried to recompile the SVN version and found a bug with cmake that is related to phonon library: bug #[_386742_]("https://bugs.launchpad.net/ubuntu/+source/cmake/+bug/386742"). The solution is to reinstall libqt4-phonon-dev. Worked for me and still I wasn't able compile RKWard because CMAKE_MODULE_PATH was incorrect. Installing kdelibs5-dev was the solution. I recompiled RKWard and it is fully functional right now.

---

