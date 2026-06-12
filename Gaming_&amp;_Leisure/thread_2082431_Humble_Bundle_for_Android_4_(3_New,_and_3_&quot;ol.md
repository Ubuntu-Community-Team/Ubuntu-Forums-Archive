---
title: "Humble Bundle for Android 4 (3 New, and 3 &quot;old&quot; )"
date: 2012-11-09
forum: Gaming &amp; Leisure
---

### Post by Dlambert on 2012-11-09
With all the hype about Steam it's easy to understand why this post hasen't been made yet, but here it is!
 
> 
**Six glorious games for your mobile entertainment.** Humble Bundle for Android 4 features a handpicked selection of the finest portable gaming ever seen for Android. Pay-what-you-want and dive into the creative physics puzzler *Crayon Physics Deluxe*; the plant-based interstellar RTS *Eufloria*; the cell-splitting microbial puzzler *Splice*; the future-retro audiovisual concoction *Superbrothers: Sword & Sworcery EP*; and the side-scrolling planetary adventure, *Waking Mars*. Customers who pay more than the average price will also get the fantastic mechanical point-and-click adventure *Machinarium*!
**Desktop ready.** Buying the Humble Bundle for Android 4 also gets you the games on Windows, Mac, and Linux! For your listening pleasure, all six games also come with an official soundtrack.
**Pay what you want.** On their own, buying this unbeatable collection of mobile and desktop games with soundtracks would cost around $119, but we're letting you name your price!
**The games are DRM-free and work great on Android, Windows, Mac, and Linux ([system requirements here]("http://support.humblebundle.com/customer/portal/articles/812570-humble-bundle-for-android-4-system-requirements")).** Note that this is the initial release for many of the Android and Linux versions of the games. Please be patient while the developers fix any 1.0 bugs as quickly as they can, and don't hesitate to contact us if you run into any issues!
**Support charities and developers.** Choose how your purchase is divided: to the developers, the Electronic Frontier Foundation, and/or the Child's Play Charity. And if you like this promotion, a tip to the Humble Bundle would be greatly appreciated!
 
 
[http://www.humblebundle.com/](http://www.humblebundle.com/)
 
 
The New games:
 
> 
**Splice**

[Cipher Prime]("http://www.cipherprime.com/games/splice/") 
Resequence, mutate, and splice in this experimental microbial puzzler by Cipher Prime. Available for the first time on Android, *Splice* will strain your brain while you commence cellular alteration to connect and complete a sequence of puzzles, all to a fantastic and compelling score. 
For the best Splice experience, Cipher Prime recommends a device with a screen size of five inches or larger. 
 
> 
**Eufloria**

[Omni Systems]("http://www.eufloria-game.com/") 
Take to space, conquer asteroids, and grow an organic army of seedlings in this elegant and unique real-time strategy game by Omni Systems. Featuring themes of plant growth and bio mechanical evolution, *Eufloria* uses beautiful visuals and an amazing ambient soundtrack to create an experience unlike any other. 
 
> 
**Waking Mars**

[Tiger Style]("http://www.tigerstylegames.com/wakingmars/") 
When a mission of first contact doesn't go as expected, astrobiologist Liang is trapped underneath the surface of Mars. With the help of his trusty jetpack and his allies on the surface, you must help Liang discover the secret ecosystem underground and bring a sleeping planet to life. *Waking Mars* developers Tiger Style describe the gameplay as "action gardening" where the player controls how the ecosystem of Mars develops, making for a unique environment dictated by the player's actions. 
*Waking Mars* has been nominated for Best Mobile Game and Excellence in Audio in 2012 Independent Game Festival, and is debuting for Windows, Mac, Linux, and Android. 
 
 
This bundle also includes Crayon Physics, Superbrothers:SSEP, and Machinarium.

---

### Post by em3raldxiii on 2012-11-10
Yep, I bought it :D  I like to support the humble bundles.  Sadly, I only learned about them fairly recently, so I have only been able to snag 2 of the bundles so far (including this one).  So far almost all of the games are running perfectly.  I find Torchlight (from the last bundle) is amazing.  I have a couple of notes for people who try this latest bundle out:

**Machinarium** works well, but note that it is Flash based.  On my stock system with the open source Radeon drivers, there is a strange issue with the mouse where it is very slow and laggy when moving over interactive areas.  The solution has been to do one or both of these steps:  Right-Click in the game and DE-select hardware acceleration, and then also within the game, move to the bottom of the screen and DE-select full-screen mode.  From there it works beautifully.

**Crayon Physics** looks to be a super entertaining little game, and possibly fun for kids too.  Unfortunately, I haven't been able to launch this one.  I attempted registering on their forum, but it appears their registration system is broken (takes me to a blank page).  Here are details:

Crayon Physics is the only game from the Humble Indie Bundle that is not working for me on my stock Ubuntu 12.10 with the open source Radeon drivers. Running from the terminal gives me the following message:

```

$ /opt/crayon-physics-deluxe/launcher
libGL error: failed to load driver: r600
libGL error: Try again with LIBGL_DEBUG=verbose for more details.
libGL error: failed to load driver: swrast
libGL error: Try again with LIBGL_DEBUG=verbose for more details.
Segmentation fault (core dumped)

```

These seem to indicate that there are missing drivers or libraries, but this is definitely not the case as everything else on my system runs perfectly, including numerous graphics-intensive games. I suspect that the game is calling to the wrong location somehow for the game. Also note that I do have both SWRAST and R600 installed as shown by this output:

```

$ locate r600
/usr/include/libdrm/r600_pci_ids.h
/usr/lib/i386-linux-gnu/dri/r600_dri.so
/usr/lib/i386-linux-gnu/gbm/pipe_r600.so

```

and

```

$ locate swrast
/usr/lib/i386-linux-gnu/dri/swrast_dri.so
/usr/lib/i386-linux-gnu/gbm/pipe_swrast.so

```

I installed the game using the Ubuntu Software Center method, linked from the Humble Bundle confirmation page.

Anyhoo ... I posted this here for 2 reasons:  First to help anyone else who might encounter my issues, and second to stir up some discussion on the problems.

Cheers!

---

### Post by weasel fierce on 2012-11-10
Not as interested in this one as some previous ones, but I picked it up for the support. 

It's always nice to have some fun puzzle games to spend a little time on.

---

### Post by evilsoup on 2012-11-10
Be careful with Machnarium. It stores its save as a flash cookie, so if you are in the habit of deleting those you'll have a problem.

---

### Post by pardalet on 2012-11-10
> **em3raldxiii said:**
> Crayon Physics is the only game from the Humble Indie Bundle that is not working for me on my stock Ubuntu 12.10 with the open source Radeon drivers. Running from the terminal gives me the following message:

```

$ /opt/crayon-physics-deluxe/launcher
libGL error: failed to load driver: r600
libGL error: Try again with LIBGL_DEBUG=verbose for more details.
libGL error: failed to load driver: swrast
libGL error: Try again with LIBGL_DEBUG=verbose for more details.
Segmentation fault (core dumped)

```

These seem to indicate that there are missing drivers or libraries, but this is definitely not the case as everything else on my system runs perfectly, including numerous graphics-intensive games. I suspect that the game is calling to the wrong location somehow for the game. Also note that I do have both SWRAST and R600 installed as shown by this output:

```

$ locate r600
/usr/include/libdrm/r600_pci_ids.h
/usr/lib/i386-linux-gnu/dri/r600_dri.so
/usr/lib/i386-linux-gnu/gbm/pipe_r600.so

```

and

```

$ locate swrast
/usr/lib/i386-linux-gnu/dri/swrast_dri.so
/usr/lib/i386-linux-gnu/gbm/pipe_swrast.so

```


I am experiencing the same problem. It seems to be due to the **libstdc++.so.6** which comes with the game (in the lib32 directory on /opt/CrayonPhysicsDeluxe). This is an outdated version of the library and hence all the fuss.

I just replaced **/opt/CrayonPhysicsDeluxe/lib32/libstdc++.so.6** with **/usr/lib/i386-linux-gnu/libstdc++.so.6.0.17** (renaming it to libstdc++.so.6, of course).

The bad news is that the game still doesn't work. The only error message I'm getting now is that it can't find a configuration file:

```
$ LIBGL_DEBUG=verbose ./launcher 
libGL: OpenDriver: trying /usr/lib/i386-linux-gnu/dri/tls/r600_dri.so
libGL: OpenDriver: trying /usr/lib/i386-linux-gnu/dri/r600_dri.so
libGL: Can't open configuration file /etc/drirc: El fitxer o directori no existeix.
libGL: Can't open configuration file /home/marc/.drirc: El fitxer o directori no existeix.
libGL: Can't open configuration file /etc/drirc: El fitxer o directori no existeix.
libGL: Can't open configuration file /home/marc/.drirc: El fitxer o directori no existeix.

```


Any suggestions?

---

### Post by pardalet on 2012-11-10
Got it. :D

I just renamed all the libraries in the lib32 directory except libGLEW.so.1.5, so the game uses the newer versions on Ubuntu 12.10, and I finally got the game working.

---

### Post by Sableyes on 2012-11-11
Ooo Machinarium is on Android? Groovy! I fancy another play through of that ^^

---

### Post by Naddiseo on 2012-11-12
> **pardalet said:**
> Got it. :D

I just renamed all the libraries in the lib32 directory except libGLEW.so.1.5, so the game uses the newer versions on Ubuntu 12.10, and I finally got the game working.

Could you detail what exactly you did? Please and thank-you.

I don't see a libGLEW in the directory.

---

### Post by pardalet on 2012-11-12
> **Naddiseo said:**
> Could you detail what exactly you did? Please and thank-you.

I don't see a libGLEW in the directory.


Well, first of all I should've made clear that I installed the 32-bit deb package of Crayon Physics Deluxe from Humble Bundle for Andoid 4. Probably the 64-bit package has some other libraries, or maybe you should install the 32-bit libraries if that's your case:

```
$ sudo apt-get install ia32-libs-multiarch
```


Anyways, when I installed the game, I had all these files in the **/opt/CrayonPhysicsDeluxe/lib32 directory**:

```
$ cd /opt/CrayonPhysicsDeluxe/lib32/
$ ls -l
total 3,2M
-rw-r--r-- 1 root root 106K ago  3  2011 libgcc_s.so.1
-rw-r--r-- 1 root root 274K ago  3  2011 libGLEW.so.1.5
-rw-r--r-- 1 root root 122K ago  3  2011 libjpeg.so.62
-rw-r--r-- 1 root root 298K ago  3  2011 libmikmod.so.2
-rw-r--r-- 1 root root 492K ago  3  2011 libSDL-1.2.so.0
-rw-r--r-- 1 root root  46K ago  3  2011 libSDL_image-1.2.so.0
-rw-r--r-- 1 root root 179K ago  3  2011 libSDL_mixer-1.2.so.0
-rw-r--r-- 1 root root 241K ago  3  2011 libsmpeg-0.4.so.0
-rw-r--r-- 1 root root 909K ago  3  2011 libstdc++.so.6
-rw-r--r-- 1 root root 340K ago  3  2011 libtiff.so.4
-rw-r--r-- 1 root root  27K ago  3  2011 libvorbisfile.so.3
-rw-r--r-- 1 root root 165K ago  3  2011 libvorbis.so.0
```

I just renamed every file (adding "_BAK", for example), except **libGLEW.so.1.5** and that did the trick.

Good luck!

---

### Post by Naddiseo on 2012-11-13
@pardalet, thanks for the detailed reply. I've also sent an email to the humble bundle staff asking them to take a look at the deb packages.

---

### Post by pardalet on 2012-11-15
6 more games added to the Bundle: **[http://blog.humblebundle.com/post/35782746095/humble-bundle-for-android-4-turns-it-up-to-eleven](http://blog.humblebundle.com/post/35782746095/humble-bundle-for-android-4-turns-it-up-to-eleven)**

Basically, it's almost the whole Humble Bundle for Android #2 (which is great, because I didn't know the Humble Bundles back then      :P).

I've checked them all and happily there's no single library-related error on any of them (I downloaded the 32-bit deb package when available and the installer when not).

---

### Post by weasel fierce on 2012-11-16
Nice. If you guys haven't played Avadon, it's absolutely worth playing. Great RPG in the Baldurs Gate tradition

---

### Post by KBD20 on 2012-11-17
Is anyone else having this [issue with Splice]("https://docs.google.com/open?id=0B7A2NcqKEPUWSU5LaXRKSC0wMUk")? 
I looked at other images and it doesn’t seem to be meant to look like that. (Seems to have an extra layer of color)

---

### Post by R33D3M33R on 2012-11-18
It almost looks like some stereoscopic layer would be added so it would be 3D with proper glasses. Look in the control panel of your graphics card or in the game settings.

---

### Post by oldrocker99 on 2012-11-18
I picked up the bundle and then installed everything on the my Nexus 7 and on my 12.04 64-bit system. Everything works; I'll admit I haven't tried Machinarium on my PC due to prior problems I have had with that game, but it runs just fine on the Nexus.

Humble Bundles forever!

Posted from the Nexus, BTW.

---

