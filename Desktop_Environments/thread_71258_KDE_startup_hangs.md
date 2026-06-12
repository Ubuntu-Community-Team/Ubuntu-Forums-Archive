---
title: "KDE startup hangs"
date: 2005-10-02
forum: Desktop Environments
---

### Post by nrwilk on 2005-10-02
This has just started happening.  Startup was quick and nice for a few days, and then all of a sudden this starts happening:

after I give my login/pass KDE throws up it's splash screen and once it gets to "configuring peripherals" it hangs for about 2 minutes.  Then the splash screen disappears, leaving only the background image for about 3 more minutes.  Finally, after I've forgotten what it is I even want to DO on th computer, I hear the KDE startup sound, and about a minute later I see my desktop.  Another little thing that occured at the same time (seemingly) is that it takes a whole minute AFTER that for my keyboard to start working.  Very annoying.

I searched and searched, but I can't find anything that looks like this on here.  I tried disconnecting my ethernet cable and rebooting, and I also tried disabling NTP time syncing (both issues I saw accused of hanging the startup process).  But, the problem didn't even flinch.  Still there.

Any ideas are completely welcome!  Thanks much!

---

### Post by m0ns00n on 2005-10-05
This can happen if the machine crashed or the .kde folder somehow got a bit corrupted. Have had it happen to me many times. Remove the .kde folder and things should be dandy. Remember to back up your Mail dir :-)
File system corruptions can happen sadly...

Other ways this can happen anyone?

---

### Post by mlomker on 2005-10-05
> Other ways this can happen anyone?

If you have the default ext3 filesystem then it should be immune to that sort of corruption.  I'd agree that renaming the ~/.kde directory is a good troubleshooting method.

---

