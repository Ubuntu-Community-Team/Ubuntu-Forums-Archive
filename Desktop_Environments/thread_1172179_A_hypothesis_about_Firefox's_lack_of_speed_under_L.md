---
title: "A hypothesis about Firefox's lack of speed under Linux"
date: 2009-05-28
forum: Desktop Environments
---

### Post by extigyro on 2009-05-28
I have digged a lot of Internet forums and there's no solution.

I've read that the slowness is caused by IPv6, DNSes configuration, Adobe Flash plugin and so on.

There is some truth in that propositions, i have to say. 

According to me the main reason is the "not-so-good" version of Adobe Flash for Linux. The second reason is the "not-good-enough" version of JRE (Java Runtime Environment) for Linux. These two are not just enough optimized.

I suppose there are many other reason which i'm not aware of.


I think that the Linux Mint Team maybe has found to some extent a solution for this particular problem. The speed of rendering is very impressive. Maybe it's the way Firefox is built:

Configure arguments
--build=i486-linux-gnu --prefix=/usr '--includedir=${prefix}/include' '--mandir=${prefix}/share/man' '--infodir=${prefix}/share/info' --sysconfdir=/etc --localstatedir=/var '--libexecdir=${prefix}/lib/xulrunner-1.9' --disable-maintainer-mode --disable-dependency-tracking --srcdir=. --enable-system-cairo --enable-system-sqlite --with-system-nspr --with-system-nss --enable-application=xulrunner --enable-extensions=xml-rpc,venkman,inspector,gnomevfs,cview,tasks,reporter,python/xpcom --enable-webservices --enable-safe-browsing --with-default-mozilla-five-home=/usr/lib/xulrunner-1.9.0.10 --enable-startup-notification --with-user-appdir=.mozilla --without-system-jpeg --with-system-zlib=/usr --with-system-bz2=/usr --enable-system-hunspell --disable-javaxpcom --disable-crashreporter --disable-elf-dynstr-gc --disable-installer --disable-strip --disable-strip-libs --disable-install-strip --disable-tests --disable-mochitest --disable-updater --enable-optimize --with-distribution-id=com.ubuntu 

I am not quite sure.

The Flash banners are shown right after the text and pictures are shown on the page . And that causes pages to be shown (the interesting part of them) much faster and with less lag.

I want to share my observations because I'm very irritated by the slow rendering of Firefox.

I've also tested Firefox under Wine and even with emulation the Windows version is considerably faster. Pff...

---

### Post by timcredible on 2009-05-28
yeah, firefox on linux takes a lot of cpu also for no good reason.  looks to me like flash is the real problem, so i installed the firefox add-on 'flashblock', which doesn't download or play any flash on a webpage unless you click on the little icon.  makes firefox much quicker since most of the flash on webpages these days are ads.

---

### Post by extigyro on 2009-05-28
I used Flashblock and it betters the speed but AFTER THE PAGE IS LOADED (because it disables only the autostart of embedded media). It betters the scrolling speed and very little the rendering speed (not enough).

Now i use "Stop Autoplay", it seems that it's a little better than Flashblock. However, the difference is very insignificant.

---

### Post by j7%&lt;RmUg on 2009-05-28
I agree with you about java being fairly bad on ubuntu. But i have a 256k connection to the net (which is very slow) and most pages load in an acceptable time in firefox. (but then again i do have a 3.2Ghz P4 and 1GB of RAM)

Have you thought that maybe its your hardware thats causing it?

It is not always the software that is the problem, that is just one possibility.

---

### Post by extigyro on 2009-05-28
> **nisshh said:**
> 
It is not always the software that is the problem, that is just one possibility.
You bet! ;)

I have fairly advanced knowledge about computer hardware. I do know that.

Intel Core 2 Duo T7400
4 GB DDR2
Amd.Ati Mobility X1600 256 MB gddr3 (r5xx family... RV515 if you wanna be precise)
...

The network speed... [http://www.speedtest.net/result/483300274.png](http://www.speedtest.net/result/483300274.png) for 13 Euros monthly.

Software (some package versions): 

the latest open-source radeon driver from GIT Repo (radeon_drv or ati_drv, version 6.12.2);
X.org - ver. 1.6.2 RC1;
Acceleration Method - EXA with Option "DynamicClocks" enabled.

---

### Post by extigyro on 2009-06-01
I've made some more testing and I do really consider now that the main reason is only the Adobe Flash Plug-in.

I'm using Ubuntu Jaunty 64-bit edition, fully updated and I manually installed the 64-bit version of adobe flash plug-in (in this way there is no need of ndiswrapper and any kind of emulation). 

Now there is very little lag (almost insignificant) when rendering pages with some animation content. However, if you want to watch clips in [http://www.youtube.com/](http://www.youtube.com/) in full screen, you will probably notice that the video is lagging behind the sound a little.

Conclusion: Mozilla Foundation is actually doing its job pretty well. The most part of the speed problems under Linux IS NOT the quality of the Mozilla's program code but the third-party software like the Adobe Flash Player. The 64-bit version of Adobe Flash Plug-in is definitely good advancement but there is some more hard work to be done before we can fully utilize it.

Now I really realize why the Free Software Foundation rates so high the development of open-source free and fast GNU program to play flash content.

[http://www.fsf.org/campaigns/priority.html#gnash](http://www.fsf.org/campaigns/priority.html#gnash)

Have a nice day, dudes!

---

### Post by extigyro on 2009-06-20
Actually there are two more things I've discovered.

The second main cause for the lack of speed under Linux is the openjdk plug-in for Firefox (package name: icedtea6-plugin).

After the removal of this package and afterwards installing the original Sun Java 6 plug-in (package name: sun-java6-plugin), there is considerable and very noticeable growth of speed (mostly when scrolling through a heavy web-page).

The third reason (maybe!) is the too conservative speed configuration of Firefox under Linux. After some more tweaking in "about:config", 

now I can truly admit that I'm very contented with the results.

---

