---
title: "Installing new kernel corrupts my xorg.conf"
date: 2006-07-19
forum: Desktop Environments
---

### Post by hfederau on 2006-07-19
I have been trying to install linux-k7 on my amd64 PC for a while now. It currently using linux-386. I have the Nvidia-glx drivers installed. Every time I install linux-k7 it cannot start X Window system anymore, it says that my xorg.conf is bad. Do I need to do more than just install linux-k7 for it to work?

Thanks,
Horst

---

### Post by avtolle on 2006-07-19
From other threads on the forum, I understand you need to reinstall your Nvidia drivers when you install a new kernel.

---

### Post by hfederau on 2006-07-19
thanks for the quick respond. So I guess what I need to do is go into "recovery mode" for the given kernel (k7) and then run "sudo apt-get install nvidia-glx again?

Thanks,
Horst

---

### Post by Mickeysofine1972 on 2006-07-19
Hi

When it fails you can drop to the command prompt by pressing CRTL+ALT+F1 then login.

once you have done that you can type:
```

sudo dpkg-reconfirgure xserver-xorg

```

Then go through the steps and select the 'nv' driver and finally reboot.

once you have rebooted you can uninstall the old nvidia-glx and then reinstall to get the k7 version.

Hope this helps!

Mike

---

### Post by hfederau on 2006-07-19
Thanks for the help Mike. I will try it tonight.

Horst

---

### Post by hfederau on 2006-07-19
Sorry Mike, I meant to ask you. Do you think that there will be a performance increase from kernel-386 to kernel-k7 on my amd64?

Horst

---

### Post by philippe_carlo on 2006-07-19
All you need to do, as suggested earlier is reinstalling. But you need to explicily tell apt to reinstall by issuing

```

sudo aptidude reinstall linux-restricted-modules-$(uname -r) nvidia-glx

```

The common install command will just tell you it's already installed and do zip.

I have to do something similar with my ATI card after every kernel update. It's supposed to be 'normal'.

---

### Post by hfederau on 2006-07-19
Thanks philippe_carlo. Do you see a performance increase when switching from kernel to the other? I mean, is it worth the effort? 

Horst

---

### Post by Mickeysofine1972 on 2006-07-20
I suppose the peformance increase is dependent on your other components, mobo and memory etc, as your cpu may be able to do more but, can your mobo allow it to go that fast?

the only answer really is suck it an see.

Mike

---

### Post by Ramses de Norre on 2006-07-20
I don't see a real performance increase here between 386 and k7 on my amd64.
But it's not much work to give in one command and try it out..

And you'll need to use this command after every kernel update (doesn't happen too much;)) so it's a good idea to write it down somewhere when you think you might forget it.

---

