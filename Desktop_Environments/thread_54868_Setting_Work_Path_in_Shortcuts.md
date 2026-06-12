---
title: "Setting Work Path in Shortcuts"
date: 2005-08-06
forum: Desktop Environments
---

### Post by J1m on 2005-08-06
Hello all,

I am trying to create a menu item using Smeg to run a small windows game using wine.  I need to set the work path in the shortcut and can't see any way to do it.

If I am in a console in the correct path and run the game,  it works fine, if I try running it from a different path, or from a shortcut in the menu, it says there are files missing (can't find Elma.res, etc) and wont work.

Can anyone tell me how to create a link or shortcut where I can set the "work path" to a specific directory.  (Like I was able to do in KDE using Mepis)

Thanks in advance.

Jim

---

### Post by kosmic on 2005-08-06
how have to do something like this :


wine "C:\programfiles\aplication.exe" so you can run it with a shortcut

---

### Post by J1m on 2005-08-06
Hi kosmic.

Yes.  My shortcut is just as you have posted.  The application starts when I click on the shortcut but quits with errors.

Only when I'm in a terminal and in the actual directory to run the file does the application work.

So I need to find a way to set the path before running the app.  Just ticking "run in terminal" box does not help either :(

---

### Post by cwaldbieser on 2005-08-06
You could just make a simple script like:

```
#! /bin/bash

cd /working/directory
wine "C:\programfiles\aplication.exe"
```

Save it as "mywinprog", give it executable permissions with "chmod u+x mywinprog", and then make the shortcut to that instead?

---

### Post by J1m on 2005-08-07
cwaldbieser

That was exactly what I was looking for thank you very much.  But it still doesn't work :)

I don't understand it now, I thought that would have solved the problem for sure  ](*,)

---

### Post by cwaldbieser on 2005-08-07
Well, maybe you neet to include the full path to the "wine" executable as well:

```
#! /bin/bash

cd /working/directory
/usr/bin/wine "C:\programfiles\aplication.exe"
```

Could be that maybe wine is also looking for files relative to the executable?  I dun't know about that-- I haven't actually ever run wine.  But I set up similar wrapper scripts for lots of my games that way.

---

