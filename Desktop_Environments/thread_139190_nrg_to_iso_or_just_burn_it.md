---
title: "nrg to iso or just burn it?"
date: 2006-03-03
forum: Desktop Environments
---

### Post by syklitengutt on 2006-03-03
When I migrated from windows I made some copies from my dvd movies,
and one of them (dont ask me why) was saved as a .nrg file.
How can I burn this with k3b or gnomebaker?
The file is 4.4 gig big.

---

### Post by z_diver on 2006-03-03
That's a nero disk image so I would imagine Nero for Linux would be able to burn it onto CD.

---

### Post by taurus on 2006-03-03
k3b can handle nrg file just fine...  No need to convert it to iso first so if you don't have it, install k3b and check it out.

---

### Post by akiro.yamamoto on 2006-03-03
Good tip taurus, I didn't know k3b could handle .nrg files.
Linux RUULLLES!!!!!!
;)
Sorry didn't mean to get so emotional :rolleyes:

---

### Post by taurus on 2006-03-03
[QUOTE=akiro.yamamoto]Good tip taurus, I didn't know k3b could handle .nrg files.
Linux RUULLLES!!!!!!
;)
Sorry didn't mean to get so emotional :rolleyes:[/QUOTE]
You didn't know that!  Now you do.  And yes, Linux always rules.  

p.s.  Looks like somebody needs a hug!!!  :mrgreen:

---

### Post by akiro.yamamoto on 2006-03-03
Hah!!  ;)

---

### Post by syklitengutt on 2006-03-04
burned it with k3b after a md5sum check.
But the format is unknown .
dmesg | tail said unknown disk format,
and my dvdplayer in the livingroom didnt read it. 
Unknown there also.

So how do I burn a nrg file corectly with k3b?

And if anyone know, how do I convert the nrg file?

---

### Post by taurus on 2006-03-04
Was that an CD image or a DVD image and how did you burn it?

---

### Post by syklitengutt on 2006-03-04
it was a dvd turned into a nrg file.
I solved this myself.
In synaptic I installed nrg2iso...
Its a terminal prog and works like a charm...

anyway, tnx for your help.

---

