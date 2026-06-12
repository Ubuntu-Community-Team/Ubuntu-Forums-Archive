---
title: "K3b problems with starting"
date: 2005-07-09
forum: Desktop Environments
---

### Post by fastb on 2005-07-09
Sometimes I try to start k3b and the first window opens normaly. But then it stops when checking cd devices. It just freezes. I can try and open a new one but still the same. But then when I restart the computer k3b starts itself and then it works normally and I can burn cds and dvds.
What could I do?

Thanks

---

### Post by anatole on 2005-11-27
same problem here, it hangs when "scanning for cd devices". any help?

---

### Post by anatole on 2005-11-27
sometimes (seems really random) i starts with:
```
attila@nanaki:~$ k3b
attila@nanaki:~$ find: /dev/.static: Permission denied
k3b: ERROR: (K3bDevice::Device) Unable to do inquiry.
k3b: ERROR: (K3bDevice::Device) Unable to do inquiry.
```

what may be the problem?

---

### Post by ytene on 2007-12-30
This may be a common problem - I'm seeing the same thing  too. What makes this all the more interesting is that I have observed this across multiple different releases of ubuntu [5.10, 6.10 and 7.10].

As with an earlier post here, I see the splash screen, then this hangs and basically any other KDE window is forced to appear "behind" it in the KDE display stack. Nothing works until I reboot the machine [effectively a full init 6 reboot, though I do use the KDE menu] and once KDE opens, K3B automatically loads and works as though nothing is wrong.

I have seen some slight variations here... namely it seems to be *occasionally* more reliable if you place a valid CD in every available drive, including a blank CD in your intended "writer" device. This suggests to me that earlier comments about it hanging during CD device detection might be valid.

Finally, and I'd be interested to know if anyone else has seen this, I get something similar, on occasion, when launching grip, the GNU ripper utility. Like K3B, grip seems to hang on start-up and of course it also depends upon the presence of an optical drive with media in it. This is probably just a wild guess in the dark, but I wonder if both apps are experiencing related parts of a common problem?

For anyone who might be interested in helping me diagnose the problem further... I am using ubuntu 7.10/AMD64 with KDE added on top. This gives me K3b 1.0.3 on top of KDE 3.5.8. Pretty much everything else works perfectly.

Hardware consists of a Tyan Thunder K8W motherboard [SMP with 2 x 250's] and an NEC DVD-RW with a model ID of ND-3540A.

I'd be interested to know if there is any news on this one...

Thanks and Regards,

C

---

