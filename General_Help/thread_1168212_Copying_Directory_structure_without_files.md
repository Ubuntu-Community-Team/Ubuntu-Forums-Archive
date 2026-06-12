---
title: "Copying Directory structure without files"
date: 2009-05-23
forum: General Help
---

### Post by ffxigotenks on 2009-05-23
I've been trying to thin down my music collection and I know that I have a lot of duplicate files (same song in both m4a and mp3 format, for example) but I like how they are currently structured, so I want to copy all the subfolders without the files, I was wondering if anyone knows of a way to do it, or failing that, a way to sort an excessively large music collection

---

### Post by SuperSonic4 on 2009-05-23
Well you can delete a filetype from a directory, something like ```
rm -v *.m4a
```

You may want to pass an -i flag to prompt you to make sure it works and remember to cd to the directory you wan't.

Edit 1: the -s flag will make symbolic links, which could be removed I suppose

Edit 2: 
```
mkdir /where/you/wantem
cd /source/dir
find * -type d -exec mkdir /where/you/wantem/\{\} \; 
```

I tested it out on Avenged Sevenfold and it worked

---

### Post by colau on 2009-05-23
> **SuperSonic4 said:**
> Well you can delete a filetype from a directory, something like ```
rm -v *.m4a
```

You may want to pass an -i flag to prompt you to make sure it works and remember to cd to the directory you wan't.

Edit 1: the -s flag will make symbolic links, which could be removed I suppose
Is there any command to copy directory recursively without the files inside it?

---

### Post by SuperSonic4 on 2009-05-23
Yeah, I edited it into my previous post as edit 2 :)

I'm not sure how to avoid the first step of making the directory but it shouldn't be too hard to make the parent directory (or just use ~ or another mounted one)

---

### Post by albinootje on 2009-05-23
> **SuperSonic4 said:**
> 
```
mkdir /where/you/wantem
cd /source/dir
find * -type d -exec mkdir /where/you/wantem/\{\} \; 
```

I tested it out on Avenged Sevenfold and it worked

Looks interesting, but what about those annoying directories with spaces in the directory name ? That's usually a problem in scripts afair.

---

### Post by SuperSonic4 on 2009-05-23
> **albinootje said:**
> Looks interesting, but what about those annoying directories with spaces in the directory name ? That's usually a problem in scripts afair.

Works fine :) - it copies the Allman Brothers Band without any problems. I sent mine to a folder called testing XD

---

### Post by colau on 2009-05-23
> **SuperSonic4 said:**
> Well you can delete a filetype from a directory, something like ```
rm -v *.m4a
```

You may want to pass an -i flag to prompt you to make sure it works and remember to cd to the directory you wan't.

Edit 1: the -s flag will make symbolic links, which could be removed I suppose

Edit 2: 
```
mkdir /where/you/wantem
cd /source/dir
find * -type d -exec mkdir /where/you/wantem/\{\} \; 
```

I tested it out on Avenged Sevenfold and it worked

Would you please tell how these options work?
```

find * -type d -exec mkdir /where/you/wantem/\{\} \; 
```
These options below:
```

\{\} \;

```

---

### Post by albinootje on 2009-05-23
> **SuperSonic4 said:**
> Works fine :) - it copies the Allman Brothers Band without any problems. I sent mine to a folder called testing XD
Excellent :)

---

### Post by SuperSonic4 on 2009-05-24
> **colau said:**
> Would you please tell how these options work?
```

find * -type d -exec mkdir /where/you/wantem/\{\} \; 
```
These options below:
```

\{\} \;

```

I've no idea, I just googled the code

---

### Post by andrew.46 on 2009-05-25
Hi colau,

> **colau said:**
> Would you please tell how these options work?
```

find * -type d -exec mkdir /where/you/wantem/\{\} \; 
```
These options below:
```

\{\} \;

```

This is part of the 'find ....... -exec' syntax. The brackets {} are replaced by the current file being processed and in this case the brackets have been 'escaped' to protect them from shell expansion. If you were interested in the usage of 'find' have a look at a guide I wrote a couple of weeks ago:

Linux Basics: A gentle introduction to 'find'
[http://ubuntuforums.org/showthread.php?t=1128937](http://ubuntuforums.org/showthread.php?t=1128937)

All the best,

Andrew

---

### Post by ffxigotenks on 2009-06-07
sorry I haven't replied in a while, but thank you, supersonic, for the help, it worked beautifully

---

