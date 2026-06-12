---
title: "Google Chrome on Ubuntu 12.04"
date: 2012-04-29
forum: Desktop Environments
---

### Post by blitzit on 2012-04-29
Google Chrome for Linux worked very well with ubuntu 10.04.

However, on ubuntu 12.04 I face the following problems as of now:
1) The tabs don't seem to work as seamlessly as they did earlier. I can pick up one tab and split it into a different window, but I cannot put that tab back into an existing window. Only new windows can be created.

2) Videos in youtube have a funny colour. Seems to be flash plugin error maybe, but as chrome comes with in-built flash plugin, I don't know what the problem is.

Kindly help with suggestions.

P.S.: I am using a 32 bit desktop. I have NVIDIA proprietary drivers installed.

---

### Post by markbl on 2012-04-29
I don't know about 1) but 2) is not specific to 12.04. It started on 11.10 about one month ago when adobe introduced a bad tint bug to the flashplayer update. Really annoying bug and completely lackluster response by adobe to address it so far. See [https://bugs.launchpad.net/ubuntu/+source/adobe-flashplugin/+bug/967091](https://bugs.launchpad.net/ubuntu/+source/adobe-flashplugin/+bug/967091).

---

### Post by lovinglinux on 2012-04-29
> **blitzit said:**
> Google Chrome for Linux worked very well with ubuntu 10.04.

However, on ubuntu 12.04 I face the following problems as of now:
1) The tabs don't seem to work as seamlessly as they did earlier. I can pick up one tab and split it into a different window, but I cannot put that tab back into an existing window. Only new windows can be created.

2) Videos in youtube have a funny colour. Seems to be flash plugin error maybe, but as chrome comes with in-built flash plugin, I don't know what the problem is.

Kindly help with suggestions.

P.S.: I am using a 32 bit desktop. I have NVIDIA proprietary drivers installed.

I can reproduce problem 1, but I don't have a solution. Must be a Chrome bug. 

About problem 2, see [http://ubuntuforums.org/showthread.php?t=1953796](http://ubuntuforums.org/showthread.php?t=1953796). Although some of the solutions require to use Firefox, they will work with Chrome as well.

---

### Post by blitzit on 2012-04-29
Unchecking the tick on "Enable Hardware Acceleration" worked. Bye-bye Smurfs :P

Thanks :)

---

