---
title: "Image to hex file converter"
date: 2013-05-13
forum: Education &amp; Science
---

### Post by akhilvarma on 2013-05-13
Hey, I'm tring to convert an image file (bmp, gif) to a long string of hex numbers (hex file). I'm planning to upload the image in this form to an LCD. Is there any software available to do the same?

---

### Post by papibe on 2013-05-13
Hi akhilvarma. Welcome to the forum ):P

Yes. Take a look at the command line 'od'. For instance:
```
od -x file.gif
```
For more details:
```
man od
```
Hope it helps. Regards.

---

### Post by akhilvarma on 2013-05-13
> **papibe said:**
> Hi akhilvarma. Welcome to the forum ):P 

Thanks papibe! :) I'm really a newbie to ubuntu..but I'm luvin it.

```
od -x file.gif
``` 

Thanks a lot for the code.:) It works fine.

---

### Post by papibe on 2013-05-14
:) Glad I could help. Come here often and have fun!

When you have the chance, please mark the thread as solved ([here]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")'s how).

Regards.

---

