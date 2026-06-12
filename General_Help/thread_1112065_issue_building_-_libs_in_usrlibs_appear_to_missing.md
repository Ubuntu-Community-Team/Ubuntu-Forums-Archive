---
title: "issue building - libs in /usr/libs appear to missing 'top level' symlinks?"
date: 2009-03-31
forum: General Help
---

### Post by richardjb on 2009-03-31
Hi

Apologies if this is an issue that I should be able to find a solution for, but I have spent a good number of hours searching around the 'net in general and these forums but...

I'm relatively new to using Ubuntu as a development platform but we are seeing an interesting issue while attempting to do initial builds of an application we are developing.

The application is built against Qt (4.5.0) and although the compile is successfull, we are are failing at the link stage.

The (first) is -lgobject-2.0

What I'm posting for, is that as expected, in /usr/lib there is the following files

libgobject-2.0.so.0 -> libgobject-2.0.so.0.1800.2
libgobject-2.0.so.0.1800.2

What I am surprised about, is that I would have expected an extra symlink

libgobject-2.0.so -> libgobject-2.0.so.0

since this is basically what the linker is looking for.

Therefore, I guess I'm asking:

1) is my install wrong? (I don't think so, since it is the same on all the Ibex installs we have running)?
2) what do I need to do to allow me to build against these libs?

Many thanks in advance for any help/advice.

Thanks and regards,
Richard

---

