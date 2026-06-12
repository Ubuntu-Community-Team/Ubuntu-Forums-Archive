---
title: "Cannot change resolution"
date: 2018-04-05
forum: Desktop Environments
---

### Post by turb03 on 2018-04-05
Hello everyone,
I recently installed lubuntu 17.10 on my old HP mini 2140 because it says it is designed for old systems, and so far is going great! But I encountered a few problems after the installation. Even though after I finished installing Lubuntu i rebooted my machine and on start up i had a black screen on the top left corner, that covered 2/3 of the screen. After reading some other posts about solution I managed to boot the system in "nomodeset" mode and it worked fine, but the resolution was pretty bad. I made is so it boots up that way everytime, and now I don't have to worry about the black box, but the resolution is really bad and when I try to do something it is very blurry. I tried installing drivers for my integrated intel video card (intel GMA 950) and I think I did something, but I still do not have the option the increase the resolution. I also tried adding new resolution (1024 x 576, which is the maximum for my laptop) using 'cvt 1024 576' and then xrendr to add it as a mode, and I make it available. But when I type 'xrandr -s 1024x576' it says it cannot change it, and also once I reboot the machine the whole thing is gone, so only the 640x480 is available. I'm pretty new with linux, so I would really appreciate it if anyone can help me.

Thank you very much,
- turb0

---

### Post by TheFu on 2018-04-06
I don't have a clue, but if Lubuntu switched to Wayland in 17.10 like the main Ubuntu desktop did, then perhaps trying to use X/Windows tools to control the display doesn't work?  With the main Ubuntu desktop, prior to login, we can click the "gear" and select xorg for the display manager after login.

Sometimes the selection of a different DE/WM/Display manager doesn't take, so be certain to check it twice before logging in.

But if Lubuntu doesn't use wayland, it won't work.

---

### Post by turb03 on 2018-04-06
Ok so I found a solution to my problem.

I updated the kernel of my lubuntu to the newest one that was available at the Ubuntu website, then I restarted the laptop and removed the 'nomodeset' command. After I did this the laptop recognized all of the possible resolutions and now it works perfectly! Hope that helps anyone with the same issue as mine.

- turb0

---

### Post by TheFu on 2018-04-07
> **turb03 said:**
> Ok so I found a solution to my problem.

I updated the kernel of my lubuntu to the newest one that was available at the Ubuntu website, then I restarted the laptop and removed the 'nomodeset' command. After I did this the laptop recognized all of the possible resolutions and now it works perfectly! Hope that helps anyone with the same issue as mine.

- turb0

Was this just an **apt upgrade** or did you manually get the kernel, source, compile, and install it? Basically, my question is whether normal patching would handle it or not.  
Would be helpful to know the exact kernel version that fixes it and the version where it is broken.  **uname -a**

---

### Post by turb03 on 2018-04-08
I had to manually download the kernel files and then install them to my machine, it wasn't just a normal **apt upgrade**. I think my kernel version was 4.13, and then I downloaded and installed v. 4.16 which fixed my resolution error.

---

