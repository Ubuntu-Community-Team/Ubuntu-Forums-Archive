---
title: "Creating global commands"
date: 2005-09-15
forum: Desktop Environments
---

### Post by plefno on 2005-09-15
I'm not even sure what you call this, but say you install a piece of software by compiling it yourself or any other way than Synaptic.  For example, I just installed the new Firefox 1.5 Beta myself and removed the older version that I had installed from a package on Synaptic.  With the Synaptic package, I could run firefox by simply typing "firefox" into any terminal regardless of what directory I was in.  How do I go about creating a command like that myself with the version I've installed myself?  Hopefully this makes sense to someone.  Thanks.

---

### Post by plefno on 2005-09-15
Nevermind, I figured it out.  In case there is anyone else who happens to want to know this.  You can just put a symlink to the application in the /usr/bin directory.  Thanks anyway.

---

### Post by bsussman on 2005-09-15
Actualy, /usr/local/bin might be a more proper place.

Although it is one of those long debates, and history holds several competing schemes, the authority I go by is 

[www.debian.org/doc/packaging-manuals/fhs/](www.debian.org/doc/packaging-manuals/fhs/)

---

### Post by matthew on 2005-09-15
[QUOTE=bsussman][http://www.debian.org/doc/packaging-manuals/fhs/]("http://http://www.debian.org/doc/packaging-manuals/fhs/")[/QUOTE]
I clicked on that link and was redirected to: [http://www.microsoft.com/](http://www.microsoft.com/)
No lie. I have no idea why.

---

### Post by bsussman on 2005-09-15
I dont understand - I fell down that rat hole too!

ok - use google "debian standard directory" 

The second link down (indented says file system hierarchy

I gonna try to figure out how Uncle Bill got in there!!

---

### Post by Fiyawerx on 2005-09-15
[QUOTE=matthew]I clicked on that link and was redirected to: [http://www.microsoft.com/](http://www.microsoft.com/)
No lie. I have no idea why.[/QUOTE]

It's because the link has two http://'s in it :
*[http://http//](http://http//)*[www.debian.org/doc/packaging-manuals/fhs/](www.debian.org/doc/packaging-manuals/fhs/)

try this one:
[http://www.debian.org/doc/packaging-manuals/fhs/](http://www.debian.org/doc/packaging-manuals/fhs/)

---

### Post by matthew on 2005-09-15
[QUOTE=Fiyawerx]It's because the link has two http://'s in it :
*[http://http//](http://http//)*[www.debian.org/doc/packaging-manuals/fhs/](www.debian.org/doc/packaging-manuals/fhs/)

try this one:
[http://www.debian.org/doc/packaging-manuals/fhs/](http://www.debian.org/doc/packaging-manuals/fhs/)[/QUOTE]
Thanks. If I had been paying attention I might have caught that. Glad you were.

---

### Post by bsussman on 2005-09-16
[QUOTE=matthew]Thanks. If I had been paying attention I might have caught that. Glad you were.[/QUOTE]

](*,)

Seemed to be a booger to correct too...

---

