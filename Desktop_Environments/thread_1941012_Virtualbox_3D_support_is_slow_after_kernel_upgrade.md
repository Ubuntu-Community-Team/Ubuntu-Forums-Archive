---
title: "Virtualbox 3D support is slow after kernel upgrade"
date: 2012-03-14
forum: Desktop Environments
---

### Post by matt.parkes on 2012-03-14
I hope this is in the right area... Apologizes if it is not.

So I installed VirtualBox 4.1.10 on Windows 7 64bit and Ubuntu 11.10 (64bit) a few days ago.  I enabled 3D support in VirtualBox and installed guest additions in ubuntu.  It was great, super smooth.  Window manager was snappy and I could move windows around no problem.  CPU usage goes up a bit but it was very responsive. 

```
user@user-VirtualBox:~$ uname -r
3.0.0-12-generic
```

Here is the problem.  When I did all the ubuntu updates today, the responsiveness dropped completely.  I re installed the guest additions but still terrible.  I realized there was a kernel update, so i'm not sure if this is the problem

```
user@user-VirtualBox:~$ uname -r
3.0.0-16-generic
```

So, I re-installed the Ubuntu VM completely and installed guest additions.  Everything 3D is good.  

So, should I not do the updates?  Has anyone experienced similar issues?  Anyway to solve it for the new kernel?  Let me know if you want some more information.

(I'm assuming it is something to do with the kernel but I guess it could be something else that gets updated)

---

### Post by MSPdwalt on 2012-03-14
What are you using for a host OS?

I run vmware player on my Ubuntu box, and use a windows VM.  Almost every time there's a Kernel update Vmware has to re-compile it's kernel modules for the new Kernel.  I've never had an issue, I would assume vbox would want/need to do something similar.

---

### Post by matt.parkes on 2012-03-15
I'm using Windows 7 64bit as the host. I have an i7 with 12 gb of ram and an nvidia 570.  I tried updating graphics drivers as new ones came out yesterday.  Its so weird, I can replicate the issue.  I have a couple different guests.  One did all Ubuntu updates first then installed guest.  One did updates, and enabled restricted drivers.  Both are noticeably slower 3D support after updates.  Shouldn't virtualbox be off loading graphics processing to the video card? I wonder if it will be fixed in a future update

---

### Post by MSPdwalt on 2012-03-15
Are virtualization extensions enabled in the BIOS?  Have you tried updating/re-installing vbox?

---

### Post by matt.parkes on 2012-03-15
I have virtualization extensions enabled in the BIOS.  I have tried a couple different versions of virtual box.  Not sure at this point what could be wrong... Seems to happen after ubuntu upgrades.  Do you think it is better to do all the upgrades then install GuestAdditions?  I tried that, but still same result.

---

### Post by MSPdwalt on 2012-03-16
guest addons after updates seems like the best idea.  Have you tried the vbox forums too?

---

