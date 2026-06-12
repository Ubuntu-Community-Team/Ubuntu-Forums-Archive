---
title: "KDE 3.5.0 using ALOT of memory"
date: 2006-01-05
forum: General Help
---

### Post by daedalusman on 2006-01-05
Ok I know KDE will use a good amount of memory and I have plenty to accomedate. Thing is, Ksysgaurd is telling me that almost all of my memory is being used. I have 1.5GB of ram and Ksysgaurd tells me that I have just 40megs or so free! Whats up with this seemingly ridiculously high usage of memory, is there some important peace of information that I'm messing or is this actually how much ram is being used by my system. I haven't noticed any really performence hits that would most likely plague a system in this case so I think I'm missing something here. Thanks for the help.

---

### Post by GeneralZod on 2006-01-05
Most modern Operating Systems make sure the RAM is as full as possible with cached files etc as your RAM is far faster than your harddrive.

Try

```

free

```

for a more "accurate" reading of your memory usage.

---

### Post by Pawel Stolowski on 2006-01-05
As GeneralZod said, Linux is making a good use of your RAM for disk cache. If any application needs more RAM, it will be freed immediately, so nothing to be worried about... You may run System->KInfoCenter (choose Memory tab) to see how much memory is used for caching...

---

### Post by daedalusman on 2006-01-05
Ahh, alright, I thought something might be going on just wasn't sure and I have never seen this before, thanks. I like kinfocenter, much better than Ksysgaurd in regards to memory usage as a whole.

---

