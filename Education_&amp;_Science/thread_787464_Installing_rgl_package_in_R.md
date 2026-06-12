---
title: "Installing rgl package in R"
date: 2008-05-08
forum: Education &amp; Science
---

### Post by Tart on 2008-05-08
Hi All,

I'm trying to install rgl package for R and I get the following error

checking for X... no
configure: error: X11 not found but required, configure aborted.
ERROR: configuration failed for package 'rgl'

I notice that this is not only me, was anyone able to solve this problem?

Thank you for your help

---

### Post by Tart on 2008-05-08
I managed to install rgl with 

```
sudo apt-get install r-cran-rgl
```

However when I try to use it, for example

>library(rgl)
>example(plot3d)

R creates plot, but the plot doesn't react in anyway, can't rotate or zoom or anything until I close it with rgl.close().

Any suggestions or recommendations?

---

### Post by Tart on 2008-05-09
After some digging around I found out that apparently there are some libraries are missing.  > 
This is the problem. rgl needs to work with (surprise) GL libraries and include files. With SuSE 9.0 the thing you need is 
> rpm -qf /usr/include/GL/gl.h

How can I translate it to ubuntu? What libraries do I need and how to download them?

---

### Post by kirillt on 2010-04-27
Late, but for the record here is a potential solution:
Try, in bash:
$sudo apt-get install libX11-dev freeglut3 freeglut3-dev

Then in R:
>install.packages(rgl)

This got me through the installation, although call to rgl produced a segfault on my virtual ubuntu 9.1.

---

### Post by LeoBastos on 2011-02-03
Thanks! I've got the same problem trying to install the rgl package. 

I solved installing "xserver-xorg-dev" and then following the kirillt post.

Cheers

---

### Post by iansf on 2012-10-12
In my case R was not built with X support, and I was also missing some openGL libraries.  The info I needed was in the README inside the unzipped tarball for rgl.  But rgl cleaned up after failing the install, and deleted the README, so I never new the README was there until I manually untarr'ed the tarball and looked inside it.  (Error msg from install.packages("rgl") showed where the tarball was.)

I needed to do the following:
1.  Rebuild R with X support.  Add --with-X to the configure line when building  See app.B.1 "Configuration Options" of R Installation & Admin manual
./configure --with-tcltk --with-system-zlib --with-system-bzlib --enable-R-shlib --with-x
                                (note:  might need --x-includes=DIR --x-libraries=DIR  .  Seemed to work without these for me, presumably because they are in the default location)
                        make
                        make check
                        make install
2.  Install missing openGL libraries (I'm on RHEL...use apt get on other systems):
yum install mesa-libGL-devel mesa-libGLU-devel libpng-devel

3.  Install rgl
                        > install.packages("rgl")

HTH

---

### Post by overdrank on 2012-10-12
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

