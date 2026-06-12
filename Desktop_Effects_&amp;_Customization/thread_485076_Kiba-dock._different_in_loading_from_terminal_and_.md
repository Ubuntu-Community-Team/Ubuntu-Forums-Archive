---
title: "Kiba-dock. different in loading from terminal and session?"
date: 2007-06-26
forum: Desktop Effects &amp; Customization
---

### Post by TXBDan on 2007-06-26
Howdy,

I'm running feisty, the latest greatest compiz fusion, and kiba-dock. 

Everything works great except that kiba-dock only works properly when i load it from a terminal 'kiba-dock &'

I added it to the session manager so that it would automatically load, but for some reason when loaded this way, it only displays a small kiba dock (only trash and memory thing, none of the other stuff) and things do not minimize to it. they just disappear.  

Any ideas?

Thanks a lot

---

### Post by Calash on 2007-06-26
I have seen the same problem.  Have not had a chance to troubleshoot it yet, I just shut it off in the Session Manager and started it after everything booted.

---

### Post by walkerk on 2007-06-26
try this in session manager:
```
sleep 5 && kiba-dock &
```

---

