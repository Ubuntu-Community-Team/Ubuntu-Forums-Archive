---
title: "How to see htm &amp; html files"
date: 2005-12-08
forum: Desktop Environments
---

### Post by ShirishAg75 on 2005-12-08
Hi all,
      Each time I try to view an htm or html page it asks that its an executable file so should it run or display it. I wanna suppress this & it should directly open under FF. Can somebody tell me how I can do this.

---

### Post by Joe_CoT on 2005-12-08
from what i can see, that only happens if the file is set as executable.

if you set your htm and html files as not executable (chmod -x), it won't do that anymore .. though i'm at a lot as to how to recursively change only htm and html files on the entire system to not executable

---

### Post by RAOF on 2005-12-08
I'd suspect the commands you'd be after are: chmod -R -x *.htm and chmod -R -x *.html

---

### Post by Joe_CoT on 2005-12-08
yes, but that only works on the files in the base of the directory you're currently in. you could do:
```
sudo chmod -R -x /home
```
to change **everything** in that directory and subdirectories, but
```
 joe@jpt8:~$ cd /
joe@jpt8:/$ sudo chmod -R -x *.htm
chmod: cannot access `*.htm': No such file or directory
```

---

### Post by Joe_CoT on 2005-12-08
ah, here we go:

```
cd /
sudo chmod -x `find . -name '*.htm'`
sudo chmod -x `find . -name '*.html'`
```

i found it, and i know it works. someday i'll need to learn *why* this stuff works.

---

### Post by ShirishAg75 on 2005-12-09
thnx a lot guys, that's what I was actually after, the thing is I'm able to connect only through Windows at the present moment to the Net although hopefully soon, I would get an NIC & be able to surf my router through the NIC. then can save web pages natively in Linux.

---

