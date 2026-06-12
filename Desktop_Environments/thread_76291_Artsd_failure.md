---
title: "Artsd failure"
date: 2005-10-14
forum: Desktop Environments
---

### Post by Jvaldezjr on 2005-10-14
I don't know if this should be in the Kubuntu forums or the Ubuntu forums, but I'm running ubuntu, with KDE installed, and when KDE loads, I get a message saying that the soundserver has failed.  Anyone else had these problems with Breezy?  I never had that problem with Hoary.

---

### Post by kaiska on 2005-10-18
Yep !
I have the same problem here under kde 3.5 beta 2. I did not find any workaround. Somebody could help us ?

---

### Post by kaiska on 2005-10-18
He seems having the same problem :
[http://ubuntuforums.org/showthread.php?t=72812&highlight=soundserver]("http://ubuntuforums.org/showthread.php?t=72812&highlight=soundserver")
Here is the log given by kde crash manager :```
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread -1219451200 (LWP 9197)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[KCrash handler]
#14 0xb779033e in __gnu_cxx::__pool<true>::_M_reclaim_block ()
   from /usr/lib/libstdc++.so.6
#15 0x080606b3 in ?? ()
#16 0x08074cc0 in Arts::ByteSoundProducerV2_base::_IID ()
#17 0x08218ec8 in ?? ()
#18 0x00000008 in ?? ()
#19 0xb7720900 in __malloc_initialize_hook ()
   from /lib/tls/i686/cmov/libc.so.6
#20 0x08164244 in ?? ()
#21 0x00000000 in ?? ()
#22 0x08164204 in ?? ()
#23 0x081641ec in ?? ()
#24 0x081641e4 in ?? ()
#25 0x081641dc in ?? ()
#26 0x081641d4 in ?? ()
#27 0x081bef28 in ?? ()
#28 0x081bede8 in ?? ()
#29 0x080b97dc in ?? ()
#30 0xbfb3a860 in ?? ()
#31 0x08119bc4 in ?? ()
#32 0x08119c3c in ?? ()
#33 0x08219b94 in ?? ()
#34 0x08219b94 in ?? ()
#35 0x081fa070 in ?? ()
#36 0x0821df04 in ?? ()
#37 0x08071d38 in ?? ()
#38 0x00000133 in ?? ()
#39 0x081641d0 in ?? ()
#40 0x0806af04 in typeinfo name for Arts::TimeNotify ()
#41 0x081641d0 in ?? ()
#42 0xbfb3a878 in ?? ()
#43 0x08068018 in ?? ()
#44 0x081641d0 in ?? ()
#45 0x0806af08 in typeinfo name for Arts::TimeNotify ()
#46 0x08164274 in ?? ()
#47 0x08164274 in ?? ()
#48 0x0806b03c in typeinfo name for Arts::TimeNotify ()
#49 0x08164220 in ?? ()
#50 0xbfb3a8b8 in ?? ()
#51 0x08060ff6 in ?? ()
#52 0x081641d0 in ?? ()
#53 0x0806af04 in typeinfo name for Arts::TimeNotify ()
#54 0x000000a8 in ?? ()
#55 0xb782ccd0 in ?? () from /usr/lib/libstdc++.so.6
#56 0x000000a8 in ?? ()
#57 0x0810b360 in ?? ()
#58 0xbfb3a8b8 in ?? ()
#59 0xb78084c5 in operator new () from /usr/lib/libstdc++.so.6
```

---

