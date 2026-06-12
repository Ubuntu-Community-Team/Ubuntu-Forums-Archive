---
title: "strange behavior of nautilus"
date: 2009-05-07
forum: General Help
---

### Post by sa-mejia on 2009-05-07
By some weird reason, that I completely ignore, there is now a particular directory in Nautilus that, whenever I click on it, it makes nautilus collapse and restart again.  

I can access the files in the directory (and subdirectories) without any problem from the terminal, but I can not access them within nautilus.  As soon as I click on this directory, nautilus closes and restarts.

In case this information is useful, this began happening as I was committing a few files into my subversion repository within this directory, with a program called nautilussvn ([http://code.google.com/p/nautilussvn/](http://code.google.com/p/nautilussvn/)).

Any help is appreciated.

Santiago.

---

### Post by sa-mejia on 2009-05-07
Bump.

(anyone can tell me why my post does not appear in boldface, but just in ordinary typeface?).

Santiago.

---

### Post by sa-mejia on 2009-05-07
SOLVED:  It is actually a problem with nautilussvn in Hardy. 

The mantainer was very quick in responding me and helpful. Here is what he had to say:

Sounds like Issue #102 to me, see:

[http://code.google.com/p/nautilussvn/issues/detail?id=102](http://code.google.com/p/nautilussvn/issues/detail?id=102)

If so then since this is basically a broken working copy just do an
svn update.

---

### Post by Elfy on 2009-05-07
> (anyone can tell me why my post does not appear in boldface, but just in ordinary typeface?).Only unread threads are in bold - you'd already read it :)

It should appear in bold to you until you've read this.

---

