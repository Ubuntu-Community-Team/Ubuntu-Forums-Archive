---
title: "Missing titlebar/window border"
date: 2011-04-28
forum: Desktop Environments
---

### Post by e_torano on 2011-04-28
So, I just installed 11.04 and was installing everything I wanted fine till I got to installing compiz. It installed fine and ran for a few minutes before my window borders disappeared entirely (see the attached screenshot). I've since tried running metacity --replace, but this makes unity disappear, so I'm left with my open windows only. I've now removed compiz in the hope that might help, but it hasn't.

Any ideas as to the cause would be great.

PS; I heard that there can be issues with ATI/AMD. Alas, that is my exact setup. I am urged to install proprietary drivers, but they fail to download.

---

### Post by e_torano on 2011-04-28
Never mind this. I got it all sorted. Seems I somehow de-activated window decorations in CCSM without meaning to. Stupid mistake.

---

### Post by drenze on 2011-05-04
So what specifically did you have to do to resolve it? Because I have not been able to figure this one out.

Thanks!

---

### Post by Krytarik on 2011-05-04
drenze, please see this troubleshooting guide:
[http://ubuntu4beginners.blogspot.com/2011/04/missing-top-and-side-panels-in-unity.html](http://ubuntu4beginners.blogspot.com/2011/04/missing-top-and-side-panels-in-unity.html)

Greetings.

---

### Post by lnfinlty on 2011-05-20
I had the same problem with my system.  I read about configuring your x11 config file, adding lines etc..   Opened up CCSM, clicked on Windows Decoration and my title bar showed up.  Restarted the PC and found that I was unable to move my windows.  Located the "move window" option and found that it was unchecked.  Activated it by clicking the box and viola, back to normal.  Super easy fix.

---

