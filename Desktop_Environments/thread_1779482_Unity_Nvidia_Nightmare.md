---
title: "Unity Nvidia Nightmare"
date: 2011-06-10
forum: Desktop Environments
---

### Post by Crempel on 2011-06-10
Having read quite a few of the contributions about Unity, I am still looking for a solution to the following problem, which, I am sure; others have encountered also:

1. Clean install, no access to Unity
2. Additional drivers install - done
3. Driver installed but not active - no matter whether it's current or 173)
4. Unity works for a while, after updating the system, unity doesn't work anymore. 
5. Back to Gnome 2, downloading the org Nvidia driver, trying to install it on the command line (init 1) - black and white vertical stripes!

For Pete's sake, I DO like Unity, but please let me successfully install it! Judging by forum messages, this BUG has been known for at least a month. I anybody going to do anything about it!?

I have downloaded Kernel 2.6.39 from whateversource, but have not installed it yet. Is it the kernel, is it whatever in Natty that courses these problems, or is it my Nvidia card?

My hardware: AMD 2.9 Mhz dual core, Nvidia 7200 GS (258 Mhz), 4 GB Ram

I really want to use Unity, but if nothings happens soon, I will have to give up.

P.S. Fedora 15 enables Gnome 3 (shell) on nouveau; to install the propriety Nvidia divers, however, is also impossible...

---

### Post by Crempel on 2011-06-10
Further to my previous post: I have now installed kernel 2.6.39 using ppa.launchpad.net/kernel-ppa/ppa/ubuntu natty main and the same thing happened -
with Nvidia driver 173 installed (but not active ?!) Unity worked well. 

Once I updated the system using synaptic, Unity will not start anymore.

Sorry, I give up and see where I'll go with Fedora 15 and the gnome shell; I sure would have preferred Unity....

