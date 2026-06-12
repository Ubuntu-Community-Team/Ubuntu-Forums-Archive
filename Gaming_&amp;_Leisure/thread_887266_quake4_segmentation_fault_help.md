---
title: "quake4 segmentation fault help"
date: 2008-08-12
forum: Gaming &amp; Leisure
---

### Post by tjwoosta on 2008-08-12
so i am trying to install quake4

im running hardy 64bit

all seems to have gone well up untill now

when i try to run quake4 i get the same exact error that is mentioned in theis thread
[http://ubuntuforums.org/showthread.php?t=155756]("http://ubuntuforums.org/showthread.php?t=155756")

so according to this thread, what i will need to do is temporarily disable xgl (whatever that is) and compiz

the problem is that this thread, to me, seems a little vague

i understand that i can use the command metacity --replace to temporarily disable compiz but how can i temporarily disable xgl?

and more importantly what is xgl?

---

### Post by Crafty Kisses on 2008-08-12
Well for starters "XGL" isn't enabled or installed by default and if your using "Desktop effects" whitch is actualy called "Compiz" that might be what you're talking about. So if you don't know what XGL is, it is actually a rendering platform that you can use when you are using Compiz or Beryl (Beryl being another Window Manager).
```
ps -A
```

Look for XGL on that list.

You may want to look at this thread too < [http://ubuntuforums.org/showthread.php?t=176636](http://ubuntuforums.org/showthread.php?t=176636)

---

### Post by tjwoosta on 2008-08-12
alright so im not using xgl

and i have already disabled compiz

why am i getting the error message and how do i fix it?

---

### Post by Crafty Kisses on 2008-08-12
> **tjwoosta said:**
> alright so im not using xgl

and i have already disabled compiz

why am i getting the error message and how do i fix it?

Not sure, I'm not sure if AWM or something could cause this issue, I can't see why it would.

I'll look into this for you.

---

