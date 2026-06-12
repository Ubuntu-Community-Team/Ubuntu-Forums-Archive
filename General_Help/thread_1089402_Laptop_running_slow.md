---
title: "Laptop running slow"
date: 2009-03-07
forum: General Help
---

### Post by enverhoxha on 2009-03-07
I know there should be no registry or fragmentation problems with Ubuntu, or virus infections. 
Nevertheless, over 5 or 6 months, my HP laptop with Ubuntu 8.04 grew slower. The regular Ubuntu updates don't seem to improve the system, but rather to make it noticeably lazier. Firefox, for instance, starts and closes with annoying delays. 
And the system monitor frequently shows the CPUs (Intel Core2Duo) loaded alternatively at almost 100% without any special job to do (just browsing and PDF reading). 
What could be the problem here? Is there any kind of maintenance and/or testing software I should use?

---

### Post by martrn on 2009-03-07
You could goto [http://ubuntuforums.org/showthread.php?t=89491]("http://ubuntuforums.org/showthread.php?t=89491") and make sure you are not loading any unecessary services while booting up.  Remove any unnecessary services.

Open a terminal and type ```
top
```

Find out what processes are causing ubuntu to accelerate you cpu to 100%, and  what process are using a lot of memory in your system.

Type
```
sudo kill 7356
```
if process 7356 is causing your system to hog cpu time.

Firefox3 cause a lot of cpu if flash is running in multiple tabs or windows.  Strange enough I find opening pdf in adobe reader (adobes version) less resource hungry than any other pdf reader.  It much better than flash.

Does anything other than firefox cause your problems ?

---

### Post by murataht on 2009-03-07
It is not ubuntu, i guess, it is the programs or services.

If you are using evince, it is heavy, too, sometimes. especially when you open several pdf. try other pdf viewers. 
and firefox is a heavyweight, with flash it is unbearable. So, I have installed "flash blocker" plugIn to the firefox. And no flash runs without my permission. 

plus, check if you have tracker enabled. tracker is a resource hog, too. it starts itself from time to time, and eats up your cpu at almost 100%. I have not disabled it, because I frequently look for files using it. So, when I am working seriously, if tracker starts to run, I will kill it as explained in the previous post. 

hope this helps.

---

### Post by enverhoxha on 2009-03-07
Except for Firefox and Evince, nothing yet. Thank for the advice.

---

### Post by enverhoxha on 2009-03-07
For tracker I don't know. But if I look in System Monitor for processes running, there's almost nothing. Everything is "sleeping". And still...

---

