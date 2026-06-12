---
title: "Problems installing StepMania"
date: 2005-09-20
forum: Gaming &amp; Leisure
---

### Post by Nathan1 on 2005-09-20
Hi I'm having problems installing Stepmania on linux.  I've tried the binary and source code.  When I unpack it and click on the stepmania executable nothing happens, and for some reason I get an error when I try to compile the source.  (it says that It doesn't have an install-sh, but it does.)  Could someone please tell me an easy way to install Stepmania because I've spent 4+ hrs with no luck.  ~Thanks

---

### Post by gerbman on 2005-09-21
[QUOTE=Nathan1]Hi I'm having problems installing Stepmania on linux.  I've tried the binary and source code.  When I unpack it and click on the stepmania executable nothing happens, and for some reason I get an error when I try to compile the source.  (it says that It doesn't have an install-sh, but it does.)  Could someone please tell me an easy way to install Stepmania because I've spent 4+ hrs with no luck.  ~Thanks[/QUOTE]

I'm not sure if there is an *easy* way to do it, but it is definitely possible using the binary from [here](http://prdownloads.sourceforge.net/stepmania/StepMania-3.9-rc3-linux.tar.gz).    After you download the file unpack it with ```
tar -xvzf yourfile.tar.gz
```  and move it to where you like.  The major problem I and a few others had is that it looks for a number of library files that you might or might not have.  After you unpack everything go into the folder and run it with ```
./stepmania
```I'm guessing you'll get some errors about missing library files.  Read [this](http://www.ubuntuforums.org/showthread.php?t=56336) and [this](http://www.ubuntuforums.org/showthread.php?t=60435) for tips on the library problems.  Post any errors you get stuck on.

---

