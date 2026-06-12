---
title: "Performance"
date: 2005-09-13
forum: Desktop Environments
---

### Post by LucoB on 2005-09-13
Hi,

I have recently installed Kubuntu and i have noticed that it seems to hang for a a few seconds quite regularly. To give you an idea, if a cds playing it will sound like its got stuck. I thought this might be because i dont have a swap partion.

Ive been using Mandrake 9 and that worked fine. 

Ubuntu is installed on my laptop, 850Mhz, 256RAM and its on a 10Gb partion. not amazing i know but its all i need. 

Any ideas woud be great. 

Thanks.

---

### Post by agm642 on 2005-09-13
Having a swap partition is *HIGHLY* recommended...

---

### Post by heimo on 2005-09-13
Just weak ideas, but you need to start somewhere. First thing I'd do is check logfile /var/log/messages, anything happening during hangs?

Create swap file. Instructions on this thread:
[http://www.ubuntuforums.org/showthread.php?t=54307](http://www.ubuntuforums.org/showthread.php?t=54307)

Install laptop-mode
 ```
sudo apt-get install laptop-mode
```

---

