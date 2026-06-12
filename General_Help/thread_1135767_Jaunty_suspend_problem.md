---
title: "Jaunty suspend problem"
date: 2009-04-24
forum: General Help
---

### Post by johnlugh on 2009-04-24
After upgrading from Intrepid yesterday, my suspend and hibernate functions stop working right. 

Have never had a problem before, but now they both don't manage to power down the computer and just bring up a black screen with a log-in window. Services and such are restarted.

Anybody else experiencing this behaviour? 

I'm using a Dell XPS M1330 btw, and am not sure if it's do with the the nvidia drivers.

Have checked but can't seem to find any similar problems so any debugging help would be awesome :)

---

### Post by 1packer on 2009-04-24
I just had the same problem, but mine just locked the screen, rather then logging me out. I also have never had this problem before and would appreciate any tips or advice.

Edit: I'm also using a Dell XPS, which may be coincidental or related.

---

### Post by yoasif on 2009-04-24
[https://wiki.ubuntu.com/DebuggingKernelSuspendHibernateResume](https://wiki.ubuntu.com/DebuggingKernelSuspendHibernateResume)

be sure to [report the bug]("https://bugs.launchpad.net/ubuntu/+source/linux/+filebug") and mention that it is a regression from intrepid.

---

### Post by 1packer on 2009-04-25
I got my computer to hibernate once, unfortunately it seems to have broken my kernel and I am now unable to boot into it. My previous kernel, 2.6.27-11, still works and is able to hibernate.

Edit: logged into 2.6.28-11 under recovery. X-windows is now broken and unable to be started

---

### Post by Anzan on 2009-04-26
> **yoasif said:**
> [https://wiki.ubuntu.com/DebuggingKernelSuspendHibernateResume](https://wiki.ubuntu.com/DebuggingKernelSuspendHibernateResume)

be sure to [report the bug]("https://bugs.launchpad.net/ubuntu/+source/linux/+filebug") and mention that it is a regression from intrepid.

Thanks for this.

I am getting the same problem with Ubuntu and Xubuntu on a ThinkPad R40.

---

### Post by johnlugh on 2009-04-26
yeah, my screen locks up rather than logs out (same as you 1packer). Anybody opened up a bug report? i will do, but not now as im in the middle of my exam period :P

---

### Post by schrodycat on 2009-04-26
Same thing here. Lost suspend after upgrade from Intrepid to Jaunty. Suspend log shows a component inhibited the suspend.

A little more investigation showed that it was pulseaudio.

See this existing bug: [https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/312505]("https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/312505")

I temporarily renamed pulseaudio on my system until this is resolved, and suspend/resume works fine again.

---

### Post by johnlugh on 2009-04-26
thanks! that bug report really helped me out- fixed it now. just looked at the pm-suspend.log to troubleshoot and there were some problems with a power-saving script i had (similar to [http://ubuntuforums.org/showthread.php?t=847773](http://ubuntuforums.org/showthread.php?t=847773)). 

haven't got a clue why but for my scripts in /etc/pm/power.d & sleep.d the script endings were no longer there! (i.e. "fi" didn't finish it off)
didn't have an issue with it before :S also there were some discrepancies with modprobe which jaunty didn't like me doing. it's all good now though, thanks :)

---

### Post by randyklein99 on 2009-04-27
Same thing here - Dell XPS, Intrepid to Jaunty, hibernate and suspend degraded from before.

where do I find this log report?

---

### Post by Gizmonty on 2009-04-27
Hi,

I'm also having this issue with a Dell Inspiron 1520 (Intel X3100 graphics) and it's a major problem for me - a shame given the number of improvements I'm seeing with Jaunty. Would someone mind explaining how to go about renaming the pulseaudio binary. Also, does this cause sound problems? I don't know much about audio on linux.

Cheers!

---

### Post by TylerMD on 2009-04-27
I fixed mine by removing the following files (I installed myself):

```

manuel@xps:~$ sudo rm /etc/pm/power.d/99-savings /etc/pm/power.d/99-nvidia
manuel@xps:~$ sudo rm /etc/pm/sleep.d/99-savings /etc/pm/sleep.d/99-nvidia 

```

---

### Post by jcookeman on 2009-04-27
The thinkwiki fix works. But, I just don't get why this is necessary. I installed Jaunty on an x61s -- by all means modern hardware -- and not only did I have to manually do the mouse scroll fix here, but hibernate was busted. Luckily, someone had found the fix for that, too. 

[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/312505](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/312505)

---

### Post by johnlugh on 2009-04-27
the suspend log can be found at /var/log/pm-suspend.log

might help you figure out what is stopping the suspend from working properly.

---

### Post by 1packer on 2009-04-29
After using an old kernel a few times and running all the disk checks available from booting into recovery my suspend is working fine now. I didn't do anything but it has worked consistently a few times now. It did remove my older kernel entry from the grub though...

---

### Post by wersdaluv on 2009-05-11
[https://bugs.launchpad.net/ubuntu/+bug/369606](https://bugs.launchpad.net/ubuntu/+bug/369606)

---

### Post by wersdaluv on 2009-05-14
When I installed the 2.6.29 kernel from [http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582) , the suspend problem was fixed.

---

### Post by Gizmonty on 2009-05-15
I tried the kernel upgrade on my inspiron 1520 with no luck (but did have to deal with an annoying tracker index bug thingy).

Looking at the earlier post linking to bug 312505, there is now a fix there that worked for me.

Edit the file /usr/lib/pm-utils/sleep.d/01PulseAudio and wherever it says sudo -H -u $i, change it to sudo -H -u "#$i" and voila, instant fix!

---

### Post by Gizmonty on 2009-05-17
Correction. Suspend now works *intermittently* only. Grrrr.

I'm a little annoyed that this hasn't yet been corrected in an update. It's a pretty major regression that Canonical should be jumping on. I've been browsing Apple's online store - that Macbook is starting to look more and more appealing.

---

### Post by Gizmonty on 2009-06-01
I just got around to trying the rename pulseaudio thing which does seem to work.

In case anyone is interested, the command I used was

sudo mv /usr/bin/pulseaudio /usr/bin/pulseaudio.bak

Audio still seems to work

---

### Post by mbradlcu on 2009-08-26
> **wersdaluv said:**
> When I installed the 2.6.29 kernel from [http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582) , the suspend problem was fixed.

yep, same here. I built and installed 2.6.30 (didn't use the existing ubuntu config,, doing that now, I'll report back if it doesn't work) using the instruction found here: [http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu) ... Little hassle with the dkms, apparmor modules not loading, and had to build the nvidia modules. Oh, the pm-suspend log didnt' show any errors when suspend would fail.

---

