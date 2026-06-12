---
title: "Upgraded to Hardy, octave 3.0.0 does not start"
date: 2008-06-22
forum: Education &amp; Science
---

### Post by ayesha kalra on 2008-06-22
Hi all

I just upgraded to Hardy and found that octave is not starting now. This is the error message I am getting

```

octave: error while loading shared libraries: libumfpack.so.1: cannot open shared object file: No such file or directory

```

Obviously, I do not have libumfpack.so.1, or do not have it at the right location, or there is a name change involved. Any suggestions here will be helpful.

Thanks
Ayesha

---

### Post by ahmatti on 2008-06-23
How did you install octave? I use the Octave3.0 installed from hardy repos and it works nicely. Octave3.0 didn't exist in feisty so chances are that you have the wrong package installed?

---

### Post by ayesha kalra on 2008-06-23
I also installed Octave from Hardy repos via Syanptic Package Manager. Still the problem exists :(

Ayesha

---

### Post by thisismalhotra on 2008-06-24
> **ayesha kalra said:**
> I also installed Octave from Hardy repos via Syanptic Package Manager. Still the problem exists :(

Ayesha

I have seen this problem before when I made octave 3.0 deb's on Gutsy.
Anyways try running following commands
```

sudo apt-get update
sudo apt-get build-dep octave
```

Post again if that does not work.

---

### Post by ayesha kalra on 2008-06-24
That did not work, thank though.

I think this is the problem. 

libumfpack.so.1 has been replaced by libumfpack.so.3.1.0 (I see libumfpack.so.3.1.0 in my /usr/lib ). But how do I tell Octave to look for libumfpack.so.3.1.0 instead of libumfpack.so.1


Ayesha

---

