---
title: "GDM Started, Gnome won't Display"
date: 2009-02-28
forum: Desktop Environments
---

### Post by iam13013 on 2009-02-28
I was trying to install **NVIDIA-Linux-x86-180.29-pkg1.run**, so I opened rcconf and unchecked gdm.

I rebooted, installed the Nvidia driver, everything seemed to work fine.

Then I again opened rcconf, checked gdm, and rebooted.

Now when I reboot, I get the Ubuntu Loading Screen, then just a black screen. No matter how long I wait, nothing happens unless I press [ALT]+[F4], which it then goes to a command line login screen.

If I try to start GDM manually, it tells me that GDM is already running, then aborts the operation.

Can someone please help me get Gnome back?

Thanks in advance.

---

### Post by mediajunkie on 2009-02-28
HI  13013, 

I had similar issues on my notebook while using the latest notebook nvidia drivers.(..180.22..0 final)

Turns out that, if I run the latest version, it won't work. However, running the beta version ...180.17... does work perfectly. you might want to try that one.

---

