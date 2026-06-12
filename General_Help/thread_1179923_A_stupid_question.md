---
title: "A stupid question"
date: 2009-06-06
forum: General Help
---

### Post by madmaxou on 2009-06-06
I know it's a stupid question and emberassing that I cannot figure it out...
I tried to find the path of an application via whereis and then tried to pipe it into the cd command. I tried this:
```
whereis <application> | cd 
and this:
whereis <app> >> cd
```these and several more things i tried didn't work... thanks for help

---

### Post by Soul-Sing on 2009-06-06
whereis [option(s)] program_name(s)
: [http://www.linfo.org/whereis.html](http://www.linfo.org/whereis.html)

---

### Post by Legace on 2009-06-06
> **leoquant said:**
> whereis [option(s)] program_name(s)
: [http://www.linfo.org/whereis.html](http://www.linfo.org/whereis.html)

Thats not what he's (or she's) looking for.

---

### Post by konqueror7 on 2009-06-06
wouldn't it create a conflict since 'whereis' has the possibility of returning multiple results?

---

### Post by madmaxou on 2009-06-06
I'm looking for a way to change then directly into the dir from the output of whereis

---

### Post by Legace on 2009-06-06
> **konqueror7 said:**
> wouldn't it create a conflict since 'whereis' has the possibility of returning multiple results?

Thats what I was thinking.
For example, **whereis firefox** returs:
```
firefox: /usr/bin/firefox /usr/lib/firefox /usr/lib64/firefox /usr/share/firefox
```

---

### Post by kay-man on 2009-06-06
Also, it returns file names, not directories, so you can't directly cd into the result of whereis

---

### Post by madmaxou on 2009-06-06
which of them is the directory?

---

### Post by konqueror7 on 2009-06-06
if you want to find the directory, use 'locate' instead rather than 'whereis',,,'whereis' returns a file/program's specific url, while 'locate' returns the directory...

---

### Post by kay-man on 2009-06-06
Ah, I just learned something, too :)

---

### Post by bollix47 on 2009-06-06
You can try something like:

```
cd `locate filename`
```


The problem is you would only cd to the first folder it finds containing the filename and that may not be the folder you're looking for.

---

### Post by Soul-Sing on 2009-06-06
the ls command (which is used to list the [COLOR="Red"]contents[/COLOR] of any specified directory)
ex. ```
whereis ls firefox
```

---

### Post by madmaxou on 2009-06-06
> **bollix47 said:**
> You can try something like:

```
cd `locate filename`
```
The problem is you would only cd to the first folder it finds containing the filename and that may not be the folder you're looking for.

Cool thanks a lot

---

