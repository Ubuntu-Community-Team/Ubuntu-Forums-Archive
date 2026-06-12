---
title: "Enable dual core on Intel Core Cuo"
date: 2006-07-21
forum: Desktop Environments
---

### Post by McLaughysSN on 2006-07-21
Hey, this is my first post here on the forum. 

I'm new to linux but know my way around most operations. I am running version 6.06 ubuntu.

when i ran the system information program i realized im only running on one core. I looked for other threads on enabling the second core but didn't find much help. one of the suggesstions i ran across was to update my SMP kernel through synaptic but i couldn't find it. 

Anyone want to take a whack at this for me?

Thanks

---

### Post by -Phi- on 2006-07-21
Here is a thread that talks about smp: [http://ubuntuforums.org/showthread.php?t=212685](http://ubuntuforums.org/showthread.php?t=212685)

The command ```
sudo aptitude update && sudo aptitude install linux-686-smp
``` should install the correct kernel, and the thread talks about configuration (sorry, I don't know about dual core myself).

Welcome to the forums, and hope this helps!

- Phi

---

### Post by McLaughysSN on 2006-07-21
Perfect, I appreciate it

---

### Post by Dubbayoo on 2006-07-21
I just noticed that I have linux-image-2.6.15-25-686 installed of linux-686-smp. My smp appears to be working fine. What's the deal with that? 

[http://dubbayoo.net/files/pics/screenshots/dvdauthor.jpg](http://dubbayoo.net/files/pics/screenshots/dvdauthor.jpg)

---

### Post by patrickfromspain on 2006-07-21
no deal.. there isn't a 686-SMP kernel anymore. Instead of that, the standard 686 kernel has SMP enabled and that's it.

---

