---
title: "How to rename many files with a short script?"
date: 2006-07-10
forum: Desktop Environments
---

### Post by leeyee on 2006-07-10
Hi guys,
I have many files in a folder, all of them are in a same style, which have a prefix "My-*", just for example:

My-abc.mp3
My-ghgh.mp3
My-fefaea.mp3
.
.
.

Now I want to rename all of them, and I'd like to remove the prefix from file names. However, I'm a fresh man of BASH programming, knew very little about that, anyone can help me a script?
Sorry for my English, I hope you can understand me.
Thanks!

---

### Post by halfvolle melk on 2006-07-10
Hi,
Check out "man rename". I modified the example:
```
rename &#8217;s/\My-$//&#8217; My-*
```
Please note: I didn't test it! You may wan't to back the dir up before trying.

---

### Post by leeyee on 2006-07-10
Hello,
Thanks for your reply! But rename doesn't support multi-characters I think, this is help:
```

[leeyee@myUbuntu:~/My music/&#21608;&#26480;&#20262;/jay (copy)]$ for i in *; do mv $i ${i#&#21608;&#26480;&#20262;-};done


```

---

