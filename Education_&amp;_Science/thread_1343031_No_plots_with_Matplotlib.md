---
title: "No plots with Matplotlib"
date: 2009-12-01
forum: Education &amp; Science
---

### Post by kbaumen on 2009-12-01
Hi

I've just picked up Matplotlib and am now trying to get my head around it. I am new to python so this might me a stupid question with a simple solution, however, someone has said that there are no stupid questions.

I am trying to make the most simple plot.

```
>>> from pylab import *
>>> plot ([1,2,3])
```

However, I just get

```
[<matplotlib.lines.Line2D object at 0x2ae5f10>]
```

No new windows appear. There is no plot. Could someone please tell me what am I doing wrong? Or maybe I am missing some packages? I did however go through this [COLOR=Blue]_[list]("http://packages.ubuntu.com/jaunty/python-matplotlib")_[/COLOR] and it appears that I have all of the packages listed.

Is there maybe some default output directory?

Cheers for any answers.

---

### Post by cdnaerogeek on 2009-12-01
As a first step, try typing in ```
>>> show()
``` right after your plot command and see if that displays a plot.

---

### Post by kbaumen on 2009-12-01
Hmm... that was quite a simple solution. The tutorial didn't mention that. Anyway, cheers.

---

### Post by tyrael_ on 2011-09-13
> **cdnaerogeek said:**
> As a first step, try typing in ```
>>> show()
``` right after your plot command and see if that displays a plot.

I did it but I cannot take any feedback. I use ipython (ver. 0.11) with qtconsole and I use 10.10.
I made reinstall from pip, and then remove and install with aptitude, now I am trying with python setup module.

---

### Post by Berto88 on 2011-09-14
using

```
>>>ion()
```

will mean that you don't need to type show()

If you are using ipython you can also run start the session with 

ipython -pylab

this automatically imports pylab as well. I think it also means you don't have to type show()

---

