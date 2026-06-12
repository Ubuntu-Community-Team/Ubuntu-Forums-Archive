---
title: "Configuration of one user mixed up - newb"
date: 2012-12-03
forum: Desktop Environments
---

### Post by RobertoRecordo on 2012-12-03
Hello 
My desktop quit working, I'm distressed, I need to get back to work!

recent fresh install of 12.10 Ubuntu Studio 64 bit
added the office suite.
Mostly things were working as expected, but still messing around with Jack/Alsa settings.

Today my desktop environment went funny (but I'm not laughing)
* gedit shows no insertion point indicator
* most programs (firefox, gedit others) sill shop pull down menus that disappear when I try to mouse over - managed to arrow down to select the required prefix thread to post  this!
* no windows have  minimize/full screen/quit buttons 
* the second user on this machine has no such problems

I did not hack any settings, with the exception of pulse audio settings.

I saw an earlier post today - same title 
[http://ubuntuforums.org/showthread.php?t=2090403](http://ubuntuforums.org/showthread.php?t=2090403)

but I think my problem is not self inflicted, and I don't think I could perform/understand  the suggested remedy because I'm linux NEWB.

Can any one help?

Rob

---

### Post by Isamu715 on 2012-12-04
If you didn't alter settings much there should be no problem with resetting them for your user account. Either delete them all and copy from the other users account or(after backing up your personal data) delete the problematic user and create it again. If the problem persists after redoing your tweaks to pulse audio settings then these tweaks may be the reason of your current problems.

---

### Post by RobertoRecordo on 2012-12-04
> **Isamu715 said:**
> If you didn't alter settings much there should be no problem with resetting them for your user account. Either delete them all and copy from the other users account or(after backing up your personal data) delete the problematic user and create it again. If the problem persists after redoing your tweaks to pulse audio settings then these tweaks may be the reason of your current problems.

Thank you for the reply.  Because I am learning the basics of using Ubuntu, and have not yet learned where user settings are stored, or even if you mean all of the user settings, or just desktop settings, or... I am lost. 

There is a recent thread [B]how to reset compiz and unity completely?
[/B][http://ubuntuforums.org/showthread.php?t=2087068](http://ubuntuforums.org/showthread.php?t=2087068)looking at that tells me that I probably need to know more before I can proceed.
I know how to do the basics in the shell, and I am willing to work on this, but I need a better description of what needs to be done.

Thank you,

Rob

---

### Post by Isamu715 on 2012-12-05
> There is a recent thread **how to reset compiz and unity completely?**What window manager are you using? If it's not Compiz following this makes no sense, Ubuntu Studio doesn't use Unity and you said you didn't alter settings much, thus I believe you're still on Xfce. There are lots of problems when running Compiz on Xfce, if that's the case try running:
```
xfwm4 --replace
```See if it makes any difference.

---

### Post by Impavidus on 2012-12-05
> **Isamu715 said:**
> What window manager are you using? If it's not Compiz following this makes no sense, Ubuntu Studio doesn't use Unity and you said you didn't alter settings much, thus I believe you're still on Xfce. There are lots of problems when running Compiz on Xfce, if that's the case try running:
```
xfwm4 --replace
```See if it makes any difference.
That's the code that worked for me. And don't delete all your settings too soon, you may delete more than you wished.

---

### Post by RobertoRecordo on 2013-07-05
You won't believe that it took me this long to get back to it!
Yet, this certainly made Firefox useable: I can see the minimix/maximiz/exit icons and the fonts and colors are as expected.

Thanks!

---

