---
title: "Google Earth won't stay on"
date: 2009-02-23
forum: General Help
---

### Post by Dustin2128 on 2009-02-23
Whenever I start googe earth 5, it goes in about 5 seconds, you can see the earth and all, then it just cuts out. How do I fix it, do I need to reinstall from the bin?

---

### Post by mikewhatever on 2009-02-23
Try starting it from Terminal by typing googleearth. You'll probably get an error message, so post it here.

---

### Post by slowtrain on 2009-02-26
Well, here's what I get when I try to run googleearth from the command line (see below).  I'm running it on an amd64 machine w/ a 64 bit version of Ubuntu.  Looking over the forums, I've seen the suggestion to rename libcrypto.so.0.9.8.  I've tried that, but then get an error msg as follows: /usr/lib32/googleearth/googleearth-bin: symbol lookup error: /usr/lib32/googleearth/libssl.so.0.9.8: undefined symbol: EVP_idea_cbc.  Looks like libssl depends on libcrypto, which makes sense.  I guess I could try disabling it as well, but won't that leave my software open to intrusion?

peter@Ghost:/usr/lib32/googleearth$ /usr/bin/googleearth 
wx=0.312690, wy=0.328990, rx=0.639990, ry=0.330000
gx=0.210000, gy=0.710000, bx=0.149990, by=0.059990
wx=0.312690, wy=0.328990, rx=0.639990, ry=0.330000
gx=0.210000, gy=0.710000, bx=0.149990, by=0.059990
wx=0.312690, wy=0.328990, rx=0.639990, ry=0.330000
gx=0.210000, gy=0.710000, bx=0.149990, by=0.059990
Google Earth has caught signal 11.

