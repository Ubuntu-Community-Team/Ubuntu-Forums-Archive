---
title: "&quot;look&quot; command"
date: 2005-09-13
forum: Desktop Environments
---

### Post by cwaldbieser on 2005-09-13
When I tried to use the "look" command today, I received an error:
```

$ look courteous
look: /usr/share/dict/words: No such file or directory

```
So I did an ls -al of /usr/share/dict/words, and it turns out it is a broken link to /etc/dictionaries-common/words.  The folder is there, just the "words" file is missing.  Any idea if I am missing some package that would install this file?

Thanks.

---

### Post by heimo on 2005-09-13
On my system:
 ```
ls -l /usr/share/dict/*
``` 
 > -rw-r--r--  1 root root 908846 2004-06-20 06:23 /usr/share/dict/american-english
-rw-r--r--  1 root root 906950 2004-06-20 06:23 /usr/share/dict/british-english
lrwxrwxrwx  1 root root     30 2005-09-07 07:24 /usr/share/dict/words -> /etc/dictionaries-common/words
 

If you don't have these, you can install one of the packages starting with w on this list: [http://packages.ubuntu.com/hoary/text/]("http://packages.ubuntu.com/hoary/text/") wamerican, wbritish...

On my system:
 ```
ls -l /etc/dictionaries-common/words
``` 
 > lrwxrwxrwx  1 root root 31 2005-08-19 08:05 /etc/dictionaries-common/words -> /usr/share/dict/british-english
 

It's possible that all you need to do is:
 ```
sudo ln -s /etc/dictionaries-common/words /usr/share/dict/american-english
```

---

### Post by cwaldbieser on 2005-09-14
[QUOTE=heimo]On my system:
 ```
ls -l /usr/share/dict/*
``` 
  

If you don't have these, you can install one of the packages starting with w on this list: [http://packages.ubuntu.com/hoary/text/]("http://packages.ubuntu.com/hoary/text/") wamerican, wbritish...

On my system:
 ```
ls -l /etc/dictionaries-common/words
``` 
  

It's possible that all you need to do is:
 ```
sudo ln -s /etc/dictionaries-common/words /usr/share/dict/american-english
```[/QUOTE]
Thanks.  Installing the wamerican package installed the dictionary and set up the link.

---

