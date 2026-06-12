---
title: "Umbrello UML Error in Exit Process"
date: 2010-01-23
forum: Desktop Environments
---

### Post by acho on 2010-01-23
[IMG]http://yadi1blogs.files.wordpress.com/2010/01/doc1.gif[/IMG]


I had error like the picture below... anyone can help me fix the problem??

I was importing my project into Umbrello then it's going ok after i create everything. Then after i close my project. It's look like that....

I was looking for some help with kde official website [http://bugs.kde.org]("http://bugs.kde.org") but i can't send error report to them....

 regards,

Yadi Acho

---

### Post by Zorael on 2010-01-24
Try starting it from a terminal with these commands, then exit it again. If it doesn't crash now, it's caused by [a bug in libc6](https://bugs.kde.org/show_bug.cgi?id=196207).
```
$ export QT_NO_GLIB=1
$ export MALLOC_CHECK_=0
$ umbrello
```

---

### Post by acho on 2010-01-26
[IMG]http://ubuntuforums.org/picture.php?albumid=1637&pictureid=5553[/IMG]

Thx for your help zorael,,

But still error look like that, I try to connect to bugs.kde.org.... is there any way to fix problem, thx......

---

### Post by bertram_wooster on 2010-02-24
I am having this problem too.

Also, Umbrello is hanging when I import some of my classes (c++), but this may be unrelated.

---

### Post by bertram_wooster on 2010-02-25
I continued to have this problem even with Zorael's suggested fix, so instead I tracked down an older version and installed that. Found here:

[URL]
packages.debian.org/lenny/umbrello
[/URL]

I know it isn't an ideal solution, but this version hasn't thrown the SIGSEGV fault yet and imports my badly written c++ just fine without hanging.

One thing I didn't mention was that I am using Jaunty for amd64 machines (ubuntu-9.04-amd64).

---

