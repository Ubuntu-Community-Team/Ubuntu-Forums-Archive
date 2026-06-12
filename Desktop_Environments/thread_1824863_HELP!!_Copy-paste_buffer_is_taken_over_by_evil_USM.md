---
title: "HELP!! Copy-paste buffer is taken over by evil USMLEWORLD"
date: 2011-08-14
forum: Desktop Environments
---

### Post by Shompol on 2011-08-14
Every time I try to copy-paste, this is the line that always sits in my paste buffer:

"Copyright(c) 2006 USMLE WORLD, Please do not save, print, cut, copy or paste anything while USMLE WORLD is running. Thanks!!"

It seems they intentionally crippled copy-paste on my computer just so I cannot copy their precious copyrighted material. Using computer with crippled copy-paste is a nightmare. I could not care less about their intellectual crap, but they should not take my computer hostage of their idiotic fears.

Their application is written in Java (which is the reason why I could run their evil crap on Ubuntu). I cannot boycott them because my spouse needs to pass the test, and this is the prep material.

Please help me figure out how to protect copy-paste buffer from intruding crippleware written in Java.

Thanx
- Shompol

---

### Post by Shompol on 2011-08-14
Found one workaround: there is a separate, independent way to copy-paste in Linux, that did not get crippled and works pretty well. It's called Klipper (Glipper):

                   <a href=http://embraceubuntu.com/2006/12/12/cut-copy-paste-clipboard-management/">
 ...did you know that there is another way to copy and paste in X? You can  highlight some text, and then go to another window or application, click  where you want to paste the highlighted text, and then middle-click. If  your mouse has no middle button, then you can click both the left and  right buttons together to create the middle-click. Thats it – your  highlighted text is now pasted in the other application.</a>

This is still a big problem because:
1) Windows users are still affected. Internet is full of complaints about this uncalled for "feature".
2) USMLEWORLD illegally crippled my desktop, including applications they have nothing to do with. 
2) This is a security issue. A single app was able to to take over my desktop environment. Are they also allowed to read my clipboard and transmit private data to their server? This is a gaping loophole that needs to be fixed.

---

### Post by N1GHTS on 2011-08-14
That program seems to be performing an X selection persistently in its main loop. Ultimately, the only thing short of reverse engineering the program to stop the selection would be to isolate that function at an application level using some kind of hook. I don't know a way to do that, but I would love to know.

---

### Post by milap88 on 2012-04-26
This is pretty late, but in case anyone else runs upon this, they may find it helpful.
#kill -STOP [pid] (or [process-name]
At this point, you can just do screen shots, you won't be able to copy and paste text as the application is suspended.
#kill - CONT [pid]
to start the application back up.

Windows users can use the application Process Explorer to do the same thing.

---

