---
title: "Rainbow Pixelation on Windows?"
date: 2008-01-18
forum: Desktop Effects &amp; Customization
---

### Post by Bionic Apple on 2008-01-18
Starting a few days ago, my window decoration turns into this randomly or whenever I put my cursor over it:

[IMG]http://img26.picoodle.com/img/img26/4/1/18/f_Screenshotm_b7553f2.png[/IMG]

It might be my video card for two reasons: One, it is a 7900 GT, which is the second one I have had because the last one had a corrupted BIOS (free replacement).  Two, I overclocked it in Windows for a few minutes, however I doubt that matters in the least bit (but, the more information the better!).

Here is my Gnome settings:
-Emerald Theme Manager
--Vista Q theme
-Compiz window decoration blur
-Nvidia Driver 169.09 (configured by Envy)

---

### Post by bogdan_5844 on 2008-01-18
don't know much about overclocking,but the video card surely has nothing to do with this.
Does in the normal(not compiz,metacity)display manager show the same?
you can try by pressing Alt+F2 and typing in metacity --replace

---

### Post by Bionic Apple on 2008-01-18
As far as I can tell, there is no problem in Metacity.  Now I don't know if this is related, but a update failed for my x-server core 30 minutes ago (first update that has failed for me actually):

```
W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/x/xorg-server/xserver-xorg-core_1.3.0.0.dfsg-12ubuntu8.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/x/xorg-server/xserver-xorg-core_1.3.0.0.dfsg-12ubuntu8.1_i386.deb)
  403 Forbidden
```

[IMG]http://img33.picoodle.com/img/img33/4/1/18/f_Screenshotm_bb4d0c1.png[/IMG]

---

### Post by rune0077 on 2008-01-18
It might just be Emerald or even just the theme that is corrupted. Have you tried setting a different theme to see if it still happens?

---

### Post by FuturePilot on 2008-01-18
> **Bionic Apple said:**
> As far as I can tell, there is no problem in Metacity.  Now I don't know if this is related, but a update failed for my x-server core 30 minutes ago (first update that has failed for me actually):

```
W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/x/xorg-server/xserver-xorg-core_1.3.0.0.dfsg-12ubuntu8.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/x/xorg-server/xserver-xorg-core_1.3.0.0.dfsg-12ubuntu8.1_i386.deb)
  403 Forbidden
```

[IMG]http://img33.picoodle.com/img/img33/4/1/18/f_Screenshotm_bb4d0c1.png[/IMG]

Not related. The update was defective so it's been blocked. It's being worked on now.
Maybe try changing to a different Emerald theme and see if it still happens.

---

### Post by Bionic Apple on 2008-01-18
Thanks for the info about the update.  However, the problem still persists no matter which theme I choose.  All of the engines in Emerald have the same problem.

---

### Post by kryth on 2008-01-18
I used to have the same problem. What I did to fix it, was to rollback compiz to and older version. I got this problem after I updated compiz. Going back fixed it for me. Your milage may very.

---

### Post by Bionic Apple on 2008-01-18
Roll back compiz?  Would I do that through Synaptic?

If so, which option:

[IMG]http://img37.picoodle.com/img/img37/4/1/18/f_Screenshotm_f62219b.png[/IMG]

---

### Post by DaymItzJack on 2008-01-18
I have the 7900 GSKO and I get a weird window border mishap too:
[http://ubuntuforums.org/showthread.php?t=606276](http://ubuntuforums.org/showthread.php?t=606276)

---

### Post by Bionic Apple on 2008-01-19
I had that problem before, I believe I solved it with installing emerald as the theme decorator (however, that has caused this problem).

---

### Post by Bionic Apple on 2008-01-19
Nobody knows?

---

### Post by Bionic Apple on 2008-01-20
I reinstalled some of the Compiz packages, but the problem is still occurring.  I need some help!

---

### Post by rosegarden78 on 2008-01-20
You may consider your quest for eye candy to be the bane of your computer's existence.  For average systems with built-in graphics card, don't expect the moon.  The special effects cause headaches so bad you'll want to revert to XFCE like I did.

First - it looks liker you manually installed Beryl and Compiz yourself.  I was told the project has merged and was integrated into Ubuntu by default as of Gutsy 7.10.  But I see you're using Gutsy?  You need to remove all windows decoration that you installed yourself.

Try typing these command at the terminal:

sudo aptitude remove compiz
sudo aptitude remove beryl
sudo aptitude purge compiz
sudo aptitude purge beryl

Then go to your Display - Themes and choose a default theme like Human or Plastik.  Last check the Windows Decoration tab (eye-candy-o-mater) and select none.

If that doesn't work backup and clean install your system with a slow-burnt 4x Ubuntu CD.  Discs burnt at high speeds have shallow pits and cause errors despite perfect checksums.  Nice and easy does it every time.   Beryl and Compiz cannot co-exist on the same system.

---

### Post by rune0077 on 2008-01-20
With a 7900GT using the latest nvidia drivers, you should have no problem running Compiz (unless you're very low on RAM). I suspect (without knowing) that the real culprit is Emerald, and you should maybe try to reinstall it (if you haven't already).

Another thing, try to check your settings in Nvidia settings (it should be installed with Envy, and is located in Applications > System Tools > Nvidia settings). Try playing with the settings here, abd check the Sync to VBlank under OpenGL settings - if it's enabled, try disabling it, and vice versa (performance is better if it's turned off, but enabling it should prevent at least minor graphic corruptions). 

