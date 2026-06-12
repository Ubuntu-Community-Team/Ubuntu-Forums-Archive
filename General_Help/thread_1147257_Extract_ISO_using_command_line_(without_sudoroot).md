---
title: "Extract ISO using command line (without sudo/root)"
date: 2009-05-03
forum: General Help
---

### Post by Kjella on 2009-05-03
Does anyone know of a command line too to extract an iso image to a directory without using mount, because it requires root access? I know the difference, just looking for a way to do:

extractiso foo.iso /path/to/dir

and have all the file structure of foo.iso put into /path/to/dir. Strangely enough I find tools to create it, just no option to do the opposite.

---

### Post by MaxIBoy on 2009-05-03
[s]The easiest way is to mount the ISO as a CD and then copy/paste everything. In Ubuntu, you can mount it graphically without using root (which is actually one of the things I changed on my laptop, for security reasons, and you may wish to do the same.) To do it on the command line, you need to be root. There are other ways, but using this way is just the easiest. 


If you're on someone else's machine and don't have their password, you really shouldn't try to circumvent that. :P[/s]



Wow, just wow.

---

### Post by geirha on 2009-05-03
Right click the iso, and choose Open with Archive Manager ...

---

### Post by MaxIBoy on 2009-05-03
> **geirha said:**
> Right click the iso, and choose Open with Archive Manager ...Darn you, GNOME!


Yeah, I kinda forgot about that.

---

### Post by geirha on 2009-05-03
You can run the archive manager from the command-line too.
```
file-roller -e /path/to/extract/to /path/to/iso
```

---

