---
title: "how to install different gcc version"
date: 2009-05-06
forum: General Help
---

### Post by david.v on 2009-05-06
hi all,

 I am trying to install gcc 3.4.0 (needed to compile a specific c++ module) without uninstalling the default version of gcc 4.3.2 (in ubuntu 8.10). As I know, I have to install the new version in a different directory and after that, in order to compile with it, just to indicate the path where the new version is. Although I have tried to do this in some different ways I still haven't found the solution.

Has somebody already do this? Could you please tell me where and how you installed the new compiler?

thanks a lot

---

### Post by geirha on 2009-05-06
Just install the [g++-3.4](apt:g++-3.4) package, and use g++-3.4 instead of g++ when you compile. The different versions will happily coexist.

However, it's probably better to just fix the code to compile with the latest compiler.

---

