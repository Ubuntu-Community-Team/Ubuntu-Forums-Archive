---
title: "Random freezes with compiz fusion on gutsy"
date: 2007-12-06
forum: Dell  Ubuntu Support
---

### Post by Spitz on 2007-12-06
Hi, I have a Dell 1405e/640m laptop with a integrated Intel 945GMA graphics card.

My system tends to have random freezes where the screen and keyboard do not work. The mouse however moves nicely about, and the only keyboard commands that work are SysRq commands. The Alt+PrintScreen+k is able to kill X, but it isn't able to restore it again, and therefore the only thing I can do is rebooting by using the powerbutton or Alt+PrintScreen+b.

It looks like it is more likely to freeze when using memory heavy programs, like OOo (esspecially when scrolling) and sometimes Firefox, but it also happens when only running smaller programs.

I would be really happy if someone found a solution to the problem, since I love all the compiz fusion effects and it is a drawback to turn compiz of every time I am doing something important on my computer.

---

### Post by bluedragon436 on 2007-12-08
Do you have the restriced drivers loaded???  Also do you have the Compiz Settings manager loaded???  I was having a very similar issue when I first installed 7.10 and Compiz on my Dell laptop, and after I installed the restricted driver for my video card, and installed the Compiz settings manager it was working better.....but I also did a search in here for Compiz Fusion not being able to be activated....and I found my fix at this link: [http://ubuntuforums.org/showthread.php?t=582207&page=7](http://ubuntuforums.org/showthread.php?t=582207&page=7)  at the bottom by Forlong....I read all the previous post on that thread as well, but I followed what Forlong had said on this page and it worked fine for me, not saying it will be your fix as well, but can't hurt to give it at try...

---

### Post by Paul S on 2007-12-08
> **Spitz said:**
> Hi, I have a Dell 1405e/640m laptop with a integrated Intel 945GMA graphics card.

My system tends to have random freezes where the screen and keyboard do not work. The mouse however moves nicely about, and the only keyboard commands that work are SysRq commands. The Alt+PrintScreen+k is able to kill X, but it isn't able to restore it again, and therefore the only thing I can do is rebooting by using the powerbutton or Alt+PrintScreen+b.

It looks like it is more likely to freeze when using memory heavy programs, like OOo (esspecially when scrolling) and sometimes Firefox, but it also happens when only running smaller programs.

I would be really happy if someone found a solution to the problem, since I love all the compiz fusion effects and it is a drawback to turn compiz of every time I am doing something important on my computer.

You ought to try to troubleshoot more.  Open a console and run top all the time and keep it on the bottom or side of your screen so you can see if something is consuming 100% of either cpu or memory when the freeze occurs.  Also, have you search the log files in /var/log/* to see if any errors occur when it happens.  If so, try a google search for the exact error message.

HTH

---

