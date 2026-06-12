---
title: "Small resolution"
date: 2005-12-04
forum: Desktop Environments
---

### Post by César en Linux on 2005-12-04
Hi

how i change to a bigger resolution on Ubuntu??

pd. this is my first time, be nice with me

---

### Post by matthewv on 2005-12-04
Try System --> Preferences --> Screen Resolution

---

### Post by César en Linux on 2005-12-04
ok, i try that, but only show 1024x768, and i need 1280x1024

i can see that resolution on my windows

---

### Post by Qrk on 2005-12-04
Looks like x.org didn't detect your resolution right when it was configured. Or perhaps you are using a less than optimal driver. The easiest way to fix this is to  reconfigure x.org, and to try a different driver.

```
sudo dpkg-reconfigure xserver-xorg
```

does the trick. I had to try several drivers before finding one that allowed my proper resolution. Vesa is a good resort... it has the best hardware detection, but has few features.

---

### Post by thespazzz on 2005-12-04
I'm having the same problum except i'm trapped in 640x480 at 60hz.  I tried the above recomendation and all I could get was screwed up screens I couln't even read.

I know the resolution i'm trying to use works because Windows has ran it for over a year with no issues.

---

### Post by aysiu on 2005-12-04
[Here](http://ubuntuforums.org/showpost.php?p=129379&postcount=21) are some suggestions.

---

