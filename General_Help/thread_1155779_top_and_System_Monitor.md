---
title: "top and System Monitor"
date: 2009-05-11
forum: General Help
---

### Post by jonnymccullagh on 2009-05-11
If someone could shine some light on this I'd appreciate it.
The system monitor applet is showing an Opera process as using 46 %CPU. Running top it shows 91 %CPU. It is a dual core processor so I am presuming that system monitor is averaging it across the 2 processors. Am I wrong? and how can I get top to show the same values as System Monitor?
Thanks,
jonny

---

### Post by skymera on 2009-05-11
Yes i think System Monitor averages on the amount of CPU cores you have.

If Firefox for example uses 100% of a copre for me, System Monitor shows 25%

---

### Post by jonnymccullagh on 2009-05-11
Thanks, reassuring. Is there some keyboard wizardry that will do the same in top?

---

### Post by skymera on 2009-05-11
Not sure.

I prefer htop.

it#s in the repos 

```
 sudo apt-get install htop 
```
Run by typing htop in terminal. I find it's much easier to understand than top

---

