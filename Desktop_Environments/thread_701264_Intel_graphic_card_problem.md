---
title: "Intel graphic card problem"
date: 2008-02-19
forum: Desktop Environments
---

### Post by vince-rouge on 2008-02-19
Hello,

I am a bit stupid.

I wanted to change my screen configuration and I have changed the driver working for my Intel 855GM chip set.

That was not a good idea as long as now I cannot get more than 800x600 and before I was able 1024x768. It's a stupid thing because it used to work and now I changed this and it is block.

Of course, I tried to reput the old configuration (I am not sure which driver it was) but it doesn't work. I tried the "test" button and tried to reboot system but no chance !

What can I do ?? Where to find the driver for my chipset ?

Thanks !

---

### Post by vince-rouge on 2008-02-19
I resolve the problem with this command in root :
dpkg-reconfigure xserver-xor

---

