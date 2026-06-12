---
title: "Xulrunner error in Eclipse"
date: 2009-06-02
forum: General Help
---

### Post by Cold-Gin on 2009-06-02
Ubuntu version 9.04
Eclipse version 3.4.2
Firefox version 3.0.10

Hi. I am receiving a java.lang.UnsatisfiedLink error in Eclipse whenever I try to open any .html or .xhtml file through the editor. When I open the Details section of the window, I see the following message

```

An error has occurred. See error log for more details.
.../eclipse/plugins/org.mozilla.xulrunner.gtk.linux.x86_1.8.1.3-20070904/xulrunner/libjavaxpcomglue.so: libstdc++.so.5: cannot open shared object file: No such file or directory

```

I tried doing an apt-get install xulrunner, and I also ran Software Update in Eclipse.

Does anybody know how to fix this?

Thanks.

---

### Post by Cold-Gin on 2009-06-03
Fixed it. You have to install libstdc++5 from Synaptic Package Manager. I found the solution here:

[http://www.jboss.org/index.html?module=bb&op=viewtopic&t=137163]("http://www.jboss.org/index.html?module=bb&op=viewtopic&t=137163")

---