Bye:(

---

### Post by maverick280857 on 2011-06-10
Assuming you are using nvidia drivers, can you please post the outputs of

```
ls -l /usr/lib/libGL*.so*
```

and

```
ls -l /usr/lib/xorg/modules/extensions/libglx*.so*
```

You said that Unity broke *after* an update. My guess is that the update broke the symbolic links in one or both of the directories /usr/lib and /usr/lib/xorg/modules/extensions. We can be certain when you post the output.

On my system,

/usr/lib/libGL.so -> /usr/lib/libGL.so.270.41.19

/usr/lib/xorg/modules/extensions/libglx.so -> /usr/lib/xorg/modules/extensions/libglx.so.270.41.19

---

### Post by Crempel on 2011-06-11
@maverick280857
Thanks for your reply. Ihave done a fresh install. After installing the current Nvidia driver via Additional Drivers Unity was inaccessible.
I replaced it with the version 173 and Unity worked. I then did a complete update. Now I am back to square 1 - no Unity.

The required output is as follows:


 mike@hal:~$ ls -l /usr/lib/libGL*.so*
lrwxrwxrwx 1 root root     18 2011-06-11 16:44 /usr/lib/libGLEWmx.so.1.5 -> libGLEWmx.so.1.5.2
-rw-r--r-- 1 root root 292752 2011-02-03 18:25 /usr/lib/libGLEWmx.so.1.5.2
lrwxrwxrwx 1 root root     16 2011-06-11 16:44 /usr/lib/libGLEW.so.1.5 -> libGLEW.so.1.5.2
-rw-r--r-- 1 root root 337808 2011-02-03 18:25 /usr/lib/libGLEW.so.1.5.2
lrwxrwxrwx 1 root root     20 2011-06-11 16:44 /usr/lib/libGLU.so.1 -> libGLU.so.1.3.071000
-rw-r--r-- 1 root root 453272 2011-04-19 12:52 /usr/lib/libGLU.so.1.3.071000
mike@hal:~$ ls -l /usr/lib/xorg/modules/extensions/libglx*.so*
-rw-r--r-- 1 root root 438440 2011-05-21 13:57 /usr/lib/xorg/modules/extensions/libglx.so

It would be great if you could make some sense of this, I surly can't.

Thanks in advance

---

### Post by wildmanne39 on 2011-06-12
> **Crempel said:**
> @maverick280857
Thanks for your reply. Ihave done a fresh install. After installing the current Nvidia driver via Additional Drivers Unity was inaccessible.
I replaced it with the version 173 and Unity worked. I then did a complete update. Now I am back to square 1 - no Unity.

The required output is as follows:


 mike@hal:~$ ls -l /usr/lib/libGL*.so*
lrwxrwxrwx 1 root root     18 2011-06-11 16:44 /usr/lib/libGLEWmx.so.1.5 -> libGLEWmx.so.1.5.2
-rw-r--r-- 1 root root 292752 2011-02-03 18:25 /usr/lib/libGLEWmx.so.1.5.2
lrwxrwxrwx 1 root root     16 2011-06-11 16:44 /usr/lib/libGLEW.so.1.5 -> libGLEW.so.1.5.2
-rw-r--r-- 1 root root 337808 2011-02-03 18:25 /usr/lib/libGLEW.so.1.5.2
lrwxrwxrwx 1 root root     20 2011-06-11 16:44 /usr/lib/libGLU.so.1 -> libGLU.so.1.3.071000
-rw-r--r-- 1 root root 453272 2011-04-19 12:52 /usr/lib/libGLU.so.1.3.071000
mike@hal:~$ ls -l /usr/lib/xorg/modules/extensions/libglx*.so*
-rw-r--r-- 1 root root 438440 2011-05-21 13:57 /usr/lib/xorg/modules/extensions/libglx.so

It would be great if you could make some sense of this, I surly can't.

Thanks in advanceHi, first the driver is really active when you activate it, the bug is that is shows it is noty in use,I have the same driver installed and the 173 is the best for me, the newer drivers have issues. Since you installed from 2 different sources and I know from my own experience you have to drivers installed now, go into synaptic and uninstall the new driver and leave the old and reboot.

---

### Post by Crempel on 2011-06-12
Thanks wildmanne 39,
it still doesn't work.

I'll try something else.:(

---

### Post by wildmanne39 on 2011-06-12
> **Crempel said:**
> Thanks wildmanne 39,
it still doesn't work.

I'll try something else.:(Hi, I am sorry to hear that, I know some people have not been able to solve there problems no matter what they do. Installing the new kernel will probably not help and it is not supported for natty, it is for the next release, it could cause more problems.

---

### Post by Crempel on 2011-06-13
> **wildmanne39 said:**
> Hi, I am sorry to hear that, I know some people have not been able to solve there problems no matter what they do. Installing the new kernel will probably not help and it is not supported for natty, it is for the next release, it could cause more problems.

Thanks for your interest, wildmanne39. I have since installed Fedora 15 and I can also not get the nvidia driver to work; I removed nouveau as per instruction fiven on the FC forum, but no go. Reading plenty of posts on the forum, it appeares that my Nvidia 7200 GS card is just not supported by FC 15.

I still prefer Unity over gnome 3 (which at least works perfectly with nouveau), and I thinks with Natty it's not the gpu,but for the time being I will continue to use a distro that at least works (without 3D) with my hardware (64-bit, 4 GB RAM, AMD dual core cpu):confused:

---

### Post by Crempel on 2011-06-13
Well, well, what do you know? 
After finding some info in the net saying that the Nvidia 7200 GS car was blacklisted on Natty, suggesting to add UNITY_FORCE_START=1 to /etc/environment.

OK, so, yet again, I installed Natty (from live), opted to have all upgrades installed at the same time, rebooted, and - Unity (3D) worked! I was offered to install additional drivers, but rebooted again instead. UNITY in all its glory again, and no icon on the panel offering driver updates.

Just to be sure, I rebooted again, and everything is perfect. Glxgears reads around 1550 fps and there is no need to touch /etc/environment.

BUT, I can't tell you how come this "miracle" happened, so this whole exercise won't be of much help to others, but I now can use my favorite distro again. Many thanks again to those of you who helped me with this issue.:D
I

---

### Post by Crempel on 2011-06-13
Sorry, one last entry re this issue, but I now got a happy end.

Whilst I had opted to run all updates while installing Natty, they were only downloaded, not installed. Once I installed them, I was back to "you don't seem to have the write hardware ..."

OK, now I added UNITY_FORCE_START=1 to /etc/environment and - bingo!

So, all you people having trouble with an Nvidia 7300/7200GS card, here's your answer!

Cheers:D

---

