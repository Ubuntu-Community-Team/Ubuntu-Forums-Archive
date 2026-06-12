---
title: "Please help me 7z"
date: 2009-01-17
forum: General Help
---

### Post by gate9 on 2009-01-17
When i try this (see in attach) i have error. How i can unzip 7z???

---

### Post by kesre on 2009-01-17
try this site

[http://ubuntuforums.org/showthread.php?t=263825]("http://ubuntuforums.org/showthread.php?t=263825")


Essentially

> 

```

sudo apt-get install p7zip
```

You've got to activate universe repositories (probably easiest to do it in synaptic) first though.

change directories to file location
> 
then to unzip stuff you use the command:

```
7z x (Filename)
```



---

### Post by dnairb on 2009-01-17
The problem, from actually *looking* at the screenshot attached, is the "dpgk was interrupted...." bit.

As suggested, type

```
sudo dpkg --configure -a
```

in terminal.

---

### Post by theozzlives on 2009-01-17
Use the archive manager.

---

### Post by kesre on 2009-01-17
> **dnairb said:**
> The problem, from actually *looking* at the screenshot attached, is the "dpgk was interrupted...." bit.

As suggested, type

```
sudo dpkg --configure -a
```

in terminal.

Oops, can't see how I missed that one #-o

Thanks for catching that dnairb =D

---

