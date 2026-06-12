---
title: "How to use wine with native windows programs"
date: 2007-09-28
forum: Desktop Environments
---

### Post by reflexion on 2007-09-28
Hi

I have a dual boot system with xp and ubuntu.

My windows partition is mounted in ubuntu.

Would it be possible to use Wine to run programs that are already installed on my other partition?


Thanks

---

### Post by DJ_Peng on 2007-09-28
I'm not sure about running them under Wine, but it is possible to [run them under VMWare]("http://mazimi.wordpress.com/2007/07/04/run-windows-apps-from-your-existing-windows-partition-in-linux/") from their current location.

---

### Post by reflexion on 2007-09-29
Wow,

This is so nice. I have been waiting for this for so long!

But still i have 2 minor problem:

1- Would it be possible for windows (under vmware) boots when Im booting linux?

2- When I run your program to have the start menu out of windows, what it does is simply opening a new large blue window in which all I see is blue, but I can still press the “windows button” to access the start menu. And I cannot take drag the windows created inside the “blue window”.


thanks

---

### Post by reflexion on 2007-10-01
bump
?

---

### Post by DJ_Peng on 2007-10-01
> **reflexion said:**
> Wow,

This is so nice. I have been waiting for this for so long!

But still i have 2 minor problem:

1- Would it be possible for windows (under vmware) boots when Im booting linux?You can have VMware launch at startup with System > Preferences > Sessions. I'm not sure if it's possible to start a specific VM upon launching VMware.

> 2- When I run your program to have the start menu out of windows, what it does is simply opening a new large blue window in which all I see is blue, but I can still press the “windows button” to access the start menu. And I cannot take drag the windows created inside the “blue window”.I'm not quite sure what it is you're asking, but the Wine integration in the beta of Ubuntu Gutsy adds Windows programs installed with Wine to the Applications menu (Applications > Other).

---

### Post by reflexion on 2007-10-01
This is not what I meant, but I think I managed to solve my problem.

I needed to run the program inside windows, then modify a regedit value (not the NoDesktop = 1)

Ill post the link of the solution when I find it.

---

