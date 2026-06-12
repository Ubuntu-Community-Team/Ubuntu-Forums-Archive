---
title: "Rotate one monitor with Nvidia and Compiz (Natty, Unity)"
date: 2011-10-11
forum: Desktop Environments
---

### Post by tamashumi on 2011-10-11
Hi,

1st of all I'm using two monitors:
[LIST=1]
[*]main one 24" 1920x1200
[*]additional one 19" 1280x1024 or rather 1024x1280 as it's rotated 90 degree on pivot. It's on the left side from main monitor.
[/LIST]

I was able to set up dual head config with ATI Radeon HD 4870 using proprietary driver. All was fine despite small bugs. 3D, compiz, unity, etc worked. I could drag windows between monitors and of course the 2nd monitor was rotated on pivot 90 degree with correct screen display (I could've setup this by clicking in Catalyst Control Center which comes with ATI's proprietary driver).

I've bough couple of days ago a GTX 560 Ti graphic card. Here the problems had started. There is no simple way for setup screen rotation under nvidia-settings panel which comes with proprietary driver. That's bad.
I googled and found it's not possible with Nvidia TwinView at all for single monitor. Here please correct me if anything changed in that matter.
One can try to use two separate X screens config with outdated Xinerama thingy but here is a catch. It breaks compiz :/
I tried this and indeed compiz was broken. Check the screenshot, [CLICK]("http://upload.metakmin.net/xinerama_fails.jpg"). Arrows point what was actually rendered on each monitor. The left monitor hadn't been rotated yet so it's horizontal too.

Simple question is: _can it be configured properly so I could rotate only one screen and don't loose desktop effects?_

I always thought and heard that Nvidia has better support than ATI for Linux. I believe this rumor does not apply anymore. If no solution can be found during this week Nvidia will go back to the shop giving place for some comparable GPU from ATI's. Which's a bit pity as the card I got is made solid and works coll and quiet even under heave load (windows games).

---

### Post by soft_kitten on 2012-06-23
I apologise for the necro, but I would like to present a solution.

The answer is to upgrade to the very latest nvidia beta drivers. When I had this problem I was stuck with 295. We need 302. 

First, make sure that in your Additional Drivers app you have  version current selected. If you are using post-release update you won't  use 302, you will use 295. Strange but true.

You can get 302 from the nvidia website (they also have x64)

[http://www.nvidia.com/object/linux-display-ia32-302.07-driver.html](http://www.nvidia.com/object/linux-display-ia32-302.07-driver.html) 

or using this repo (which I prefer)

[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates/]("https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates/")

Use the repo to upgrade to 302. I'm not sure if you need to restart after this, but thats what I did. maybe kill x is enough. I don't know.

Make sure in your nvidia-settings you are using Twinview without xinerama.
Then in the displays view of your control panel (not nvidia-settings), you can select each monitor individually and rotate one without affecting the others.

---

