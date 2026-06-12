---
title: "New Kernel Install and Ati Driver"
date: 2005-11-10
forum: Desktop Environments
---

### Post by lakerssuperman on 2005-11-10
I just installed the K7 kernel on my machine.  When i boot with it the mesa 3d driver loads.  With the stock i386 kernel the fglrx driver loads.  How do i get the fglrx driver to load with the k7 kernel.  Do i simply have to reinstall the driver?  Thank You for your help.

---

### Post by lakerssuperman on 2005-11-10
Never mind, just had to install the restricted modules for the kernel

---

### Post by RAOF on 2005-11-10
This is why you should install the "linux-k7" package.  It depends on the latest k7-kernel & the appropriate restricted modules ;)

---

### Post by bryant8 on 2005-11-11
Hi, I am a noob to Linux and Ubuntu. Just installed it yesterday, so I'm pretty clueless about everything.

My laptop is using the ati mobility 9000 chip. I followed the instructions here -> [http://ubuntuforums.org/showthread.php?t=78466](http://ubuntuforums.org/showthread.php?t=78466) on how to install fglrx 8.18.8 drivers. 

Upon reboot however I still get this when i do fglrxinfo

```
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)
```

So, being a noob I have no idea what I did by following the instructions in that URL. The thing about all these replies is they don't explain what the syntax does. So if possible can someone point me to somewhere I can learn about all these? I know about the Man thingy, will try to learn from there. 

So I don't know if I had installed the restricted modules from the instructions, nor do I know what a K7 kernel would be. I know what a kernel is :x 

Please advise, thank you :smile: 

--long-time windows user(from win 3.1), soon to be fully linux convert(once I start to get the hang of the OS)--

---

