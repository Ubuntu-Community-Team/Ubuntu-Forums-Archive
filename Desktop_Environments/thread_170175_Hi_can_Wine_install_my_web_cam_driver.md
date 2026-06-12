---
title: "Hi can Wine install my web cam driver"
date: 2006-05-04
forum: Desktop Environments
---

### Post by dhruv_1884 on 2006-05-04
Hi i have a CIF SIngle chip SC120 web cam,
i've heard that wine can install windows products,
could ti install the "windows" driver so that i may be able to use my webcam from ubuntu

regards
-
dc

---

### Post by Brynster on 2006-05-04
The answer to that is both yes and no.

Wine is a compatibility layer that converts win32 system requests into native Linux ones, so as a result *some* windows apps and games work (to varying degrees) on Linux. The same also applies for hardware within the Wine enviroment. 

So it may install your webcam drivers and it may make your webcam work whilst its running in Wine. But it will not then give cross compatibility to linux, sorry it just doesn't work that way. the best place to go to get more clued up is [http://www.winehq.org]("http://www.winehq.org") 

I hope i haven't put to bigger dampener on your idea

---

### Post by nalmeth on 2006-05-04
Have you already pursued getting it to work natively in Ubuntu?

---

### Post by dhruv_1884 on 2006-05-04
i plugged it into the usb port, then installed a cam software from synaptic called camstream. 
when i run camstream i get the message below
Qt: Locales not supported on X server
qstring_to_xtp result code -2
there is no device in the device list of camstream

---

### Post by shof2k on 2006-05-04
I don't think so, as you'd need to have the cam working in linux first.

If you read the winehq FAQ's it explains although wine may install the driver, because it translates the windows system calls to linux system calls, you'd need a working linux API available first.

---

