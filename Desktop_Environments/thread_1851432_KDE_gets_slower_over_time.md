---
title: "KDE gets slower over time"
date: 2011-09-28
forum: Desktop Environments
---

### Post by sirjeppe on 2011-09-28
I have a weird problem where my Kubuntu gets slower and slower over time.

Scrolling in different applications, flipping between desktop workspaces, even switching between tabs in my browser gets slower. The slowdown stops after a while when it's "slow enough", but when it is this slow, you can even see when the screen is redrawn when switching tab in the browser and see how windows slowly appears when switching desktop workspace.

I have found a quick fix for it which is to toggle (Resume -> Suspend) the desktop effects. But after a while it gets slow again, and I need to toggle the setting again to get back the performance that my computer SHOULD be able to give me (Core2 Q9400@2.6GHz, 4gig RAM, NVIDIA Quadro NVS290).

The memory usage is stable and less than half of my physical installed memory, and there is no CPU hogging process running on any of my cores.

The machine is a one week old installation of Kubuntu 11.04, and I have disabled the nouveau drivers and installed the latest NVIDIA drivers from their site.

Any idea on how I can find out what is wrong or any quick fix?

Is this a known issue?

---

### Post by sumski on 2011-09-28
[http://forum.kde.org/viewtopic.php?f=17&t=90923](http://forum.kde.org/viewtopic.php?f=17&t=90923)

[https://bugs.kde.org/show_bug.cgi?id=226182#c14](https://bugs.kde.org/show_bug.cgi?id=226182#c14)

---

### Post by sirjeppe on 2011-09-28
Thanks...

But it doesn't sound like that bug is the same as I have though? However, the video from the first post in the first link shows kind of what I experience.

But are they related?

---

### Post by sumski on 2011-09-28
Well, try it and see if it helps (i don't have nvidia so can't help you there :) )

---

### Post by sirjeppe on 2011-09-28
> **sumski said:**
> Well, try it and see if it helps (i don't have nvidia so can't help you there :) )

Yupp - I will try the UseEvents=true in xorg.conf and see if it helps :) Then at least I would not have to do something everytime I reboot my computer.

Thank you for the feedback, sumski!

---

### Post by schnelle on 2011-09-29
Try graphics system raster. Install kde-config-qt-graphicssystem package, then go to system settings>qt graphics system and change it to raster. Reboot system and see if it helps :)

Raster makes huge difference on my system.

---

### Post by schnelle on 2011-09-29
And update your KDE to 4.6.5 from kubuntu-ppa : [http://www.kubuntu.org/news/kde-release-4.6.5](http://www.kubuntu.org/news/kde-release-4.6.5)

---

### Post by sirjeppe on 2011-09-29
The UseEvents option in xorg.conf didn't solve my problem unfortunately...

> **schnelle said:**
> And update your KDE to 4.6.5 from kubuntu-ppa : [http://www.kubuntu.org/news/kde-release-4.6.5](http://www.kubuntu.org/news/kde-release-4.6.5)

Do newer versions of KDE not suffer from this issue you mean? :) Or why should I upgrade? Is an upgrade needed for the xorg.conf setting to start working?

---

### Post by sirjeppe on 2011-09-29
> **schnelle said:**
> And update your KDE to 4.6.5 from kubuntu-ppa : [http://www.kubuntu.org/news/kde-release-4.6.5](http://www.kubuntu.org/news/kde-release-4.6.5)

I have added the ppa repo now, but after updating apt, I can't find any updates for anything.

I'm on KDE 4.6.2.

Do I need to do anything special?

---

### Post by schnelle on 2011-09-29
KDE 4.6.5 is only bugfix release. It is not new KDE release.

```
sudo apt-add-repository ppa:kubuntu-ppa
sudo apt-get update
sudo apt-get dist-upgrade
```

After this reboot your system.

I hope this helps.

---

### Post by sirjeppe on 2011-09-29
> **schnelle said:**
> KDE 4.6.5 is only bugfix release. It is not new KDE release.

```
sudo apt-add-repository ppa:kubuntu-ppa
sudo apt-get update
sudo apt-get dist-upgrade
```

After this reboot your system.

I hope this helps.

I tried that as well, but it didn't give me any updates either. However... I activated "pre released updates" and updated, and then I got the 4.6.5 version.

So - I have it installed now, but haven't rebooted yet.

---

### Post by sirjeppe on 2011-09-29
> **yucww210 said:**
> Sorry, no help to you but up 

?

---

### Post by sumski on 2011-09-29
What about
nvidia-settings -a PixmapCache=0 && nvidia-settings -a PixmapCache=1
?

---

### Post by sirjeppe on 2011-09-29
> **sumski said:**
> What about
nvidia-settings -a PixmapCache=0 && nvidia-settings -a PixmapCache=1
?

Yupp... That works, and I could of course put it as a cron job or something being run every 10 minutes or so, but I don't really like the idea :P

But I'll guess I'll have to go with that kind of solution for now if the upgrade of KDE doesn't make any difference.

---

### Post by sumski on 2011-09-29
[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/787971/comments/4](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/787971/comments/4)

---

### Post by elnur on 2011-10-22
I had this problem with 11.04 too. I'm glad not to have it on 11.10.

---

### Post by elnur on 2011-11-04
Ignore my last post. I'm still having this problem in 11.10.

Seems like I started experiencing this problem after I enabled the Nvidia driver.

sumski's solution works for me:

```
nvidia-settings -a PixmapCache=0 && nvidia-settings -a PixmapCache=1
```

I've set crontab to run this string from time to time.

---

