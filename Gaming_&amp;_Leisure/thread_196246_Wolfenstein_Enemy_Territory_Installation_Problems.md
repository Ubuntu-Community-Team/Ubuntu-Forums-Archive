---
title: "Wolfenstein: Enemy Territory Installation Problems"
date: 2006-06-13
forum: Gaming &amp; Leisure
---

### Post by t.z0n3 on 2006-06-13
I'm a compete newbie to Linux in general, so I'm sorry if this is a simple fix, but I can't figure it out. I've downloaded the packages (.run type) for the game and for the 2.6.0 patch (which is in some freaky format so I can't even understand it... there's two files in the Linux folder in there, but neither of them have an extension).

So I tried to do this: I navigated to the correct directory, and typed:

sudo apt-get install et-linux-2.55.x86.run

It says :

Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package et-linux-2.55.x86.run

Which doesn't make since, because the ls command (used before and afterword) clearly shows the files there. So does 'find'.

So I'm bamboozled here. I don't understand what I did wrong... can somebody help me?

...Please? I'll make you some brownies! (non laxative of course... ^^)

---

### Post by stangbang on 2006-06-14
from the terminal browse to the folder with et-linux-2.55.x86.run

at the terminal type sudo ./et-linux-2.55.x86.run

the ./ tells it to execute this file. It will run you through the installation process.

I would also suggest installing the package libgtk1.2 before you install it, although you dont have to.

---

### Post by dresnu on 2006-06-14
You also probably need to make it executable first so while being in the right directory and before running what stangbang suggested, do this```
chmod a+x et-linux-2.55.x86.run
```

---

### Post by t.z0n3 on 2006-06-14
I just wanted to thank you guys so much. Actually, both of your posts were needed. I got the LibGTK thing, and then I made it executable, and it worked. 

*gives you brownies* :D

---

