---
title: "trying to install diablo"
date: 2006-08-19
forum: Desktop Environments
---

### Post by dexter on 2006-08-19
Hello,

i'm trying to install diablo, a better link-time optimizer (see [http://www.elis.ugent.be/diablo)](http://www.elis.ugent.be/diablo)). The install instructions can be found here: 
[http://www.elis.ugent.be/diablo/?q=node/130](http://www.elis.ugent.be/diablo/?q=node/130)

However, all three options fail for me, using the script stops, compiling everything manually doesn't work completely. As a last option I downloaded the rpm's and made .deb files off them using alien. This last method seems to go fine, except that i have a dependency problem, using dpkg i get this error:
```

pieter@Homer:~/Desktop$ sudo dpkg -i diabloflowgraph_0.4.2-1_i386.deb 
Selecting previously deselected package diabloflowgraph.
(Reading database ... 145518 files and directories currently installed.)
Unpacking diabloflowgraph (from diabloflowgraph_0.4.2-1_i386.deb) ...
dpkg: dependency problems prevent configuration of diabloflowgraph:
 diabloflowgraph depends on libjudydebian1 (<< 1.0.0-99); however:
  Version of libjudydebian1 on system is 1.0.1-5.
dpkg: error processing diabloflowgraph (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 diabloflowgraph

```

As you can see libjudydebian is installed, but he doesn't take it. Do i need a lower version (i can't find one) or is there another problem ?

---

