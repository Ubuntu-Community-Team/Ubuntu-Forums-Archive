---
title: "Fails to boot"
date: 2008-02-21
forum: Desktop Environments
---

### Post by thevoidreturns on 2008-02-21
Hello,
      I've been tweaking my Ubuntu installing a few programs not sure what I did to be honest now, I made a mistake somewhere along the lines. My ubuntu box used to work fine, but now for some reason it won't even get to the login screen. What I have tried is using the recovery mode and this mode works fine. So I'm guessing I've messed something up with the video drivers as it works in recovery mode but not normal.

Can someone help me please????

Thanks
Adam

---

### Post by taurus on 2008-02-21
If you screw up your X server, you can reconfigure it again with

```
dpkg-reconfigure xserver-xorg
```

---

