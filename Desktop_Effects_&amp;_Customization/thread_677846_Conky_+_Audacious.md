---
title: "Conky + Audacious"
date: 2008-01-25
forum: Desktop Effects &amp; Customization
---

### Post by theriddler on 2008-01-25
Hey @ all,

i got a little problem...

i installed conky on my laptop (ubuntu 7.10 Gutsy Gibbon) and  i want a Audacious Info in ConkyBar but it won´t work...

here is a screenshot...[CLICK](http://forum.ubuntuusers.de/download/8871/) u can see it last on the right side...

my audacious version is 1.3.2 and conky version is 1.4.9

please help me....

so long
riddler

---

### Post by elcasey on 2008-01-27
I just went through this process myself. There are several issues here. To begin with, Conky 1.4.7, which is the version available in the Ubuntu repositories, does not support Audacious variables. You installed the newest version, 1.4.9, which does not support Audacious 1.3.x! Here's the other problem...it's rather difficult to compile Audacious 1.4.x on Gutsy. If you look at the output from ./configure on Conky 1.4.9 it says at the bottom "audacious       no." This is easily dealt with by doing "./configure --enable-audacious," but again, it wants Audacious 1.4, so we're stuck on this one.

I solved it by removing Conky 1.4.9 and compiling and reinstalling Conky 1.4.8. This works fine with Audacious 1.3, although you can't scroll titles and it general looks pretty awful with every song cut off (unless you have a 400px wide conky). I'm disappointed overall with the Audacious variables, but Conky is still amazing.

---

### Post by notwen on 2008-03-19
There looks to be a [thread]("http://ubuntuforums.org/showthread.php?t=585096") offering a .deb file that will install conky 1.4.8 w/ audacious enabled by default if you are not cmfortable enough w/ compiling source just yet.  I have not tried it, but should accomplish what you want w/ 2 clicks. =]  Post back and let us know if it works.

---

### Post by sn3rd on 2008-06-10
If anyone's still looking for an easy solution to this, try:

```
audtool current-song
```

at the command-line. If the output is to your liking, then you can add it to your .conkyrc as 

```
${exec audtool current-song}
```

and more functionality can be found by having a look through

```
audtool help
```

---

