---
title: "vostro 3550 graphics cards"
date: 2011-12-23
forum: Dell Ubuntu Support (CLOSED)
---

### Post by dougleduck on 2011-12-23
I originally posted here,

[http://ubuntuforums.org/showthread.php?t=1899001](http://ubuntuforums.org/showthread.php?t=1899001)

about my ati graphics apparently not working, and only being able to use unity 2d. I realised this might have been a better place to post.

Thanks for any help in advance.

---

### Post by mikewhatever on 2011-12-27
Well, you provided no info on the graphics card neither here nor in the other thread. Can you do that. The output of something like the following would have been a good start:

```
lspci -knn | grep VGA -A2
```

---

### Post by dougleduck on 2012-04-10
I managed to get my graphics card working by installing the drivers from amd manually.

Instructions [here]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI#Manually_installing_Catalyst_12.3").

I didn't have any problems, and the instructions were easy to follow.

---