Other than that, I'm running out of ideas here.

---

### Post by Bionic Apple on 2008-01-20
I did what rune said and if it doesn't work, I will consider rosegarden's plan.  However, I do have a nice graphics card and I installed compiz fusion (and the advanced settings) through synaptic on a clean version of Gutsy.  Plus, I believe I did burn my Ubuntu Live cd at 4x.  However, I do have a copy of the official disk of Gutsy from Canonical, so there should be no problems if I do reinstall.

---

### Post by Bionic Apple on 2008-01-26
I think the "Sync to VBlank" setting did it.  No graphical glitches ever since I turned it on.  Thanks!

---

### Post by Bionic Apple on 2008-02-12
Update:  It started happening again  in Ubuntu.  But it gets even more interesting.  Even though I love Ubuntu, I am trying out other distributions.  Right now I am using OpenSUSE.  15 minutes after I installed Compiz Fusion, it started happening again in the new distribution!  I think this has to do with Compiz.  There is no other explanation.  How do I fix it?

---

### Post by Bionic Apple on 2008-02-13
Bump, plus I forgot to mention that I am running KDE in OpenSUSE.  So the problem really has nothing to do with Gnome/KDE or the distribution.  Now that I narrowed it down, any help?

---

### Post by Bionic Apple on 2008-02-25
Well, I am back on Ubuntu, and the problem resurfaced.  Basically, this is one tricky problem.  It has to do with my graphics card and emerald I think.  Just my opinion.

---

### Post by zdude on 2008-02-25
Try turning off button fade or adjusting the timing in Emerald. I believe this behavior was caused by the newer nvidia drivers.

---

### Post by Bionic Apple on 2008-02-26
Alright I will try that.  Also, I will see if installing the BRAND new drivers will help.  I have 169.09 and Envy won't update it, so I will see if a manual install of 169.12 will help.

---

### Post by foxxx428 on 2008-02-27
I couldn't get drivers working for either my x1650 or my x1650 pro so I ended up settling with my Nvidia 6200a and ran into this exact same problem. Luckily it was easily remedied. First, I uninstalled my Nvidia driver that I manually installed. Then in Synaptic, I searched nvidia and checked off nvidia-glx-new. After the install, in a terminal run ```
sudo nvidia-glx-config enable
``` and reboot. No more rainbow menus. Hope that helps.

---

### Post by Bionic Apple on 2008-03-06
I'm sorry, but that does not help.  Any more suggestions.  This is one weird bug...

---

### Post by Bionic Apple on 2008-03-09
Bum, bum, buuuuuuuuuuuuump.

---

### Post by Bionic Apple on 2008-03-10
No more help?  Honestly, I would try to find answers on my own, but I don't even know where to start but here.  None of the submitted solutions have worked and Google has shown me that I am the only one (that I know) with this problem.  If this happens in 8.04, I will be mad.  However, if you know the answer you can help me now and post.  Or maybe a Linux genius can walk me through a complete troubleshooting process to kill this bug once and for all.

---

### Post by zdude on 2008-03-12
So you tried going to Emerald Theme Manager and clicking on the Emerald Settings Tab and then UNcheck "Use Button Fade" and UNcheck "Use Button Pulse Fade" and it did not stop the rainbows? This fixes it for me using 169.04 and 169.09 nvidia drivers.

---

### Post by Bionic Apple on 2008-03-14
I never had pulse fade, but I did have fade.  I will see if that helps.

---

### Post by Bionic Apple on 2008-03-25
No help at all.  This is a pretty bad problem, as  I am running out of ideas.  Nothing so far works.  I have limited the problem to Emerald and perhaps the nVidia driver.  However, I did have the other problem mentioned earlier by Daym when I didn't have Emerald.  So perhaps the problem is not in Emerald, but exclusive to Compiz/nVidia.  Any more help would be appreciated.

Also, I found a Launchpad page for this (or similar) problem: [https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/186382](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/186382)

---

### Post by Bionic Apple on 2008-03-27
No more help?

---

### Post by Bionic Apple on 2008-04-05
Bump

---

