---
title: "LD_LIBRARY_PATH vs ld.so.conf"
date: 2009-04-29
forum: General Help
---

### Post by devel09 on 2009-04-29
Hello All,

I am trying to set an LD_LIBRARY_PATH in my ubuntu 8.10 to reference a native library libJavaxUsb.so. When I try to run my java app in netbeans 6.5.1 it doesn't see this library.
I've tried adding it to the /usr/lib directory, and added a reference it in the /etc/ld.so.conf file, but no luck seeing this library. I keep getting a java.lang.UnsatisfiedLinkError, which basically means it can't find the native library. Does any one know is there any additional settings I need to do in ubuntu or is there a bug or doing wrong? Or does anyone know netbeans on ubuntu.

thanks
ed

---

### Post by taurus on 2009-04-29
Did you remember to run **sudo ldconfig** after you've modified /etc/ld.so.conf?

---

### Post by devel09 on 2009-04-29
Yes I did reload ldconfig

---

### Post by sdennie on 2009-04-29
You could try to LD_PRELOAD the library before running either it or netbeans.  It's just:

```

LD_PRELOAD=/place/your/lib/lives binary_you_want_to_run

```

That forces the loading of the library before the binary even requests it.

---

