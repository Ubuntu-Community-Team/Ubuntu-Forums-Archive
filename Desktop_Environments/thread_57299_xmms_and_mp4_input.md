---
title: "xmms and mp4 input"
date: 2005-08-16
forum: Desktop Environments
---

### Post by teme82 on 2005-08-16
Hi!
I have this weir problem, I have libmp4.so in /usr/lib/xmms/Input dir and still xmms can't find it to eneble mp4 audio support :(
So is there a manual way to tell xmms that i have mp4 plugin installed?

---

### Post by RaymondQE on 2005-08-16
If I recalled correctly, you also need libmp4v2-0 installed from the repository.  Try installing that and see if the problem goes aways.

---

### Post by teme82 on 2005-08-16
[QUOTE=RaymondQE]If I recalled correctly, you also need libmp4v2-0 installed from the repository.  Try installing that and see if the problem goes aways.[/QUOTE]
Synaptec can't find it so .... it didn't help :(

---

### Post by RaymondQE on 2005-08-17
My mistake, it's only in breezy right now.

This thread may help
[http://www.ubuntuforums.org/showthread.php?t=52397](http://www.ubuntuforums.org/showthread.php?t=52397)

---

### Post by teme82 on 2005-08-17
[QUOTE=RaymondQE]My mistake, it's only in breezy right now.

This thread may help
[http://www.ubuntuforums.org/showthread.php?t=52397](http://www.ubuntuforums.org/showthread.php?t=52397)[/QUOTE]
Now xmms gives me this 
"libmikmod.so.2: cannot open shared object file: No such file or directory
/usr/lib/xmms/Input/libmp4.so: undefined symbol: NeAACDecDecode
Segmentation fault"

---

### Post by RaymondQE on 2005-08-17
The first error indicates that you need to apt-get the package libmikmod2.

Not sure about the second problem.  Check if you have libfaad2 installed.

---

### Post by teme82 on 2005-08-17
[QUOTE=RaymondQE]The first error indicates that you need to apt-get the package libmikmod2.

Not sure about the second problem.  Check if you have libfaad2 installed.[/QUOTE]
Yeah, I did install libmikmod and libfaad, byt stil got that segment failure :( all the other multimedia programs gave me the same segmentation error :P

---

### Post by RaymondQE on 2005-08-18
Hmm, maybe try installing a new version of libmp4.so --> [http://fondriest.frederic.free.fr/realisations/](http://fondriest.frederic.free.fr/realisations/)

and installing faad2 from cvs --> [http://sourceforge.net/cvs/?group_id=704](http://sourceforge.net/cvs/?group_id=704)

---

### Post by teme82 on 2005-08-18
[QUOTE=RaymondQE]Hmm, maybe try installing a new version of libmp4.so --> [http://fondriest.frederic.free.fr/realisations/](http://fondriest.frederic.free.fr/realisations/)

and installing faad2 from cvs --> [http://sourceforge.net/cvs/?group_id=704](http://sourceforge.net/cvs/?group_id=704)[/QUOTE]
Hmm... that didn't help =( well have to wait xmms 2 then ...

---

