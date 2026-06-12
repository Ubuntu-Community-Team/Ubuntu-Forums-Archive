---
title: "Determining which window is being moved"
date: 2010-05-10
forum: Desktop Environments
---

### Post by AshRice on 2010-05-10
I have a script I only want to run when a window is being dragged around. Is there an environmental variable or something that will tell me whether one is moving and which one it is? I'm using Ubuntu Lucid if it matters.

Cheers

---

### Post by AshRice on 2010-05-10
Maybe it would help if I gave more details:

I'm trying to modify a script I found to enable Windows 7 style AERO docking. It currently will resize the active window correctly, but does so whether I drag the window to the side or just move the mouse over there. It would be perfect if I could eliminate that flaw.

If there is a better script out by now then a link would be great, but I kind of want to know how to do this for future reference anyway.

---

### Post by zlatkart on 2010-05-10
Wrong language for your purpose.

---

### Post by AshRice on 2010-05-10
Yea, I'm sure something else would be better but I only know FORTRAN (not going to be much use). I could learn something else, and will when I have time, but for right now this is what I have to work with.

Should I take from this that there is nothing that does what I need it to?

---

### Post by zlatkart on 2010-05-10
with wmctrl you could read the position of the windows on your desktop. store them all in an array. Read again and compare. I don't know any short way. I tried nearly the same with bash and started learning c for these things

---

### Post by AshRice on 2010-05-10
Yea that's basically where I am. Thanks anyway!

---

### Post by zlatkart on 2010-05-10
as you know FORTRAN you seem to be older than the average here. You should have a look at C some time.

---

### Post by AshRice on 2010-05-10
Haha! I'm actually a grad student (early 20s). I have to know FORTRAN because of the research I do.

I do appreciate the advice though.

---

### Post by zlatkart on 2010-05-10
Oh sorry I thought it could only be used in some historical research (although I don't know the average here)

---

### Post by gemmakaru on 2010-05-10
I wrote some .dlls for windows 3.1 in fortran 77, that was a long time ago, I think fortran was old then, is it really still being used?  I can't remember a word of it now though.

---

