---
title: "glib required.... anjuta error"
date: 2006-07-09
forum: Desktop Environments
---

### Post by Choad on 2006-07-09
firstly.... love the new look of the forum :D

secondly, i fixed most of the errors anjuta gave me when going through the new project wizard, but one error remains.

i have libglib1.2-dev installed in synaptic, but it still complains that i dont have glib installed!

what shall i do to fix this?

---

### Post by Choad on 2006-07-10
bump 

anyone?

glib....

---

### Post by ronintiger on 2006-08-22
Hi there!

I to installed Anjuta and stumbled upon the same error as you:confused: I was surprised to see that there were  packages that needed to be installed to Anjuta work.. (automake...) finaly after installing everything that Anjuta complainned missing I got the same error as you.. missing glib ](*,) 

I haven't discovered how to fix this... anyone knows how?

Thanx in advance.

---

### Post by naglis on 2006-08-25
I had this problem too. But I fixed it.
1. Go to freshmeat.net/projects/glib/
2. Download the tarball and then install it.
3. It should work...

---

### Post by ronintiger on 2006-08-26
OK! Thanks I'll try that :D

---

### Post by Woei on 2006-08-26
> **Choad said:**
> firstly.... love the new look of the forum :D

secondly, i fixed most of the errors anjuta gave me when going through the new project wizard, but one error remains.

i have libglib1.2-dev installed in synaptic, but it still complains that i dont have glib installed!

what shall i do to fix this?

I'd gather you're trying to build a GTK2.0 program, instead of one using the deprecated and quite old GTK1.2 toolkit. For that, you'll need to install libglib2.0-dev.

Moreover, this is in the wrong forum for your question, it should be moved to the programming forum.

---

