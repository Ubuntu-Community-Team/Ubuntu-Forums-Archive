---
title: "Xubuntu 12.04 poor 2D performance (compared to other WE)"
date: 2012-05-15
forum: Desktop Environments
---

### Post by ambrosa on 2012-05-15
Looking for an Ubuntu alternative, past weekend I've tried Xubuntu, Kubuntu and Lubuntu 12.04
All o.s. was installed in a different disk partition, from scratch using its Live CD. I've created three different 40GB disk partition and I've installed o.s. above (formatting the partitions as ext4 journaled). And I've played with them :-)

Xubuntu meets my needs but ... there is something strange about 2D video performance (and I've the login timeout bug as described here [http://ubuntuforums.org/showthread.php?t=1970326](http://ubuntuforums.org/showthread.php?t=1970326) )

Kubuntu and Lubuntu are very very fast in my system (Core i7-2600, 8GB RAM, graphics Nvidia GTX-550, disk WD Velociraptor 10.000rpm 450GB).
I've tried to slighty overload the system copying 100GB files from a disk to another.
During copy KDE and LXDE are fast, I can move/resize windows, I run different program ... all without any lag. As it should be: it's Unix, not Win :-) :-)

But Xubuntu ... it looks like a Windows XP system under load: windows are frozen, very high lag, all Window Environment looks stalled. Terrible !! And unusuable.
And when the system is idle without any load, when I quickly move a window (left-right) I see vertical window border "broken" as I have a 1 USD video card with a very poor refresh: slooowww

And this sound very strange for me. I've read that Xfce is fast.
And all three o.s. installed are the same (more or less, all 12.04 version)
Why this big difference ?

Any idea ?

Thanks.

---

### Post by wkrekik on 2012-05-15
Have you checked iso image md5sum ?

---

### Post by ambrosa on 2012-05-15
> **wkrekik said:**
> Have you checked iso image md5sum ?

Obviously :-)
All 3 Live CD's are without errors.

BTW I must add an info, but I think that it's not relevant.
I need to start all Live CD's with F6 Option NOMODESET. Without this my graphics subsystem is not correctly inizialized.
But after install, I found already installed Nvidia proprietary driver, so I can use system without problem. GLXGears report about 18000 fps for all 3 o.s.

---

### Post by rai4shu2 on 2012-05-15
Have you tried Xubuntu with the Compositor disabled? (Setttings/Settings Manager/Window Manager Tweaks/Compositor, then uncheck "Enable display compositing")? That's the only real difference I can think of between those systems by default.

---

### Post by LewisTM on 2012-05-15
Strange behavior. It could be the XFCE window manager (xfwm4). Your system specs tell me you can easily run Compiz, maybe you could try installing and running it as an alternative
```
compiz --replace
```

---

### Post by ambrosa on 2012-05-15
> **rai4shu2 said:**
> Have you tried Xubuntu with the Compositor disabled? (Setttings/Settings Manager/Window Manager Tweaks/Compositor, then uncheck "Enable display compositing")? That's the only real difference I can think of between those systems by default.

Tried just now.
Nothing change.
Same behaviour enabling or disabling compositor

---

### Post by ambrosa on 2012-05-15
> **LewisTM said:**
> Strange behavior. It could be the XFCE window manager (xfwm4). Your system specs tell me you can easily run Compiz, maybe you could try installing and running it as an alternative
```
compiz --replace
```

Ok, I'll try this tomorrow.

---

