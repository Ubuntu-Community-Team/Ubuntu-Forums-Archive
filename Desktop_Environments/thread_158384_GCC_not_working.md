---
title: "GCC not working"
date: 2006-04-11
forum: Desktop Environments
---

### Post by dabster on 2006-04-11
i used synaptic to install gcc and g++ on ubuntu BB i386 ...Which installed gcc 4.0 on my computer,
But it is not working....When I try to compile the c program it says can't find stdio.h file or directory.

Also when trying install the c++ program it gives full pages of garbage values....

This is happening on my frnds comp also....
Is this a problem in ubuntu BB i386  because I know tht it worked in AMD64 version....

...

---

### Post by bonzodog on 2006-04-11
Did you get the build-essential meta package?
This simply installs all the packages needed for building software.

Just do this in a terminal:
```
$sudo apt-get install build-essential
```

That should sort out any problems you have with it.

---

### Post by dabster on 2006-04-13
Yeah, perfect....Thanks

---

