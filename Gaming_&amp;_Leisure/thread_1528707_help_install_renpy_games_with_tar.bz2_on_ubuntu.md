---
title: "help install renpy games with tar.bz2 on ubuntu"
date: 2010-07-11
forum: Gaming &amp; Leisure
---

### Post by flagstar on 2010-07-11
Hye... I have a problem to install renpy-based games (visual novel) that was in linux-x86.tar.bz2 file archive.

I tried to install by step-by-step instruction on the web but I couldn't get the terminal to run ./configure with error (no such file or directory)

I have already install the based-essential earlier but it wouldn't work out somehow...
Plz help me... Thanks n advance...

---

### Post by DrMelon on 2010-07-11
The "no such file or directory" error means that you're not in the right place in the terminal. Are you sure you've changed to the directory where you extracted the files from the .tar.bz2 archive?

---

### Post by flagstar on 2010-07-14
I'm not sure but the thing I do is make a new folder in home directory, placed the game inside the new folder, open the terminal and extracted the tar.bz2 to the same folder and cd directory to the extracted folder. When I try to ./configure, there was no file or directory on the extracted folder. I'm not sure what is the problem here...

---

### Post by Perfect Storm on 2010-07-14
Let us say you have downloaded the package to your Desktop.

```
cd ~/Desktop
tar jxf renpy-6.10.2-sdk.tar.bz2
cd renpy*
./renpy.sh
```

---

### Post by flagstar on 2010-07-14
still not working... it still show the same error like the last time...
I'm curious... do I even need to install the game in order for it to work or it can run by itself? I can't even find the necessary file that needed to install it...

That game has two version (Windows/linux). I try to install it on Windows and it worked flawlessly... Does it not support Ubuntu for Netbook?

---

### Post by Perfect Storm on 2010-07-14
It do, it's must be you that doing something wrong.
Better to post every out/in-put from the terminal.

---

### Post by renpytom on 2010-07-15
In general, .tar.bz2 Ren'Py games do not require an install to run. Instead, all you need to do to run them is to run the *gamename*.sh file that's included in the package.

You may also need the 32-bit libraries, if you're on 64-bit.

If you let me know which games you're interested in, I can give more specific instructions.

---

### Post by tastefuldeath on 2012-09-15
I used to be able to just run the .sh file and play. But after I reformatted my netbook, the terminal seems to appear and then close and then no game. Anyone who can help?

---

### Post by Perfect Storm on 2012-09-15
This is an old thread, please start a new one.

Thanks.


Thread closed.

---

