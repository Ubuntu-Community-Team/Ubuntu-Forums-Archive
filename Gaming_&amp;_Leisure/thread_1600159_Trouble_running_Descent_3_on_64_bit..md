---
title: "Trouble running Descent 3 on 64 bit."
date: 2010-10-18
forum: Gaming &amp; Leisure
---

### Post by bobmatino17 on 2010-10-18
well, i love the descent series and always have.
i started using 64 bit ubuntu on my shiny new computer, and to my complete and utter horror, an error message comes up when i try to install Descent 3.:(
```
This installation doesn't support glibc-2.1 on x86_64
```
is there anyway besides downloading a 32 distro that i can run D3.

---

### Post by bobmatino17 on 2010-10-20
Please help me?

---

### Post by Brebs on 2010-10-20
Try [http://ubuntuforums.org/archive/index.php/t-196938.html](http://ubuntuforums.org/archive/index.php/t-196938.html)

---

### Post by bobmatino17 on 2010-10-20
ahh, thank you for your help, but i found a thread with the same solution 'bout the same time you posted this one. thanks again.

---

### Post by bobmatino17 on 2010-10-21
however... it runs, with no sound...

---

### Post by Perfect Storm on 2010-10-21
Run the game through the terminal with padsp command.

---

### Post by bobmatino17 on 2010-10-21
Worked Perfectly! Thank You very much!

---

### Post by schmidtbag on 2011-06-06
if you're an alsa user, edit /etc/modules.conf and add:
snd-pcm-oss
snd-mixer-oss

---

