---
title: "ngspice history"
date: 2008-02-11
forum: Education &amp; Science
---

### Post by jonlemur on 2008-02-11
Hello all,

I recently installed ngspice in Gutsy Gibbon, and I was wondering if the up and down arrows should cycle through the history of previously entered commands.  It certainly is not doing that for me.  Instead, an up arrow is converted to a "^[" if it's the first thing pressed or a "A[" if it comes after something else, a down arrow is converted to a "B[", the right arrow to a "C[" and the left arrow to a "D[".  Finally, the delete key is converted to a "[3~".

So my question is pretty much just is this how it is on other people's systems, and if not (I sure hope not), can anyone help me fix it?  It also prevents moving the cursor to a previous point in a line to fix an error.

I know I can use the history command (aliased to 'h') to recall previously entered commands, but being able to use all of the arrow keys and the delete key would be very beneficial.

Thanks for any help you can provide.

---

### Post by jonlemur on 2008-02-14
Bump

---

### Post by jonlemur on 2008-07-02
I fixed the issue a while ago.  But if anyone else comes across the same problem, this is how I fixed it.  I uninstalled the version of ngspice that I had (which was installed from the usual ./configure, make, make install) and downloaded the deb for it.  If I remember right, I also had to download the deb for xspice and run something like 
```
dpkg -i ngspice.deb xspice.deb
```

They had to be done together because they both depended on each other.

---

