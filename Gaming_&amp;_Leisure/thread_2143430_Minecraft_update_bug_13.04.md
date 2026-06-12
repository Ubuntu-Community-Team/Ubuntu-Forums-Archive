---
title: "Minecraft update bug 13.04"
date: 2013-05-09
forum: Gaming &amp; Leisure
---

### Post by Chaosvoid on 2013-05-09
Hey, I need help with a minecraft bug. When i clicked force update it said will force but it doesn't. Please help? [http://tinypic.com/r/191ggg/5](http://tinypic.com/r/191ggg/5)

---

### Post by efflandt on 2013-05-10
Is the version that shows up in the screen after you login something other than 1.5.2? If you have a different version than current, it will usually ask after you login if you want to update.

If you want to try any "snapshots" of upcoming versions, that requires a somewhat different technique. Those do not contain a launcher and simply replace ~/.minecraft/bin/minecraft.jar in a working minecraft. And if you "update" those, they go back to whatever is the current release version. To test snapshots I replicate my .minecraft directory under a different name (which indicates its version) and use a script to swap directory names for the active ~/.minecraft.

You don't show the terminal window that launched minecraft to see if there are any errors there. The only insignificant error I see in the terminal is "java.io.FileNotFoundException: http://assets.minecraft.net/1_6_has_been_released.flag" because 1.6 has NOT been released yet. In the other terminal window you seem to have some problem with your network or apt sources (unrelated to minecraft).

Although, I am running 64-bit Ubuntu 12.04.2 (which I just reinstalled and copied my home directory to from a failing hard drive).

---

