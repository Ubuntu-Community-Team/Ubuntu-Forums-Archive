---
title: "Beryl window bars no longer appear after reconfig'ing XConfig"
date: 2007-03-06
forum: Desktop Environments
---

### Post by zoopside on 2007-03-06
Hello,

I successfully installed Beryl on my machine with the nVidia drivers pointed at a default VGA card/monitor. Everything worked and looked great. I wanted to bump up my resolution to higher than the default 1024x768, so after perusing some sites I decided to :

sudo dpkg-reconfigure xserver-xorg

with all my video card (nVidia GeForce 6800) & monitor information (Dell FPW2005).

Once I rebooted, I have up to 1280x1024 screen resolution available, but the nice Beryl window bars have left. So I am unable to move windows, minimize/maximize them, etc. The beryl cube still works, however, and I can still move between workspaces without issue.

So, it appears that some portion of Beryl is unhappy with my new xconfig params. Can someone point me in the right direction for debugging this further?

Thanks beforehand for any help.

---

### Post by ffxr on 2007-03-06
> Can someone point me in the right direction for debugging this further?

i would try uninsatlling/reinstalling beryl... first anyway (purging all settings)

remove beryl

```

sudo apt-get --purge remove beryl* emerald* libberyl* libemerald*
sudo apt-get --purge autoremove
sudo apt-get autoclean

rm -r ~/.beryl
rm -r ~/.emerald
rm -r ~/.beryl-managerrc 
```

i would also check the beryl forums as i am sure i read something about this the other day...

---

### Post by compmodder26 on 2007-03-06
I had this problem before.  I was able to fix it by adding:

```
Option         "AddARGBGLXVisuals" "True"
```

in xorg.conf under the "Screen" section

---

### Post by zoopside on 2007-03-06
compmodder26, thanks much! The added line in xconf fixed my beryl install....

---

