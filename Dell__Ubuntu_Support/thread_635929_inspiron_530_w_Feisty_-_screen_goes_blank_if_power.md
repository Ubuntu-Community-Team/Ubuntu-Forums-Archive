---
title: "inspiron 530 w Feisty - screen goes blank if power-cycled monitor"
date: 2007-12-09
forum: Dell  Ubuntu Support
---

### Post by LesFromWaldenVT on 2007-12-09
I have posted about this problem before and never seen an answer. I've reduced the problem to turning the power on the 20" Dell flatscreen off/on and the screen shows only grey. All of the apps are running (I've had downloads going and leave the system on overnight in this condition so they would complete - and they do). The video driver must take a nosedive and not come back.

This will also happen if I leave the system on long enough. Eventually, some kind of power option must kick in and cause the video driver to take an action that causes it to crash. I've turned off every power saving option I can find but it still does this.

I have a work-around. If I run vlc and pause the video, it seems to tell the os that it is 'busy' and whatever power option causes my problem does not kick in.

Does anyone know what API vlc might be using to tell the OS not to allow power-saving options to start? I would like to write a short program that just does that.

Thanks,
Les

---

