---
title: "Help writing a basic script"
date: 2009-03-22
forum: General Help
---

### Post by Oreo Priest on 2009-03-22
Hello,

I am fairly new to coding, and completely new to shell scripts. I can only code in C.

What I want is to write a program or script to break this monstrous text file, containing all of Moby-Dick, ( [http://www.gutenberg.org/files/2701/2701.txt](http://www.gutenberg.org/files/2701/2701.txt) ) into one small text file for each chapter. In principle, this should be easy; each chapter begins with CHAPTER X. in block caps, so it should be easy for the computer to recognize.

In any case, I don't really know what the appropriate tools would be, or if it should be done as a shell script or a program or what.

Any help is appreciated. If this is not the most appropriate place to ask the question, please let me know where is.

Thanks.

---

### Post by kaibob on 2009-03-22
> **Oreo Priest said:**
> In any case, I don't really know what the appropriate tools would be, or if it should be done as a shell script or a program or what.

I believe awk might be a good tool to tackle this job. I'm new to awk, but I think the process would be to have awk locate the line number (NR) of CHAPTER 1 and then the line number of CHAPTER 2. That chapter would then be printed to a file somewhat as follows:

```
awk 'NR==1,NR==100' mobydick > chapter1
```

I would probably tackle this within a for loop, although I suspect it might be doable as a 1-liner. There are some real awk experts in this forum who may be able to help.

If you want to have a go at this yourself, the following is the awk manual:

[http://www.gnu.org/software/gawk/manual/gawk.html](http://www.gnu.org/software/gawk/manual/gawk.html)

---

### Post by ghostdog74 on 2009-03-22
use csplit
```

# csplit file /^CHAPTER/ '{*}'

```

---

### Post by kaibob on 2009-03-22
> **ghostdog74 said:**
> use csplit
```

# csplit file /^CHAPTER/ '{*}'

```

Can't get any better than that :p  I'm new to this, but I'm still surprised by all the specialized commands that make things easier for us.

---

### Post by Oreo Priest on 2009-03-22
Wow, csplit is the perfect tool. Thanks!

Also, I'm going to try to use awks to give the chapters titles. Thanks to you too!

---

