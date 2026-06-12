---
title: "Ubuntu 10.10 Freezing"
date: 2010-11-05
forum: Desktop Environments
---

### Post by different_guy on 2010-11-05
Hello my Ubuntu buds!

I have recently installed Ubuntu 10.10. And strange thing happens. Two or three times on a daily basis it just freezes and I do not know why. For example, I am doing some minor coding, surfing the web and just some regular stuff and suddenly, out of nowhere, it just freezes. I cannot force reboot, cannot shutdown, cannot run, cannot enter terminal, nothing. Totally helpless. Only physical reboot do the work. Never had this issue before. What do you think that is about mates?

Thank you!

---

### Post by nl4m on 2010-11-05
I'm not sure if it will help, but did you check the logs (/var/log/)? Maybe they can tell you exactly what application is causing the problem.

---

### Post by different_guy on 2010-11-05
Checked them mate, but have not found anything useful. But thanks!

---

### Post by fishbulb1022 on 2010-11-05
I had problems like that in 10.04. I think turning of compiz and just using metacity worked. I wanted my effects though so I updated my kernel using the .deb packeges [here]("http://kernel.ubuntu.com/~kernel-ppa/mainline/"). updating the kernel seemed to work and you always have the option to boot into old kernels if it doesn't work/causes problems. You might try running the 2.6.36 kernel. Its what I'm running now and its working fine for me.

---

### Post by different_guy on 2010-11-06
I will try that. Thank you fishbulb1022!

---

### Post by azertyh on 2010-11-06
hello,
i had a problem similar : [http://ubuntuforums.org/showthread.php?t=1606041](http://ubuntuforums.org/showthread.php?t=1606041)

---

### Post by arnavk007 on 2010-11-06
I think you should stop using gompiz and desktop effects
use only metacity
if It doesn't work then
install.    Sudo apt-get install lxde
if lxde runs fine that means gnome had some problem

---

### Post by @lpha on 2010-11-06
What kind of processor do you have? 

Is it AMD? Does it have a cool & quiet feature? If so, disable it! 

If your answer was yes to every question above, check out my article
[http://ubuntuforums.org/showthread.php?t=1589135](http://ubuntuforums.org/showthread.php?t=1589135)

---

### Post by different_guy on 2010-11-06
> **arnavk007 said:**
> I think you should stop using gompiz and desktop effects
use only metacity
if It doesn't work then
install.    Sudo apt-get install lxde
if lxde runs fine that means gnome had some problem

No mate. That is not the issue. But thank you for you effort!

@lpha, I have Intel processor.

azertyh, thanks for links. Useful to read it.

I think I found the source of the issue and that is Firefox. Most of the time the system freezes when I browse the Internet. Maybe I should install other Web browser?

---

### Post by different_guy on 2010-11-06
Firefox was the issue. I have installed Google Chrome and freezing is history.

---

### Post by Yuran321 on 2011-02-28
The issue is not solved for me. 
I use Ubuntu 10.10 on HP 6735s. My web browser is Google Chrome. But system freezes almost every time when I use browser and rhythmbox

---

### Post by Topazgb on 2011-03-24
My PC started freezing recently but I noticed a common factor.  It was always when using a lot of applications just after an update.  I know some updates don't say reboot but if I don't then often the PC freezes.:lolflag:

---

### Post by Matt Pellegrini on 2011-04-26
I think i have the same problem here, i will post in a couple of weeks when i have disabled firefox and let you know if freezing stops, if you're still following this thread can i ask if you're using a laptop or desktop?

---

