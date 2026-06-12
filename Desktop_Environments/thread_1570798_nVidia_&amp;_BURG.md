---
title: "nVidia &amp; BURG"
date: 2010-09-08
forum: Desktop Environments
---

### Post by GARoss on 2010-09-08
I've stumbled on to something & was curious if anyone had experienced something similar. Basically, nVidia drivers clash & cause BURG not to function.
 
I thought BURG would be a nice add to my Ubuntu 10.04 amd64 & Windows 7-64bit PC. I was using v173 driver for my nVidia 6800GT; Dell monitor set to 1920x1200.

Something went wrong installing BURG & I messed up grub & couldn't boot at all. With some help from our forum members, I was able to reinstall grub2. I tried a number of reinstalls of BURG but could never get BURG at startup even when it appeared to install. All I got was the typical grub OS selection menu. 

Thinking BURG wasn't compatible with amd64, I decided to install Ubuntu 10.04 32bit. Went through all the updates, then installed the recommended v173 driver for nVidia video card. After reboot, installed BURG & had similar results as before with amd64 version. BURG didn't work.

But, I did notice something interesting. Prior to installing the v173 driver, the usplash screen was at a much higher rez, looking similar as it looks using the install disc. Also, my desktop was already set to 1920x1200 resolution with a default driver. After v173 was installed the usplash screen went to a much lower rez - maybe 640x480 (this is the same in amd64bit, too).

I decided to reinstall Ubuntu 10.04 32 bit but this time I did not install any nVidia drivers. This time  BURG installed & works perfectly.
 
Needless to say, I haven't attempted to install any nVidia drivers as I'm not crazy about advanced graphics anyway. But, it could be a good experiment to see if BURG would still work properly. I am convinced that BURG will not work with nVidia drivers; at lease not with the combination video card & driver my PC needed. Maybe it's not an issue for new cards. 

This wasn't intended to be a rant but to help someone who has a similar issue installing BURG. If you have another theory why BURG didn't work until nVidia was removed, please chime in.

---

### Post by GARoss on 2010-09-08
Out of curiosity, I activated v173 driver & BURG still preforms OK. Weird.

---

