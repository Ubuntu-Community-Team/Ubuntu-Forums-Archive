---
title: "gnome-shell abnormal cpu usage on a fresh 12.04 installation"
date: 2012-04-27
forum: Desktop Environments
---

### Post by stefo11 on 2012-04-27
Hi all,
i've just installed ubuntu 12.04 and, not being a unity fan, i've installed gnome (a noobish "sudo apt-get install gnome"). 
The system is quite fresh, i've just installed a browser (chromium) and my videocard's driver (from the official ati site).
When i try to use gnome as desktom enviroment, the process "gnome-shell" uses a huge amount of cpu, boosting the temperature. In an idle situation the cpu usage of "gnome-shell" is around 15%, with even a browser opened it rises to almost 100%.
I've surfed google searching for clues but, though many people has my same problem there are no solutions that works for me.
Any idea on how can i fix it? I'm currently using unity since with that cpu usage the gnome enviroment is almost unusable (the classic one works just fine, but it's hugly:P)

Thanks!

---

### Post by Caiux on 2012-05-01
Same problem here after upgrading to Precise (before I was using classic Gnome). Gnome-shell shows 10-15% cpu load when idle, jumps to 30-40% when the cursor is moving, and is constantly between 70 and 85% when Totem is playing some web streaming (note that Totem takes just 5%). Installed on a iMac with ATI proprietary drivers.

---

### Post by Jumbs on 2012-05-02
Similar here.
Gnome shell hovers in the 10-60% range while nothing is open or doing.

I disabled all gnome3 extensions to debug, but no change.

I have the ATI proprietary driver enabled.

---

### Post by Jumbs on 2012-05-02
> **Jumbs said:**
> Similar here.
Gnome shell hovers in the 10-60% range while nothing is open or doing.

I disabled all gnome3 extensions to debug, but no change.

I have the ATI proprietary driver enabled.

Also tried linking to the Gnome 3 PPA ppa:gnome3-team/gnome3, no results.


Is it possible that that the ATI driver is not really in use? any way to check?

---

### Post by Caiux on 2012-05-03
I removed the ATI proprietary drivers and everything is working fine now, so my conclusion is that the ATI drivers are somehow interfering with gnome-shell.

I previously installed the ATI drivers from Ubuntu System Settings (the standard ones, not the post-release which was not installing). It may be worth trying to install the latest version from ATI - last time I tried their package it was not installing. More news if I manage to find some time to experiment with this.

---

### Post by Oblivio on 2012-05-03
I have not been able to install the "Post release" driver option and I tried a few times/distro ever since 10.04. Will try disabling them though. Though I have not tried gnome-shell without the ati drivers. Will test. Though between Unity and Gnome shell efficiency... both are annoyingly loud and power costly.

I went into the settings to check them out and sure enough ```
cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
``` returned a "performance" value (on both cores) that I can not change to "ondemand". When changing by "gsku gedit", "sudo gedit" it says something about not finding a backup and for some reason "save anyway" does nothing.

 cpufreq-indicator is also useless because it automatically resets to performance after a few seconds of anything. If I use any of the numbered values (for me they are 0,5; 1,1; 2,2GHz per core) to keep cpu speed at it sets to the highest number as if it doesn't even see the lower ones.

---

### Post by Jumbs on 2012-05-03
I have never had any luck with the post release drivers.

How did you remove the ATI package? I don't even know the package name.

My desktop is Nvidia, however i have not been home to upgrade and test that.

---

### Post by Jumbs on 2012-05-03
> **Oblivio said:**
> I have not been able to install the "Post release" driver option and I tried a few times/distro ever since 10.04. Will try disabling them though. Though I have not tried gnome-shell without the ati drivers. Will test. Though between Unity and Gnome shell efficiency... both are annoyingly loud and power costly.

I went into the settings to check them out and sure enough ```
cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
``` returned a "performance" value (on both cores) that I can not change to "ondemand". When changing by "gsku gedit", "sudo gedit" it says something about not finding a backup and for some reason "save anyway" does nothing.

 cpufreq-indicator is also useless because it automatically resets to performance after a few seconds of anything. If I use any of the numbered values (for me they are 0,5; 1,1; 2,2GHz per core) to keep cpu speed at it sets to the highest number as if it doesn't even see the lower ones.

Confirmed. I removed the ATI driver, and it seems to have calmed the runaway gnome-shell process.

QUESTION: I have been using ubuntu for years, however installing the video drivers has always been a do-then-forget-about step. What is the effect of not having the driver?
On windows, no driver would suck, however on ubuntu, does it use an open source alternative?

QUESTION: Has anyone seen this with nvidia?

---

### Post by Caiux on 2012-05-04
> **Jumbs said:**
> I have never had any luck with the post release drivers.

How did you remove the ATI package? I don't even know the package name.

My desktop is Nvidia, however i have not been home to upgrade and test that.

If you installed the ATI drivers through System Settings --> Additional Drivers you can just deactivate them the same way, or if you used the Ubuntu packages just uninstall fglrx and fglrx-amdcccle. After that you need to reboot (if you just  log out the system may freeze).

