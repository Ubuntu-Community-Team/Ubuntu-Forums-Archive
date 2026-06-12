---
title: "Disappearing desktop. WHAT THE???"
date: 2006-07-30
forum: Desktop Environments
---

### Post by muz1 on 2006-07-30
This morning, I turned my computer on to check my email. It went through the initial startup and then where it showed the brown ubuntu logo... some more scrolling white text... then shell. No GUI. I am at a loss as I don't know waht has happened. Is there some way of switching back to the GUI mode? What could have caused it to disappear or switch?
Any help REALLY appreciated.
Cheers
muz

---

### Post by Dr. Nick on 2006-07-30
preform any updates prior to this? maybe something updated and caused a problem.

logon at the termainal as your regular user and run 

startx

note any errors and post a more detailed message

---

### Post by taurus on 2006-07-30
And if "startx" at the prompt returns with an error message, then maybe you need to reconfigure your X again with

```

sudo dpkg-reconfigure xserver-xorg

```
Did you happen to upgrade your xorg and forgot to reinstall nVidia driver for your graphic card again???

---