Stacktrace from glibc:
  /usr/lib32/googleearth/googleearth-bin(__gxx_personality_v0+0x1e8) [0x8057fb4]
  /usr/lib32/googleearth/googleearth-bin [0x8058399]
  [0xf7fa9400]
  ./libbase.so(_ZN5earth8SpinLock4lockEj+0x22) [0xf7f633fc]
  ./libbase.so(_ZN5earth9LockGuardC1ERNS_8SpinLockE+0x1f) [0xf7f4927f]
  ./libnet.so(_ZN5earth3net18CurlHttpConnection13removeRequestEPNS0_15CurlHttpRequestE+0x25) [0xf7ae545b]
  ./libnet.so(_ZN5earth3net15CurlHttpRequest4stopEv+0x20) [0xf7ae54aa]
  ./libnet.so(_ZN5earth3net15CurlHttpRequestD0Ev+0x25) [0xf7ae54d7]
  ./libnet.so(_ZN5earth3net11HttpRequest5unrefEv+0x35) [0xf7add701]
  ./libnet.so(_ZN5earth6RefPtrINS_3net11HttpRequestEED1Ev+0x1e) [0xf7ad49c2]
  ./libnet.so(_ZN5earth3net14NetworkRequestD0Ev+0x28) [0xf7ad5a70]
  ./libbase.so(_ZN5earth8Referent8orphanedEv+0x10) [0xf7f3e4fe]
  ./libbase.so(_ZN5earth8Referent5unrefEv+0x17) [0xf7f651d5]
  ./libnet.so(_ZN5earth3net7FetcherD0Ev+0x42) [0xf7ad9332]
  ./libbase.so(_ZN5earth8Referent8orphanedEv+0x10) [0xf7f3e4fe]
  ./libbase.so(_ZN5earth8Referent5unrefEv+0x17) [0xf7f651d5]
  ./libwmsbase.so(_ZN5earth6RefPtrINS_3net7FetcherEEaSEPS2_+0x27) [0xf7b3a055]
  /usr/lib32/googleearth/libevll.so(_ZN5earth4evll18NetworkLinkFetcher9fetchDoneEv+0x890) [0xf293e486]
  /usr/lib32/googleearth/libevll.so(_ZN5earth4evll18NetworkLinkFetcher12ProcessWorkQEd+0x38) [0xf293e56a]
  /usr/lib32/googleearth/libevll.so(_ZN5earth4evll18GeobaseContextImpl8endFrameEd+0x1a) [0xf293e60c]
  /usr/lib32/googleearth/libevll.so(_ZN5earth4evll13VisualContext8endFrameEv+0x19b) [0xf2a3bae7]
  /usr/lib32/googleearth/libevll.so(_ZN5earth4evll13VisualContext4drawEbb+0xb2) [0xf2a3d9f8]
  /usr/lib32/googleearth/libevll.so(_ZN5earth4evll17RenderContextImpl4drawEv+0xa1) [0xf29f7b51]
  ./librender.so(_ZN12RenderWidget10paintEventEP11QPaintEvent+0x24) [0xf62d67d0]
  ./librender.so(_ZN5earth6render11RenderTimer4fireEv+0x14) [0xf62c360c]
  ./libbase.so(_ZN5earth5Timer10timerEventEP11QTimerEvent+0x31) [0xf7f3e9bb]
  /usr/lib32/googleearth/libqt-mt.so.3(_ZN7QObject5eventEP6QEvent+0x82) [0xf6db2fc2]
  /usr/lib32/googleearth/libqt-mt.so.3(_ZN12QApplication14internalNotifyEP7QObjectP6QEvent+0xa1) [0xf6d479a1]
  /usr/lib32/googleearth/libqt-mt.so.3(_ZN12QApplication6notifyEP7QObjectP6QEvent+0xef) [0xf6d484af]
  /usr/lib32/googleearth/libqt-mt.so.3(_ZN10QEventLoop14activateTimersEv+0x1ed) [0xf6d3b43d]
  /usr/lib32/googleearth/libqt-mt.so.3(_ZN10QEventLoop13processEventsEj+0x57b) [0xf6ced24b]
  /usr/lib32/googleearth/libqt-mt.so.3(_ZN10QEventLoop13processEventsEji+0x5a) [0xf6d615ea]
  /usr/lib32/googleearth/libqt-mt.so.3(_ZN12QApplication13processEventsEi+0x2c) [0xf6d4733c]
  /usr/lib32/googleearth/libqt-mt.so.3(_ZN12QApplication13processEventsEv+0x26) [0xf6d47376]
  /usr/lib32/googleearth/liblayer.so(_ZN5earth5layer11LayerWindow12onFirstEarthERKNS_4evll11UpdateEventE+0x8e) [0xefbf51ea]
  /usr/lib32/googleearth/libevll.so(_ZN5earth7EmitterINS_4evll14UpdateObserverENS1_11UpdateEventENS_19EmitterDefaultTraitIS2_S3_EEE8doNotifyEMS2_FvRKS3_ES8_+0xa7) [0xf2a00ed3]
  /usr/lib32/googleearth/libevll.so(_ZN5earth7EmitterINS_4evll14UpdateObserverENS1_11UpdateEventENS_19EmitterDefaultTraitIS2_S3_EEE6notifyEMS2_FvRKS3_ES8_b+0x3e) [0xf2a00f58]
  /usr/lib32/googleearth/libevll.so [0xf29fa31a]
  ./libbase.so(_ZN5earth5Timer10timerEventEP11QTimerEvent+0x31) [0xf7f3e9bb]
  /usr/lib32/googleearth/libqt-mt.so.3(_ZN7QObject5eventEP6QEvent+0x82) [0xf6db2fc2]
  /usr/lib32/googleearth/libqt-mt.so.3(_ZN12QApplication14internalNotifyEP7QObjectP6QEvent+0xa1) [0xf6d479a1]
  /usr/lib32/googleearth/libqt-mt.so.3(_ZN12QApplication6notifyEP7QObjectP6QEvent+0xef) [0xf6d484af]
  /usr/lib32/googleearth/libqt-mt.so.3(_ZN10QEventLoop14activateTimersEv+0x1ed) [0xf6d3b43d]
  /usr/lib32/googleearth/libqt-mt.so.3(_ZN10QEventLoop13processEventsEj+0x57b) [0xf6ced24b]
  /usr/lib32/googleearth/libqt-mt.so.3(_ZN10QEventLoop9enterLoopEv+0xc3) [0xf6d61503]
  /usr/lib32/googleearth/libqt-mt.so.3(_ZN10QEventLoop4execEv+0x26) [0xf6d613e6]
  /usr/lib32/googleearth/libqt-mt.so.3(_ZN12QApplication4execEv+0x1f) [0xf6d4739f]
  ./libgoogleearth.so(_ZN5earth6client11Application3runEv+0x24f) [0xf76e6821]
  /usr/lib32/googleearth/googleearth-bin(main+0x11f) [0x8058817]
  /lib32/libc.so.6(__libc_start_main+0xe5) [0xf6065685]
  /usr/lib32/googleearth/googleearth-bin(__gxx_personality_v0+0x75) [0x8057e41]




