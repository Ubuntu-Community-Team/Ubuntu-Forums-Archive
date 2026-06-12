---
title: "Problem with America's army"
date: 2005-10-19
forum: Gaming &amp; Leisure
---

### Post by CastleKingSide on 2005-10-19
Hi, i just installed Amercia's Army version 2.3.0 and when I try to run it I got this back:
```
tarik@satellite:~$ armyops
./armyops-bin: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory

```
That's weird, I tried apt-get install libstdc++.so.5 but there is no such package, so I need help!!!

---

### Post by CastleKingSide on 2005-10-19
Ok, solved, I just did apt-get install libstdc++5
and it worked... I'll leave the thread if someone face the same problem.

---

### Post by crane on 2005-11-04
Thanks, had teh same problem and this fixed it right up.

---

### Post by alanwalterthomas on 2009-11-05
I'm playing after all these years...

It wouldn't run in Karmic 9.10.
It installed normally but then I had to download & install 

gcc-3.3-base_3.3.6-15ubuntu4_i386.deb
 & then 
libstdc++5_3.3.6-15ubuntu4_i386.deb

America's Army started up like a charm.

To be clear, I couldn't get those from synaptic - they aren't in the repositories any longer.
Get them from [http://packages.ubuntu.com/hardy/libstdc++5](http://packages.ubuntu.com/hardy/libstdc++5)

---

