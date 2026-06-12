---
title: "Compiz: windows lag on restore from minimize."
date: 2009-03-26
forum: Desktop Environments
---

### Post by sparrowkc on 2009-03-26
When I restore a minimized window from the taskbar, there is hesitation.  Sometimes the minimize animation happens after the pause, and sometimes windows just appear in their restore positions without the animation occurring.   I suspect the problem is that offscreen windows are not being rendered constantly, and have to be redrawn before the animation can occur.  If I'm right about the problem, is there a way to force compiz to draw minimized windows?  fglrx and ATI mobility radeon HD 3450 If that helps.

I'm running an on an install that started with a jaunty daily build a few days ago.  If this disqualifies me from getting help with a minor issue, please feel free to just tell me to wait for the final release.

---

### Post by stugatzz on 2009-03-26
I was having the same problem. Here's what worked for me:

1. Go into Restricted Drivers and disable Ubuntu's ATI proprietary driver. 

2. Go to [ATI's website]("http://support.amd.com/us/gpudownload/Pages/index.aspx") and download the latest linux driver for your card. It will be a .run file

3. Run "sudo apt-get install dpkg-dev debhelper libstdc++5 dkms build-essential cdbs fakeroot" to make sure you have all the required packages

4. Make the .run file executable

5. In a terminal, run "./ati-driver-installer<VERSION YOU HAVE>-x86.x86_64.run --buildpkg Ubuntu/9.<whatever version Ubuntu your running>" . If you need to, you can do --listpkg instead of --buildpkg to see what the available Ubuntu versions are included. 

6. It will output many .deb files into the directory the .run file was in. You will only need the following 2...

7. "sudo dpkg -i fglrx-kernel-source_<VERSION YOU HAVE>.deb"

8. "sudo dpkg -i xorg-driver-fglrx_<VERSION YOU HAVE>.deb"

9. Then run "sudo aticonfig --initial" to create a new xorg.conf

10. Reboot

You should be good to go now. You'll be using the latest drivers from ATI instead of the one from Ubuntu's rep. I don't know what chipset you have but I have the x1250 and it worked perfect for me. Good luck.

---

### Post by MikeWanDo on 2009-04-16
I'm using a Radeon HD 3450 and am experiencing the same lag when using the fglrx drivers from the Ubuntu repositories. I tried stugatzz's suggestion and everything seemed to work up, but when I rebooted I was greeted with an error and had to go back to a default Xorg configuration in order to boot. Has anyone one else found a way to fix this and still have Compiz work?

---

### Post by lavinog on 2009-04-16
> **stugatzz said:**
> I was having the same problem. Here's what worked for me:
You should be good to go now. You'll be using the latest drivers from ATI instead of the one from Ubuntu's rep. I don't know what chipset you have but I have the x1250 and it worked perfect for me. Good luck.

The latest driver (9-3) will not work with jaunty.
Unfortunately the Jaunty driver is a hacked version of 9-2.5, 9-3 has a major improvement in performance with compiz, but isn't compatible with xserver1.6
The version packaged with jaunty was a hack to make it compatible, but doesn't have the compiz improvements.
I think 9-4 should be available sometime next week and it should be compatible

---

### Post by lavinog on 2009-04-18
Good news everyone!
the new ati driver was released yesterday
I am downloading it now.
[http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)

---

### Post by lavinog on 2009-04-18
It seems to work, no hesitation here. I did get some black artifacts after the first restore from minimize, after scrolling they went away. subsequent restoring I could not get any artifacts.

UPDATE: There seems to be a serious bug with the 9-4 driver and compiz. Occasionally I get a kernel panic when playing videos and resizing the screen. I am going to look further into this, but it looks like others are experiencing the same issue.
I would recommend not using desktop effects in the meantime.

On a similar note, many people are claiming that they got a performance increase...I have noticed that there seems to be alot of bugs in the versions that have these performance increases.

---

### Post by MikeWanDo on 2009-04-26
Thanks for the update. I tried d/ling the new version and installing it per stugatzz's instructions and it booted successfully without any xorg errors. I also experience crashing when using compiz and resizing videos, however without compiz everything seems to work perfectly. Thanks for posting about the update, please post if a fix is found for compiz and the fglrx drivers.

---

### Post by sekura on 2009-05-20
Workaround for the video-resize-fullscreen crashing over here:  [http://ubuntuforums.org/showthread.php?t=113704]("http://ubuntuforums.org/showthread.php?t=1137048")

Hope this helps :)

---

### Post by sparrowkc on 2009-07-02
I've found a solution for the lagginess.  Our problem is described in this bug:
[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/351186?comments=all]("https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/351186?comments=all")

In the comments there is a patch for X that was removed to prevent graphics corruption mostly for Intel chips.  Re-applying that patch solved my problem.

Someone set up a repo with the patched X, so all you have to do is add it, do an update, and restart!
[https://edge.launchpad.net/~ubuntu-x-swat/+archive/xserver-no-backfill]("https://edge.launchpad.net/~ubuntu-x-swat/+archive/xserver-no-backfill")

Again, video playback problems are apparently fixed by changing the video output plug in to no xv (enter 'gstreamer-properties' in a terminal.)

:guitar::guitar::guitar::guitar:

---

### Post by japher on 2009-07-12
sparrowkc - you are awesome! (and of course so is bryceharrington, the uploader of this package) :p

Thanks so much for posting this back to the forum. Problems fixed and I'm now enjoying a smooth minimize/maximize/restore action!

---

### Post by julrich on 2009-07-14
> **japher said:**
> sparrowkc - you are awesome! (and of course so is bryceharrington, the uploader of this package) :p

Thanks so much for posting this back to the forum. Problems fixed and I'm now enjoying a smooth minimize/maximize/restore action!

Wow!  For the first time in 3 years, I can enable Desktop Effects.  This is outstanding.  Resizing konsole, and all windows is as smooth as when effects are turned off.

What happens when something gets upgraded in the main?  Will this patch get lost??? I'm pretty stoked about this, but hoping all doesn't get lost with future upgrades.

---

### Post by Kejlsn on 2009-07-19
> **sparrowkc said:**
> I've found a solution for the lagginess.  Our problem is described in this bug:
[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/351186?comments=all](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/351186?comments=all)

In the comments there is a patch for X that was removed to prevent graphics corruption mostly for Intel chips.  Re-applying that patch solved my problem.

Someone set up a repo with the patched X, so all you have to do is add it, do an update, and restart!
[https://edge.launchpad.net/~ubuntu-x-swat/+archive/xserver-no-backfill]("https://edge.launchpad.net/%7Eubuntu-x-swat/+archive/xserver-no-backfill")

Again, video playback problems are apparently fixed by changing the video output plug in to no xv (enter 'gstreamer-properties' in a terminal.)

:guitar::guitar::guitar::guitar:

OMG. Thank you soo much for that post!
I thought I was the only one in the world who had this problems with window lagg!
Now the whole Ubuntu experience runs soooo smooth :D

---

### Post by ZaHACKieL on 2009-07-24
I tried the latest ATI drivers (version 9-7) and they didn't fix the lag. So, now I'm going to try that patch solution but I want to know if anyone has had any secondary problems after applying that patch. Thanx!

---

### Post by furnace on 2009-10-13
This post has been here for far too long without any follow-ups!

I'm using 9.04 and whatever drivers the System -> Administration -> Hardware Drivers tool provides (side note: how do I find out what version these drivers are?).

It's a Dell Studio laptop with an ATI HD 3650 (or something like that).

I was getting unbearably slow performance issues with Compiz - but appling that patch ([https://edge.launchpad.net/~ubuntu-x-swat/+archive/xserver-no-backfill](https://edge.launchpad.net/~ubuntu-x-swat/+archive/xserver-no-backfill) - click on 'Not using Ubuntu 9.10' for 9.04 instructions) fixed the lag!

But video crashing is a separate issue - PageMaster86's suggestion fixes this:

> Go to terminal:
gstreamer-properties

a box will pop up, click the video tab
under output, choose "no xv" option for the plugin 

Awesome :) Ubuntu on my laptop no longer sucks!

I do think the moral of the story though, is just get an nvida card if possible. I have always had problems of some sort with ATI - previously to this I had a dual-screen ATI desktop and it just wouldn't conifgure properly, stuck an nvidia gfx card in and all was good. Shame we can't just stick new gfx cards in laptops so easily, huh? :P

It would be great to get confirmation from a 9.10 user that this patch still works.

---

### Post by lavinog on 2009-10-13
> **furnace said:**
> (side note: how do I find out what version these drivers are?).

9.04 comes with a beta version of the 9-4.  9-9 is the current version available from ati.

---

### Post by julrich on 2009-11-03
I wonder if there is any hope for 9.10, as there isn't a patch out for it yet.

---

### Post by mrboojive on 2009-11-03
There is another PPA that has a 9.10 version of X server with no backfill: [https://launchpad.net/~launchpad-weyland/+archive/xserver-nobackfill/](https://launchpad.net/~launchpad-weyland/+archive/xserver-nobackfill/)

See this thread for more info:
[http://ubuntuforums.org/showpost.php?p=8114637&postcount=51](http://ubuntuforums.org/showpost.php?p=8114637&postcount=51)

---

### Post by julrich on 2009-11-04
Thank you!

---

### Post by radec on 2009-11-04
> **mrboojive said:**
> There is another PPA that has a 9.10 version of X server with no backfill: [https://launchpad.net/~launchpad-weyland/+archive/xserver-nobackfill/]("https://launchpad.net/%7Elaunchpad-weyland/+archive/xserver-nobackfill/")

See this thread for more info:
[http://ubuntuforums.org/showpost.php?p=8114637&postcount=51](http://ubuntuforums.org/showpost.php?p=8114637&postcount=51)


that worked perfectly on a lenovo t400 with an ati mobility 3470.

thanks a bunch

---

### Post by furnace on 2009-11-06
I am guessing that I will have to remove the old PPA before upgrading to 9.10, then use the new one?

Or will the upgrade to 9.10 replace my current patched version of x-server, then I just use this new PPA?

edit; to keep everyone updated, the upgrade to 9.10 replaces x-server, so you just need to install the 9.10 patched version as per radec's post

---

### Post by asn_knight on 2010-04-04
@radec Thanks man! U r a saviour!! No more lags now!!!

Enjoy
--asn_knight--

---

### Post by sparrowkc on 2010-05-21
Just some updates...
Lucid was release a few weeks ago, and the lag problem still exists with the proprietary drivers.  The PPA given earlier in this thread for karmic/9.10 looks to have been updated for Lucid/10.04.

I haven't tried that though, because the radeon driver seems to have added support for 3d acceleration on my graphics card (ATI Technologies Inc Mobility Radeon HD 3400 Series)!  The performance is perfectly acceptable for compiz, there is less tearing, I don't ever see garbage in new windows like I did with fglrx, and I feel like my system is more stable in general.

To whatever team made that happen for me, thanks!

---

### Post by jeffltw on 2010-06-25
> **mrboojive said:**
> There is another PPA that has a 9.10 version of X server with no backfill: [https://launchpad.net/~launchpad-weyland/+archive/xserver-nobackfill/]("https://launchpad.net/%7Elaunchpad-weyland/+archive/xserver-nobackfill/")

See this thread for more info:
[http://ubuntuforums.org/showpost.php?p=8114637&postcount=51](http://ubuntuforums.org/showpost.php?p=8114637&postcount=51)

I patched it before when karmic was just released but the lag issue came  back again after some updates. I tried this and it worked perfectly.

Thanks

---

