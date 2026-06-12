---
title: "No resume image, doing normal boot..."
date: 2009-07-26
forum: Desktop Environments
---

### Post by vbrocz on 2009-07-26
No resume image, doing normal boot...

Each time i start ubuntu 9.04 i get the above error, can someone tell me how to get the GUI???????

---

### Post by bad_crow on 2009-07-26
hi, 

I have this on all my linux, that's normal, the kernel seeks if the computer was sent to sleep, if there is no resume image, that's only because the computer wasn't hibernating, so there is nothing to resume, because nothing is pending.

But if you haven't the "GUI" (which I suppose is gnome), there's obviously a problem.

Is there anything else after "doing normal boot" or is it stuck as this line ? do you got a shell prompt ? 
If you can go to the shell, try : 
startx

this command normally launches the UI and gives the error when the UI can't be launched.

---

### Post by vbrocz on 2009-07-26
It worked perfectly............

Thank you so much!

:popcorn::popcorn:

---

### Post by dindos on 2009-07-27
> **bad_crow said:**
> hi, 

I have this on all my linux, that's normal, the kernel seeks if the computer was sent to sleep, if there is no resume image, that's only because the computer wasn't hibernating, so there is nothing to resume, because nothing is pending.

But if you haven't the "GUI" (which I suppose is gnome), there's obviously a problem.

Is there anything else after "doing normal boot" or is it stuck as this line ? do you got a shell prompt ? 
If you can go to the shell, try : 
startx

this command normally launches the UI and gives the error when the UI can't be launched.
hi its really a pain in da .. this problem been facing for a month. i have the same problem dat the gui doesnot show up and been transferred to a shell .i have tried everything but all in vain.help

---

### Post by QuizasQuizas on 2009-08-30
Hi all,

I'm actually having the same problem on boot-up; tried entering "startx" in the shell prompt and got this output:

```
waiting for X server to shut down error setting MTRR (base = 0x80000000, size = 0x10000000, type = 1) Invalid argument (22)
   ddxSigGiveUp: Closing log
```

---

