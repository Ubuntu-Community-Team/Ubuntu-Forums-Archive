---
title: "format of Pagemap???"
date: 2009-02-04
forum: General Help
---

### Post by tonyh1986 on 2009-02-04
In each process's associated /proc/ directory, there is a pagemap binary file that maps the virtual page frame to the physcial page frame. Do anyone know what's the format of that file?

I have done some research on this one, the documentation on the codes seems pretty confusing that it says 0-55 is supposed to be the page frame number, then somehow bit 55 is used for another purpose. 

Also, since x86 is little-endian format, the binary file that was dumped by the od needs to be interpreted differently than what it seemingly looks like, does any one knows how to interpret that? 

Thanks a lot.

---

### Post by tonyh1986 on 2009-02-04
can anyone help with this? I need this to get an assignment done...

---

