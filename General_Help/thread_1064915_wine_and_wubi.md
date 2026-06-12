---
title: "wine and wubi"
date: 2009-02-09
forum: General Help
---

### Post by mistafeesh on 2009-02-09
My heading sounds like some sort of bizarre meal...

I've installed ubuntu with wubi on my HP laptop, and I must say it went *very* smoothly. It's all working fine, but I can't see my 'C:' drive anywhere, and when I installed wine it showed a C: drive that just contained notepad, which is, I guess, something it does if it can't find the real one?

Any ideas? I'd really like to get going with Linu as my main OS, but there are a couple of apps I really want to be able to use that I know work OK in wine. I also want to be able to see my windows files.

thanks,

Dan

---

### Post by smo0th on 2009-02-09
go to Places>Computer and you should see your 'C' drive there. It will be labeled something else so don't expect to see a 'C:' drive there.

---

### Post by wstout on 2009-02-09
You can find your windows files by clicking Places -> Computer -> File System then find the folder named Host. The C: drive you see with wine is not the same as the one on your windows partition. Not exactly for sure of the technical term but it is a simulated C: drive so to speak so when you install windows programs they work. I'm not a WINE expert so I'm sure thats not exactly correct.

---

### Post by mistafeesh on 2009-02-09
Hi thanks very much guys. The hosts folder was what I was looking for!

Dan

---

