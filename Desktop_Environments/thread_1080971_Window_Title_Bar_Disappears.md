---
title: "Window Title Bar Disappears"
date: 2009-02-26
forum: Desktop Environments
---

### Post by skunkbad on 2009-02-26
8.10 Ubuntu

I wanted to see how the "extra" visual effects looked, because I had never enabled them, and I decided I didn't care for them. After setting visual effects back to normal, some window title bars will disappear/reappear with mouse movement over/around them.

I just installed 8.10 tonight, and all I have done done the initial system-wide upgrade, and enable the restricted drivers for nvidia. This problem didn't happen until the switch of visual effects.

What should I do to fix this?

---

### Post by Therion on 2009-02-26
Try this.  

Copy and Paste into a Terminal:```
sudo mkdir -p ~/.config/compiz/ && echo USE_EMERALD="no" >> ~/.config/compiz/compiz-manager
```

---

### Post by skunkbad on 2009-02-26
I ended up finding another thread regarding this issue. It suggested changing the appearance>theme>cutomize>window border to glossy. This worked, so I didn't feel the need to do what you suggested.

What exactly will the command(s) you suggested do? I hate feeling like my fresh install of Ubuntu is broken. Do you think it might be because I am using the nvidia restricted driver?

---

### Post by enl on 2009-03-04
i had the same problem...its a porblem with the nvidia drivers...observed when using 173/177 versions..try the new nvidia 180 drivers available in intrepid updates section in packages.ubuntu.com
this should correct the problem
cheers

---

