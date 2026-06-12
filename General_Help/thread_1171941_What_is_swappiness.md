---
title: "What is swappiness?"
date: 2009-05-27
forum: General Help
---

### Post by charleskw on 2009-05-27
So, i came across this command for the terminal that i was tokd would speed up my system the code is:  sudo sysctl -w vm.swappiness=10   what exactly does this code do?

---

### Post by salvachn on 2009-05-27
It is the amount of swapping, i.e. the frequency at which the OS swaps to disk. This 'swappiness' is a new variable in Linux kernel 2.6 to which you can assign values from 0 to 100. If you have copious amounts of ram, this needs to be set to a lower value. I use 5 myself.

---

### Post by redmk2 on 2009-05-27
> **charleskw said:**
> So, i came across this command for the terminal that i was tokd would speed up my system the code is:  sudo sysctl -w vm.swappiness=10   what exactly does this code do?

It changes the default amount of swappiness.  What is swappieness?  See [_here_]("http://unixfoo.blogspot.com/2007/11/linux-performance-tuning.html").

In this case Google really is your friend.  See [_here_]("http://www.google.com/search?hl=en&ei=QQIeSouGFISKtAPEwNiLCQ&sa=X&oi=spell&resnum=1&ct=result&cd=1&q=swappiness+linux&spell=1")

---

### Post by keypox on 2009-05-27
> **redmk2 said:**
> It changes the default amount of swappiness.  What is swappieness?  See [_here_]("http://unixfoo.blogspot.com/2007/11/linux-performance-tuning.html").

In this case Google really is your friend.  See [_here_]("http://www.google.com/search?hl=en&ei=QQIeSouGFISKtAPEwNiLCQ&sa=X&oi=spell&resnum=1&ct=result&cd=1&q=swappiness+linux&spell=1")

yeah but if he didnt post this i would have never heard of swappieness and probably others will now learn about it.

---

### Post by redmk2 on 2009-05-27
> **keypox said:**
> yeah but if he didnt post this i would have never heard of swappieness and probably others will now learn about it.

Sure you would have.  As soon as it became important. :D

Most of the time swappiness is not something to play with.  BTW -- decreasing swappieness number does not guaranty that the system will reduce the amount swappieness.  It is only one of many esoteric settings that control the swap.

---

### Post by salvachn on 2009-05-28
@ redmk2
Thanks for clarifying the point! I was thinking otherwise!

---

