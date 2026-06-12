---
title: "open office 3.1 crahses at startup"
date: 2009-05-07
forum: General Help
---

### Post by Meow27 on 2009-05-07
i downloaded OOo3.1, installed it, and lo and behold. it crashes every single time i try to run it...

when it try to close it, it keeps making a loop saying "oh this program crahsed, let me restart that for you" crashes immediately after that and restarts the loop

any ideas?

---

### Post by prafjessor on 2009-05-12
> **Meow27 said:**
> i downloaded OOo3.1, installed it, and lo and behold. it crashes every single time i try to run it...

when it try to close it, it keeps making a loop saying "oh this program crahsed, let me restart that for you" crashes immediately after that and restarts the loop

any ideas?

I had the same problem, but then i removed the .open office-file in Home and restarted, and then it worked just fine.

---

### Post by Meow27 on 2009-05-13
> **prafjessor said:**
> I had the same problem, but then i removed the .open office-file in Home and restarted, and then it worked just fine.

did the job for me..... thanks!! 
:D


:popcorn:

---

### Post by apexofservice on 2009-06-05
worked for me too!

the only ambiguity is that for me the thing to remove was a directory.  

i had to remove:

.ooo/
.openoffice.org/
.openoffice.org2/

noobs can do it with:

$rm -r DIRECTORYTOBEREMOVED

---

