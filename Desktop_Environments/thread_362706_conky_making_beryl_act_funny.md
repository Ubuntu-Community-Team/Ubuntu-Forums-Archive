---
title: "conky making beryl act funny"
date: 2007-02-15
forum: Desktop Environments
---

### Post by ntense on 2007-02-15
so i recently installed both beryl and conky on a fresh edgy system and ive noticed that when conky refreshes its information that whatever effect thats going on at that time will studder, or delay if you will. i have the exact same setup on my laptop and it dosent have that problem. i love conky and i dont want to switch back to gkrellm. has anyone else had this problem? can you point me to a possible solution? any help would be great. thanks in advance

---

### Post by shareMenaPeace on 2007-02-16
> **ntense said:**
> so i recently installed both beryl and conky on a fresh edgy system and ive noticed that when conky refreshes its information that whatever effect thats going on at that time will studder, or delay if you will. i have the exact same setup on my laptop and it dosent have that problem. i love conky and i dont want to switch back to gkrellm. has anyone else had this problem? can you point me to a possible solution? any help would be great. thanks in advance

Hmm maybe set these in .conkyrc works here 
```
own_window yes
own_window_type override
own_window_transparent yes
double_buffer yes
```

---

### Post by eXisor on 2007-02-16
I too use beryl and conky, and **had** the same problem you mention.  (I have all the good stuff mentioned by shareMenaPeace).

I think it is happens when conky resizes itself; it has to take a new snapshot of the desktop, and then paint that as the background to achieve its transparency effect. This produces the notable lag, and in my case, a momentary black flash.

The fix is quite easy. 

TIP: 

a) Set the maximum width to the largest width you want to allow.
b) Set minimum size to the width in a) and the height to the height of your screen (excluding the panels).

In effect this means conky never resizes, so it doesn't have to take the snapshot of the desktop background more than once.

This gives me a flashless conky with beryl.

---

