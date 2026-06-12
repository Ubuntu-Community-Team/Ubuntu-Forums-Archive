---
title: "Can't install .sh files"
date: 2007-01-14
forum: Gaming &amp; Leisure
---

### Post by Kittens on 2007-01-14
Every time I try to open a .sh file nothing happens. It asks me if I want to open in the terminal, or just open it. I have tried multiple times with both options and nothing at all happens.

Please someone help me. I love my new OS but things keep making me discouraged.

---

### Post by M_the_C on 2007-01-14
Open a terminal and use cd to go to the directory which the file is in.

Then type:
```
sudo sh *filename*.sh
```

---

### Post by Kittens on 2007-01-14
It tells me that there is no such file or directory when I enter the code.

[http://img212.imageshack.us/img212/2539/actioncubeerrorwj6.png](http://img212.imageshack.us/img212/2539/actioncubeerrorwj6.png)

P.S. My folder of alienarea2007 doesn't seem to need to be installed. The game opens automatically, but how can I move the folder to the location of the other games? It says I don't have the permission to do so.

---

### Post by M_the_C on 2007-01-14
> **Kittens said:**
> It tells me that there is no such file or directory when I enter the code.
It started straight away for me.  I looked up libSDL and found I had got it installed.  Try searching for libsdl with synaptic and check if it is installed, if not then install it and try again.

> **Kittens said:**
> 
P.S. My folder of alienarea2007 doesn't seem to need to be installed. The game opens automatically, but how can I move the folder to the location of the other games? It says I don't have the permission to do so.
Press Alt-F2.  In the box type:
```
gksudo nautilus /*destination*
```
Then just drag the file over.

---

### Post by Kittens on 2007-01-14
> **M_the_C said:**
> It started straight away for me.  I looked up libSDL and found I had got it installed.  Try searching for libsdl with synaptic and check if it is installed, if not then install it and try again.


Press Alt-F2.  In the box type:
```
gksudo nautilus /*destination*
```
Then just drag the file over.

There's lots and lots of packages with libsdl in them.

](*,)

---

### Post by M_the_C on 2007-01-14
> **Kittens said:**
> There's lots and lots of packages with libsdl in them.

](*,)
Sorry, forgot to check.  On your screenshot it says libsdl-image so search for that, I only found two and one of them is a dev, which I don't think you need.  So just install libsdl-image.

---

### Post by Kittens on 2007-01-14
I had to install one more after that, but it did solve the problem. Thanks very much. :)

---

