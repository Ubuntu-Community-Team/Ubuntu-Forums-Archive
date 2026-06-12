---
title: "Xorg uses %45 cpu after suspend"
date: 2011-03-11
forum: Desktop Environments
---

### Post by ramsesiitr on 2011-03-11
Hello,
I have had this issue for long time, and I think it is time to fix this since it started to bother me recently.

I am using Ubuntu 10.04 and after suspending, the Xorg cpu usage goes crazy and takes up to %45, therefore, the fan never stops. Here is my [_/var/log/Xorg.0.log file_]("http://www.heypasteit.com/clip/UM5") of which everything seems fine (at least to me). But strangely, command glxinfo returns [_this_]("http://www.heypasteit.com/clip/UM6"). at the end of glxinfo output, it goes on and on about some id's with lots of parameters saying "None" or "Slow" in the end of the each line.

My system configuration is Intel Core2Duo T6400 with 4GB ram and Intel GM45 GPU.

Please let me know if further information is needed.

Any help highly appreciated.

Thank you.

---

### Post by ramsesiitr on 2011-03-12
Nothing?

---

### Post by nherriot on 2011-03-13
I too can confirm that I'm seeing this behaviour on all my machines that I've upgraded to Kbuntu 10.10. After about 2 days my main pc consumes 100% cpu for the Xorg process.
My laptop takes about 2 days too before it runs out of CPU for the same process.

I've refrained from upgrading my Netbook!
Anyone know what this is our how to go about fixing?

Has this been raised as a bug?

---

### Post by vinkuu on 2011-04-06
This problem does not seem to affect only Ubuntu. I'm using Aptosid and am faced with the same issue. Just started googling for a resolution, after my laptop crashed probably due to overheating because of the problem. That's how I stumbled onto this thread. 

Kernel version does not affect it (personal note). Nor does it seem to make any difference if the GPU chipset is NVidia or Intel, users of both chipsets are reporting the same problem. It's really a pain having to listen to the fan screaming constantly. Hopefully someone finds a resolution for this soon...

---

