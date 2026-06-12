---
title: "I think i've destroyed evolution.... but i want it back."
date: 2009-03-10
forum: General Help
---

### Post by Kain000 on 2009-03-10
Myself being in a hurry to uninstall google earth and being let down by it's ./uninstall script, as it left lots of google earth stuff arround, I searched for google things and foolishly started deleting.    

one of witch was  libgdata-google1.2.so.1
 witch it turns out is required to run evolution.....

But I cannot find its replacement anywhere.
in synaptic it  brings up  libgdata-google1.2 without the .so.1 and it shows it as installed.

I tried complete removal of evolution and then a re-install but when I run the command evolution I get the error:
```
sean@sean-desktop:~$ evolution
evolution: error while loading shared libraries: libgdata-google-1.2.so.1: cannot open shared object file: No such file or directory

```

duh because I was an idiot and deleted it.... ugh

and now I dont know what I can do to get the lib back or just wipe out and reinstall evolution.   

cant find anything on google or this forum for libgdata-google-1.2.so.1
(most likely because noone has been this stupid...):(

---

### Post by Yellow Pasque on 2009-03-10
Open Synaptic and do a search for gdata.
Reinstall this package: libgdata-google-1.2-1

---

### Post by Kain000 on 2009-03-10
> **Temüjin said:**
> Open Synaptic and do a search for gdata.
Reinstall this package: libgdata-google-1.2-1

worked like a charm!  thanks alot

---

