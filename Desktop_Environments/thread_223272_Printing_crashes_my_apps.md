---
title: "Printing crashes my apps"
date: 2006-07-26
forum: Desktop Environments
---

### Post by jvalcke on 2006-07-26
Hello,

I recently installed Ubuntu on my system. Printing used to work flawlessly. However since a few days, whenever I want to print from an application the application freezes. I treid accessing the 'print-manager' through the System  Menu (System -> Administration -> Printing) but that application won't even start up. I also tried to connect to the cups manager with my browser (port 631) but I get nothing, the page never loads.

I've restarted the cups daemon, but that didn't help. I even rebooted my machine. same thing. I've checked the cups error_log file. Didn't find anything special there.

Any other clues?

---

### Post by cilynx on 2006-07-26
Hey,

I know it's a Win* type of solution, but did you try removing (completely) and reinstalling cups?  

```

$ sudo apt-get remove --purge cupsys* && sudo apt-get install cupsys

```

This will blow away CUPS and all of your configuration of it.  Then it will install fresh.  Beware:  If it took you a week to get CUPS working in the first place, this may not be the best method for you...

Edit, addition: 
Also, this type of thing tends to not "just happen".  You may want to do some stress testing to see if you've got some hardware considering failure.  I would look at HD and RAM personally, especially if the fix above actually works.

---

### Post by jvalcke on 2006-07-27
thanks, re-installing did the trick. Very weird.

-Jeroen-

---

