---
title: "Moving Processes between Virtual Terminals"
date: 2008-12-17
forum: General Help
---

### Post by mbsullivan on 2008-12-17
I recently ran into a question that I didn't know the answer to:

Is there any way to move a running process between virtual terminals (i.e. transfer the ownership of it)?

I was in the middle of a long apt-get installation on a friend's computer, and wanted to restart X after tinkering with it. Is there any way anybody knows of to transfer the running (CLI) program to another virtual terminal, such that I could restart the X server without interrupting the upgrade?

I know this functionality could be emulated by attaching the process to a running "screen" manager, but I was not forward-thinking enough to do so. 

Thanks!
Michael

---

### Post by Dr Small on 2008-12-17
Why not open another virtual terminal and then restart X?

---

### Post by mbsullivan on 2008-12-17
Hi Dr. Small,

Thanks for the reply! To answer your question, this would certainly work. The point here, however, was that I didn't know that I was going to run into this issue. Therefore I had started the process minutes before I decided I wanted to restart X.

If I'd thought about it before running the program, I could either start it in another virtual terminal or attach it to a running terminal multiplexer. For better or worse, I did neither of these things. Having made this poor decision, I would like to know if it is possible to move a running process, or if I am out of luck.

Mike

---

