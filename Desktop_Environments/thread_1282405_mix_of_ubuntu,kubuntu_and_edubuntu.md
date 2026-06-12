---
title: "mix of ubuntu,kubuntu and edubuntu"
date: 2009-10-04
forum: Desktop Environments
---

### Post by carlo bolzonello on 2009-10-04
Hello All,

I have installed 9.04, got it working with all my hardware, configured my way and was over the moon happy..ready to dismantle the Microsoft hold. I decided to install the educational items for ubuntu, after doing this for my daughter, my computer has gone weird!!!.

When it loads, the splash screen now says kubuntu and the login screen says edubuntu. when you login it its my old ubuntu again, I removed the education stuff and i still have this issue. 

I want my pure ubuntu back please, can any one help me please

---

### Post by ajgreeny on 2009-10-04
Try ```
sudo dpkg-reconfigure gdm
```and choose gdm from the options that appear, and ```
sudo dpkg-reconfigure usplash
``` for the splash screen, and choose again.

---

