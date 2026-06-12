---
title: "programming in ubuntu........"
date: 2009-06-01
forum: General Help
---

### Post by muctadir on 2009-06-01
in windows we got a c compiler turbo c. this is really very helpful for those who has just started to learn c language. i want to know if there is any similar programming tool for ubuntu????

---

### Post by LoneWolfJack on 2009-06-01
gcc

if you're looking for a development environment, take a look at eclipse.

---

### Post by _Purple_ on 2009-06-01
Type this in terminal
```
sudo apt-get install build-essential
```

This will install the compiler and other necessary packages.

---

### Post by ActiveFrost on 2009-06-01
Install :
```
sudo apt-get install build-essential
```
Compile :
```
gcc Source.c -o Output
```

---

### Post by saidinesh5 on 2009-06-01
for a beginner , i would suggest the nice little IDE called GEANY

may be you might even like this one called CODE::BLOCKS ..

both of them can be found in synaptic ..
Best of luck :) (Y)

---

### Post by muctadir on 2009-06-01
actually i mean a environment that is user friendly and has a number of help topics. like turbo c has.....

---

### Post by munky99999 on 2009-06-01
Try out Wine or go with something like...

[http://helpforlinux.blogspot.com/2008/12/install-borland-turbo-c-in-ubuntu.html](http://helpforlinux.blogspot.com/2008/12/install-borland-turbo-c-in-ubuntu.html)

---

### Post by mb_webguy on 2009-06-01
A number of very nice [C/C++ IDEs]("http://en.wikipedia.org/wiki/Comparison_of_integrated_development_environments#C.2FC.2B.2B") are available for Linux.  Most are in the Ubuntu repositories.

I'd suggest looking into [Code::Blocks]("apt://codeblocks"), [KDevelop]("apt://kdevelop"), [MonoDevelop]("apt://monodevelop"), [Sun Studio]("http://developers.sun.com/sunstudio/"), and NetBeans (with the C/C++ pack available from the [NetBeans website]("http://www.netbeans.org/")).

And yes, you could also try installing Turbo C under Wine, though that seems to be an awkward way of doing things when there are numerous Linux-native IDEs available.

---

### Post by Mirge on 2009-06-01
> **saidinesh5 said:**
> for a beginner , [B]i would suggest the nice little IDE called GEANY
[/B] 
may be you might even like this one called CODE::BLOCKS ..

both of them can be found in synaptic ..
Best of luck :) (Y)

I can't say enough good about Geany as well. Geany 0.17 (latest) is available in .deb form on launchpad... it's a dang fine lightweight IDE that I use for C, PHP, HTML and JS.

Builds are at the bottom: [https://launchpad.net/ubuntu/+source/geany/0.17-0ubuntu1](https://launchpad.net/ubuntu/+source/geany/0.17-0ubuntu1)

---

