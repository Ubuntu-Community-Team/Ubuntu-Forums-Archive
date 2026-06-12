---
title: "Ubuntu/Firefox Burning Up My CPU"
date: 2009-04-05
forum: General Help
---

### Post by uzzo2 on 2009-04-05
I was just wondering if anyone else had this problem and how they resolved it. I have my system temps on my top panel and sometimes i'll notice my CPU temp has gone up between 50 and 60 degrees celcius. I run "top" in the terminal and it seems to be firefox burning it up running at 100% or more. I can either refresh the page or close the browser all together and the temp will start coming back down to what the rest of the system is. So, is it a firefox or ubuntu or perhaps just certain web pages causing the problem? Thanks in advance for any advice.

---

### Post by |Porsche on 2009-04-05
I am running firefox 3.08 and have no issues. It might be a particular webpage.

---

### Post by wpshooter on 2009-04-05
Are you saying that your temperature is **_INCREASING by_** 50 to 60 degrees or that it is going to/reading 50 to 60 degrees ?

---

### Post by uzzo2 on 2009-04-05
> **wpshooter said:**
> Are you saying that your temperature is **_INCREASING by_** 50 to 60 degrees or that it is going to/reading 50 to 60 degrees ?
No, it's just getting up to between 50 and 60 degrees, yesterday it ran up to almost 70 degrees. But it was pretty warm in my house, around 80 degrees fahrenheit.

---

### Post by wpshooter on 2009-04-05
If this a desktop or a laptop ?

In any case, get a portable fan of some type and position it so that it can blow directly on the computer and see if this temperature rise stops.

Also, how / what type software are you using to measure the temperature ?  This could be a problem with that software.

---

### Post by uzzo2 on 2009-04-05
> **wpshooter said:**
> If this a desktop or a laptop ?

In any case, get a portable fan of some type and position it so that it can blow directly on the computer and see if this temperature rise stops.

Also, how / what type software are you using to measure the temperature ?  This could be a problem with that software.
I can't really remember, possibly lm-sensors, they're located on the top panel, 3 of them. I had a whale of a time trying to figure which temp was which, had to go to bios for that.

---

### Post by Yashiro on 2009-04-05
It's probably Shockwave Flash or Java causing the problem.
Either the actual Flash/Java content is CPU intensive OR you're running nspluginwrapper.
This 'plugin' spawns a process called npviewer.bin that is not getting terminated after running Flash/Java/whatever crud plugin.

---

### Post by uzzo2 on 2009-04-05
I've noticed it more on certain websites for example, fox news channel. I can go on the fox website and say watch a video from there and it don't take no time at all. CPU temp is up there around 50-60 degrees.

---

### Post by uzzo2 on 2009-04-05
> If this a desktop or a laptop ?
It's a desktop

---

