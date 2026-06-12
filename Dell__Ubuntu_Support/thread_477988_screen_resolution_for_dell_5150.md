---
title: "screen resolution for dell 5150"
date: 2007-06-18
forum: Dell  Ubuntu Support
---

### Post by mr2v6 on 2007-06-18
I have a dell 5150 and the resolution seem to be stuck  1024x768, instead of the monitor that I am using ... that goes 1600*1200.

Has anyone have a solution to have this increased.  There are times when I reinstlal Ubuntu 7.0 that it gets the resolution.  Since my pc is a dual boot, I have to fix a lot , and I can't seem to make the 1600*1200 work permanently.

Any response would be appreciated.

Thanks,
Raymond

---

### Post by reckless2k2 on 2007-06-18
you need to search on 915 resolution and that'll fix your problems. i don't know enough about it but enough to know that's what you need to install.

---

### Post by Simran on 2007-06-19
915resolution is for intel graphics chips, if that is what you have then this is what you have to do.

paste this in the terminal

```
sudo apt-get install 915resolution
```

once its installed 

```
sudo 915resolution mode 1600 1280
```

or replace 1600 1280 with what ever resolutions you want. then just restart your xserver and its all done :)

Simran

---

### Post by Frizguru on 2008-03-21
I know my Dell 5150 only goes to 1400x1050.

---