We apologize for the inconvenience, but Google Earth has crashed.
 This is a bug in the program, and should never happen under normal
 circumstances. A bug report and debugging data are now being written
 to this text file:

    /home/peterm/.googleearth/crashlogs/crashlog-1E729C0B.txt

This bug report will be sent to Google automatically next time you run
 Google Earth. Its data, which contains no personal information, will help
 us correct problems without bothering you further. If you would rather
 this info not be transmitted, please delete the above file before running
 the program again. If you want bug reports to NEVER be sent, remove the
 above 'crashlogs' directory's read/write permissions.

---

### Post by mikewhatever on 2009-02-26
There seems to be evidence that GE5 doesn't work on 64bit systems.
[http://blog.crox.net/archives/27-Getting-Google-Earth-for-linux-to-work-properly-on-amd64-x86_64-Gentoo-i915-module-do_wait-drmWaitVBlank-returned-1,-IRQs-dont-seem-to-be-working-correctly.-Try-running-with-LIBGL_THROTTLE_R.html](http://blog.crox.net/archives/27-Getting-Google-Earth-for-linux-to-work-properly-on-amd64-x86_64-Gentoo-i915-module-do_wait-drmWaitVBlank-returned-1,-IRQs-dont-seem-to-be-working-correctly.-Try-running-with-LIBGL_THROTTLE_R.html)

Obviously, the libcrypto problem is irrelevant in your case.

---

### Post by lindsay7 on 2009-02-26
I had the same problem. What I did was find the googleearth folder in Ubuntu.  There is an uninstall file there. Click it and uninstall version 5.0. I went to the googleearth site and downloaded the earlier version it is 4.3.2 or something. It works just fine.  I saw some threads last night when I was fooling around with this issue that talks about this being a bug with version 5 and it has something to do with the libcryto file being bad and needing to be ignored in the terminal commands.  Too much stuff for me.  So I will get by with the old version untill the bug is out of version 5.

---

### Post by habana on 2009-02-26
I have exactly the same problem as slowtrain - Google Earth has caught signal 11. I tried renaming the libcrypto file as mentioned in other posts but it did not work, the program would not even attempt to run in the absence of that file. My system is Intrepid, 32 bit.

---

### Post by geoffree on 2009-02-26
> **lindsay7 said:**
> I had the same problem. What I did was find the googleearth folder in Ubuntu.  There is an uninstall file there. Click it and uninstall version 5.0. I went to the googleearth site and downloaded the earlier version it is 4.3.2 or something. It works just fine.  I saw some threads last night when I was fooling around with this issue that talks about this being a bug with version 5 and it has something to do with the libcryto file being bad and needing to be ignored in the terminal commands.  Too much stuff for me.  So I will get by with the old version untill the bug is out of version 5.

I had the same problem. Looked in googleearth folder, found 'uninstall', but got error message: "command not found".  This was in the sub-dir for 'opt' and for 'google-earth'.  
Can you help me?

Geoffrey

---

### Post by geoffree on 2009-02-26
I've had similar crash problems with googleearth 5.  Searched for and found an uninstall file but got an error message saying "command not found".
Does anyone have an answer for me?  I will post a complete log but my problem is the same as what other posters have reported.

TIA

Geoffrey

---

### Post by slowtrain on 2009-02-26
Well, this is interesting:  About 1 in every 5 times I try running Google Earth, it works.  The rest of the time it crashes during initialization.  I wonder if this is true for others?

---

### Post by clemm on 2009-02-26
I dont know if this helps but im running 32 bit. Google begines to start up. soon as it goes full screen it closes.

---

### Post by lindsay7 on 2009-02-26
my google-earth folder with the uninstall file was under Hom/(my username/google-earth.  If you can not find it listed like that. I would look in "computer" under places in the menu bar. The look under "home". If you do not have a "username" folder, open up and look for th google earth folder in every place else under "home". There may be an easier way to do this but this worked for me. There will be an uninstall file listed there when you find it.  Go to the google Earth web site and download the older linux program. It is something like version 4.3.2 or something like that. It works just fine.

---

### Post by habana on 2009-02-26
Hi slowtrain. It's worked once for me in about ten attempts. When it did work it was not a pretty sight - I believe I may have to turn compiz fusion off.

---

### Post by slowtrain on 2009-02-28
Hi Habana:  That's unfortunate!  On my computer, when it does work, it works w/o a hitch, and I've made no changes to the software.  Rather odd that it does.

---

### Post by binbash on 2009-02-28
[http://www.ubuntu-inside.me/2009/02/howto-install-google-earth-50-beta-on.html](http://www.ubuntu-inside.me/2009/02/howto-install-google-earth-50-beta-on.html)

---

### Post by habana on 2009-03-01
Hi binbash. As you will read from earlier posts in this thread, that is not the solution.

---

### Post by Dustin2128 on 2009-03-08
> **lindsay7 said:**
> I had the same problem. What I did was find the googleearth folder in Ubuntu.  There is an uninstall file there. Click it and uninstall version 5.0. I went to the googleearth site and downloaded the earlier version it is 4.3.2 or something. It works just fine.  I saw some threads last night when I was fooling around with this issue that talks about this being a bug with version 5 and it has something to do with the libcryto file being bad and needing to be ignored in the terminal commands.  Too much stuff for me.  So I will get by with the old version untill the bug is out of version 5.
Well, I had earth 4.3, but I like 5 more because it's cool (used it on my windows rig) sorry I haven't been checking this thread for a while, and I have a 32 bit system

---

### Post by DeMus on 2009-03-08
This is what I get when installing GE5 on Hardy 64-bits:
jan@2-Quad:~$ ./GoogleEarthLinux.bin 
Verifying archive integrity... All good.
Uncompressing Google Earth for GNU/Linux 5.0.11337.1968..............................................................
loki_setup: Suspect size value for option option

loki_setup: Suspect size value for option option

loki_setup: Suspect size value for option option

Installing mimetypes...
Installing desktop menu entries...
Installing desktop icon...
Segmentation fault

The stupid thing is I re-installed Ubuntu and before I did that GE5 was running like clockwork. Just other things were screwed up.
Does anyone know what the messages mean?
I googled already but can't find a decent solution.

---

### Post by changhua on 2009-04-30
To get it working on Jaunty 64-bit I had to do the following:
1. Install Google Earth to /opt/google-earth via the standard download from the web page.
2. Install ia32-libs via Synaptic
3. Install lib32nss-mdns via Synaptic
4. cd /opt/google-earth
5. sudo mv libcrypto.so.0.9.8 libcrypto-backup 
6. sudo ln -s /usr/lib32/libcrypto.so.0.9.8
7. sudo mv libssl.so.0.9.8 libssl-backup
8. sudo ln -s /usr/lib32/libssl.so.0.9.8

After this I was able to run it and it seemed to work.  The about box shows it as:

Google Earth
5.0.11729.1014
Build Date
Apr 23, 2009
Build Time
12:29:46 pm
Renderer
OpenGL
Operating System
Linux (2.6.28.0)
Video Driver
NVIDIA Corporation
Max Texture Size
8192x8192
Server
kh.google.com

---

### Post by obi-nine on 2009-05-01
That worked for me on AMD64. Thanks Changhua!

---

### Post by Lunx on 2009-05-01
Seems there's several different issues in this thread, so my suggestions probably won't help in all cases. I had heaps of trouble getting GE to work (both with latest and earlier versions). I read various threads and posts on how to get it working and finally I've figured out how to get it up and running properly on my machine. First of all, I found that trying to install the package downloaded from Google doesn't work for me, it constantly crashes and throws up an error message, so now I make sure I enable the medibuntu repository and then download GE from there. Next thing is I turn off Compiz before trying to run GE (as mention earlier in this thread). This gets GE running, but it is very slow and jerky in how it reacts, but by going to the **View** menu in GE and disabling the** Atmosphere** effect, it then runs normally. This method works for me in both 8.10 and 9.04 

Follow this[ method for enabling Medibuntu]("https://help.ubuntu.com/community/Medibuntu") and you should have no problems. Make sure to run the first command (**Any** Ubuntu Release and keyring) and then the command that's specific for your distro release.

---

### Post by rijk.stofberg on 2009-05-05
I use Ubuntu Jaunty with a Nvidia card in TwinView mode. My GoogleEarth version 5, built with GoogleEarthLinux.bin (from synaptic) would fail with:
*[SIZE=2]libssl.so.0.9.8: undefined symbol: EVP_idea_cbc[/SIZE]*
Renaming the file /usr/lib/googleearth/libssl.so.0.9.8.removed-by-installer to /usr/lib/googleearth/libssl.so.0.9.8 solved this problem for me.
I found the solution at:
[https://bugs.launchpad.net/ubuntu/+source/googleearth-package/+bug/369471](https://bugs.launchpad.net/ubuntu/+source/googleearth-package/+bug/369471)

---

