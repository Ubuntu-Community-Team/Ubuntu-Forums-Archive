---
title: "Gaim: Illegal Instruction"
date: 2006-01-31
forum: Desktop Environments
---

### Post by jdw on 2006-01-31
Hiya ... I don't post much, but that'll probably change now that I'm not working so much.  But I also need help with a problem ....

When I click the Gaim icon, it doesn't start up.  The taskbar entry appears, the hourglass-thing does a few sumersaults, and then nothing happens ... the taskbar entry goes away at this point.

So I decided to try to start Gaim from the console and see if I got any output.  All I get is:  "Illegal instruction".

I tried uninstalling/reinstalling Gaim, deleting all the dot files in my /home, and even installing Gaim 2.0 ... but no matter what (even with the Gaim 2 beta) I still get "Illegal instruction".

I installed Kopete and that works fine, but I prefer Gaim.  And I'd figure I'd get this error out there in the open with the community just in case anyone else is having it (which as far as I could tell, is not the case).

Thanks!

---

### Post by benguin on 2006-01-31
[QUOTE=jdw]Hiya ... I don't post much, but that'll probably change now that I'm not working so much.  But I also need help with a problem ....

When I click the Gaim icon, it doesn't start up.  The taskbar entry appears, the hourglass-thing does a few sumersaults, and then nothing happens ... the taskbar entry goes away at this point.

So I decided to try to start Gaim from the console and see if I got any output.  All I get is:  "Illegal instruction".

I tried uninstalling/reinstalling Gaim, deleting all the dot files in my /home, and even installing Gaim 2.0 ... but no matter what (even with the Gaim 2 beta) I still get "Illegal instruction".

I installed Kopete and that works fine, but I prefer Gaim.  And I'd figure I'd get this error out there in the open with the community just in case anyone else is having it (which as far as I could tell, is not the case).

Thanks![/QUOTE]
 I don't have that exact problem, but if I block someone (yeah I have to at times, I admit), gaim immediately crashes. And it will not sign me in again unless I delete the ~/.gaim/blist.xml file. The error I get when gaim crashes is like this:

```
 *** glibc detected *** double free or corruption (out): 0x0844c0c8 ***
```

That's my gaim situation. Oh and I am (or were) using gaim 1.5.1 CVS, the one that comes with Dapper. I have not experimented with gaim2 in this installation.

---