---

### Post by Caiux on 2012-05-04
> **Jumbs said:**
> QUESTION: I have been using ubuntu for years, however installing the video drivers has always been a do-then-forget-about step. What is the effect of not having the driver?
On windows, no driver would suck, however on ubuntu, does it use an open source alternative?

Xorg supports several ATI graphics cards: [http://www.x.org/releases/X11R7.6/doc/man/man4/](http://www.x.org/releases/X11R7.6/doc/man/man4/)

Under RadeonHD I've found my HD 2600.You can find supported NVidia cards here: [http://www.x.org/releases/X11R7.6/doc/man/man4/nv.4.xhtml](http://www.x.org/releases/X11R7.6/doc/man/man4/nv.4.xhtml)

---

### Post by Jumbs on 2012-05-05
> **Caiux said:**
> Xorg supports several ATI graphics cards: [http://www.x.org/releases/X11R7.6/doc/man/man4/](http://www.x.org/releases/X11R7.6/doc/man/man4/)

Under RadeonHD I've found my HD 2600.You can find supported NVidia cards here: [http://www.x.org/releases/X11R7.6/doc/man/man4/nv.4.xhtml](http://www.x.org/releases/X11R7.6/doc/man/man4/nv.4.xhtml)

6400 M, seems ok, though. Good enough for laptop usage
Hope its ok on my Nvidia, will have to check when i am done traveling, thats my main computer

---

### Post by r_mano on 2012-05-19
This is basically a me-too. Ati radeon 2400HD. I had a question on askubuntu, will test next week by disabling ati drivers. 

[http://askubuntu.com/questions/135009/failing-gnome-shell-theme-where-can-i-find-errors-configuration-apart-from-gnom/137765#comment165853_137765](http://askubuntu.com/questions/135009/failing-gnome-shell-theme-where-can-i-find-errors-configuration-apart-from-gnom/137765#comment165853_137765)

---

### Post by LacerdaPT on 2012-07-02
Hi!

I was having this problem for quite a while.
I found this page: [http://askubuntu.com/questions/62808/ati-incompatible-with-gnome-shell](http://askubuntu.com/questions/62808/ati-incompatible-with-gnome-shell)

Check out the first answer, from Kashew. Basically installing a recent version of the drivers (in my case 12.6) solves the problem. 

I have just installed this, but as far as I could test it, the cpu usage from the process "gnome-shell" doesn't go up like crazy with anything. I used to have this problem with videos and it is all gone: youtube, 720p, no video tearing. 

Try this. As i said I have just installed the new drivers, 20 minutes ago, but it seems to be the solution :D

Cheers

---

### Post by Etrage on 2012-08-01
I have the same story with AMD Radeon HD 6800.

Gnome-shell, compiz, Unity 3D, all whack 60%+ cpu while idle. Basically, any compositing window manager. Unity 2D runs ok.

The latest (12.6) drivers haven't helped a bit. Seems the compositing is still done using CPU, not GPU.

I don't even want to remember the story when fonts in gnome-shell were garbled ([http://askubuntu.com/questions/62808/ati-incompatible-with-gnome-shell](http://askubuntu.com/questions/62808/ati-incompatible-with-gnome-shell)).

Basically, my $300 AMD Radeon video card turned up to be a useless piece of ****. I will never buy any of the AMD/ATI hardware again.

---

### Post by webe123 on 2012-08-01
I have been using Ubuntu since version 6 or 7and have loved it. But with the push to Unity, I feel I have been slowly pushed away. Unity maybe fine for some, but I just can't get to where I feel comfortable with it. I also have huge issues with the lack of support for my newer ATI 6790 card. If, and I should say when since I have redone this now at least 6 times... no exaggeration.., I perform a clean install, the screen goes blank and will not return. I have to install my older ATI 4850 card to keep a display long enough to load it. Then after it completes the load, I load the latest drivers from ATI, I remove the old card and re-insert the newer 6790. What a pain. Then to add insult to injury, the screens get real weird with multiple panel bars appearing at both the top and bottom of the screen that will not go away until I switch from Gnome back to Unity. But then it keeps telling that an error has occurred and do you wish to send. I've done it a few times but now I just hit skip. But it too has started crashing regularly and has become very unreliable. So I have searched and found that most flavors of Linux do not take well to ATI. But I have found another that I used for many years before I discovered Ubuntu and am now using it. I know we need to change with the times but becoming like macrocrash is not the way either. I don't like having to reboot my machine because the operating system decides to take a break on it's own. I'll check back and see what the future brings.

---

### Post by sundman on 2012-12-14
Just like Jumbs, gnome-shell was running really high on the cpu with the fglrx driver but is now running smooth and keeping the load on a reasonable level with the ati driver.

As always [http://wiki.cchtml.com/index.php/Main_Page]("http://wiki.cchtml.com/index.php/Main_Page") has all you need to know for (de|re)installation.

---

### Post by sundman on 2013-08-26
I got fed up with gnome-shell, too - it did not suite big screens and multiple desktops. My choice has been Cairo which has lots of settings and visual appearances but does it's job well - staying out of the way.

---

