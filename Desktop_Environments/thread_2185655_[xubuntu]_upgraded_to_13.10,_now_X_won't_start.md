---
title: "[xubuntu] upgraded to 13.10, now X won't start"
date: 2013-11-03
forum: Desktop Environments
---

### Post by jollyrogr on 2013-11-03
I've been running Xubuntu on an AMD64 machine since 8.04 I think.  I had been at 12.04 for the longest time, then yesterday decided to update.  It wouldn't let me update directly to 13.10, so I went from 12.04 to 12.10, then to 13.04, and then to 13.10.  Everything went fine through 13.04.  After the upgrade to 13.10 and reboot, X windows will not start.  On boot, it drops to a login prompt.  If I login and type 'startx' the screen will go black and the system is unresponsive and needs to be reset.

Any thoughts on where to start looking for the problem?

If I have to do a fresh install is there a way to do it w/o wiping my home dir?  I don't have enough disk space to copy it elsewhere and I don't want to lose it.

Thanks

---

### Post by Remten on 2013-11-03
What command did you use to go from each version to the next?

(I am considering trying something similar.)

---

### Post by jollyrogr on 2013-11-03
I just used the system update tool.  It tells you when a new release is available and you can choose to install it.  You may need to adjust one of the notification settings for it to notify you of a new release.  Obviously I cant get into X right now, so I can't tell you exactly.

---

### Post by grahammechanical on 2013-11-03
@jollyrogr

You can try selecting Recovery Mode at the Grub menu. You will find it in 13.10 under the Advance Options for Ubuntu sub-menu. At the recovery menu select Resume. That may get you to a desktop login without activating the proprietary video driver. Instead you will be using a subset of the Nouveau open source driver called llvmpipe. It is used for graphic cards that do not have 3D acceleration.

If you get to a desktop you should try choosing another video driver. In 13.10 we do that by going to System Settings>Software and Updates and opening the Additional Drivers tab. You must be connected to the internet. It will search for video drivers.

I would not recommend upgrading from 12.04 to 13.10 the way you did it unless we have reverted the desktop back to its default settings. I would also recommend using Nouveau instead of a proprietary video driver. By the end of April next year 14.04 will be available and those running 12.04 LTS can upgrade directly to 14.04.

But to do it version by version to get to 13.10 from 12.04 LTS we go to System Settings>Software Sources. In that utility there will be a tab that we can use to change the settings of when we are notified of new Ubuntu releases. Choose, to be notified of the next release instead of the next LTS. and then run check for updates. We should get a button to click.

Ubuntu 13.10 only has 9 months support so we will have to upgrade to 14.04 anyway.

Regards.

---

### Post by jollyrogr on 2013-11-03
So this might be a dumb question, but how do I get to the grub menu?  I never see one, it just boots straight to xubuntu.  As far as video drivers, could I simply uninstall fglrx and then wouldn't it revert to the base driver?

I should have been updating more frequently I suppose, but I've never done anything to revert any settings to default before an update, and never had an issue before.

If you're running LTS, is the best way to update to wait for the next LTS?

Edit: a quick google of Nouveau revealed that I wouldn't want to use that driver since it's for Nvidia.  My integrated graphics chip is a Radeon 3200

---

### Post by webmastir on 2013-11-03
Ah yes, ATI + Ubuntu issues. I wish I could help but do wish you the best of luck figuring this one out. I take it you didn't image your hard drive before doing a dist-upgrade?

---

### Post by jollyrogr on 2013-11-03
did the steps on this page to remove fglrx
[http://askubuntu.com/questions/68306/how-do-i-remove-the-propretary-ati-drivers](http://askubuntu.com/questions/68306/how-do-i-remove-the-propretary-ati-drivers)

also had to add "nomodeset" in /etc/defaults/grub before it would work, but it does boot into XFCE now.  I still think my best option for a smooth running system at this point is to do a fresh install since I've done nothing but update since 8.04 and there's a lot of deprecated crap on there by now.

---

### Post by dentaku65 on 2013-11-06
Is  .Xauthority file owned by you?
```
 ls -al ~/.Xauthority
```

---

### Post by jollyrogr on 2013-11-06
> **dentaku65 said:**
> Is  .Xauthority file owned by you?
```
 ls -al ~/.Xauthority
```


Yes, but the issue was not related to that file anyway.  It was purely video driver related.  See my previous post to see how I got it to work.  I'm going to do a clean install in a week or so, but until then, my system is running fine albeit with somewhat lacking graphics performance.  Not a big deal for me.

Not sure how to change the title of the post or if I can?  Maybe a mod can mark it as [solved] ?

---

### Post by jollyrogr on 2013-11-09
Did some more research on this today.  Apparently my Radeon HD3200 uses the AMD 'legacy' catalyst driver which only works on "Xorg 6.9 to Xserver 1.12 and Kernel version up to 3.4".  Hence the reason for my issues when upgrading to 13.10.  Seems to be working ok without the fglrx driver if only a little bit slower

---

### Post by dentaku65 on 2013-11-10
> **jollyrogr said:**
> Did some more research on this today.  Apparently my Radeon HD3200 uses the AMD 'legacy' catalyst driver which only works on "Xorg 6.9 to Xserver 1.12 and Kernel version up to 3.4".  Hence the reason for my issues when upgrading to 13.10.  Seems to be working ok without the fglrx driver if only a little bit slower

Hi,
while ago I wrote a guide to create deb from ATI Legacy beta drivers:
[http://ubuntuforums.org/showthread.php?t=2139200](http://ubuntuforums.org/showthread.php?t=2139200)

I still it using with my box:
> Xubuntu Saucy 64bit
Kernel 3.11.0-13
AMD Radeon HD 7400G


Despite the fact of beta stage works pretty well

---

### Post by VViL on 2013-11-10
Hi, In my case, the xubuntu loader shows up, then it closes and prompt me to console, what I do, it's install fglrx-pxpress according to this post
[URL="http://askubuntu.com/questions/205112/how-do-i-get-amd-intel-hybrid-graphics-drivers-to-work"]
http://askubuntu.com/questions/205112/how-do-i-get-amd-intel-hybrid-graphics-drivers-to-work[/URL]

sudo apt-get install fglrx fglrx-pxpress

The exact comment its this
[http://askubuntu.com/a/370468](http://askubuntu.com/a/370468)

---

