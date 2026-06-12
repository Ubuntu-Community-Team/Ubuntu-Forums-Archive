---
title: "Flightgear not working"
date: 2006-01-14
forum: Gaming &amp; Leisure
---

### Post by bathini on 2006-01-14
Hello Friends

I recently installed Flightgear via synaptic package manager. When I go to game and select flightgear nothing happens. What could be the problem? Thanks

Bathini

---

### Post by ekarni on 2006-01-14
Try running it from the commandline -- I suspect you'll see some error messages.     The command is *fgfs*  Post the errors and I'll try to help (still pretty new myself).

---

### Post by bathini on 2006-01-15
Thanks Ekarni for replying, I have tried to run through the command line and I got this

terminate called after throwing an instance of 'std::bad_alloc'
  what():  St9bad_alloc
Aborted


Thanks

Bathini

---

### Post by ekarni on 2006-01-15
Looks like a memory issue somewhere inside Flightgear.  Afraid I don't have a clue as to fixing it.  Anyone have any ideas?

---

### Post by bathini on 2006-01-17
I am thinking of reinstalling flightgear from scratch. Anyone has any ideas how I should install flightgear? I am scared to reinstall using synaptic manager. 

Thanks

Bathini

---

### Post by nab on 2006-02-15
I installed flightgear today.

starting flightgear with fgfs --aircraft=c172p I get following error message:

fgfs --aircraft=c172p
fgfs: indirect_vertex_array.c:1359: __indirect_glTexCoordPointer: Assertion `a != ((void *)0)' failed.
Abgebrochen 

Well, I installed flightgear with Synaptic.

Any idea what's wrong?
(Googleing I didn't find anything useful - probaly my english is just good enough :-))

TIA,
Niko

---

