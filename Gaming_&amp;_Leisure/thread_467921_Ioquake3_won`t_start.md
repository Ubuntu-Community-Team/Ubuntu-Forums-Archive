---
title: "Ioquake3 won`t start"
date: 2007-06-08
forum: Gaming &amp; Leisure
---

### Post by orange2k on 2007-06-08
I reinstalled Feisty because I had some problems, and now after installing Ioquake3 it won`t start.
I can`t figure out why - I got it to work on my previous install. I checked the read/write permissions and when I click either ioquake3 or ioquake3.i386 nothing happens.

Plaease help...

---

### Post by Sockerdrickan on 2007-06-08
Start from terminal and show us the error :P

---

### Post by orange2k on 2007-06-08
Well it just says "command not found" when I type "ioquake3"...

I don`t know what I`m doing wrong, when I last installed it I didn`t have to run it from the terminal, I just doubleclicked on ioquake3 and it started...

edit: I ran "sh ioquake3" and the following error comes up "./ioquake3.i386: error while loading shared libraries: libopenal.so.0: cannot open shared object file: No such file or directory"

---

### Post by Sockerdrickan on 2007-06-08
sudo apt-get install libopenal0a

And you are ready to go!

---

### Post by orange2k on 2007-06-08
> **Tux0r said:**
> sudo apt-get install libopenal0a

And you are ready to go!

That did it!

Thank you so much!!!

---

### Post by Sockerdrickan on 2007-06-08
You are welcome, glad it helped ;)

---

### Post by kvarley on 2009-03-05
I get an error when trying to install the package!

> Package libopenal0a is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  libopenal1
E: Package libopenal0a has no installation candidate


I'm running Jaunty Jackalope.

When I do trying to run ioquake3 I get this error...

> ./ioquake3.i386: error while loading shared libraries: libopenal.so.0: cannot open shared object file: No such file or directory


---

### Post by kvarley on 2009-03-05
[SOLVED]

I had to manually download the .deb package instead of using Synaptic or Terminal.

[http://packages.ubuntu.com/hardy/i386/libopenal0a/download](http://packages.ubuntu.com/hardy/i386/libopenal0a/download)

---

