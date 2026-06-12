---
title: "More Plugins for Compiz Fusion"
date: 2009-04-19
forum: General Help
---

### Post by DevinMcElheran on 2009-04-19
I've tried multiple time to compile compiz plugins, but they keep saying that I don't have a target for my "make" command. Any ideas why? All help is appreciated.

---

### Post by Tim Sharitt on 2009-04-19
Make sure there is a makefile in the directory in which you are running make. If there is not a makefile but there is a configure scrit, you probably need to run the configure script first to generate the makefiles.

The command to run the configuration script
```
./configure
```

if that does not work, you may need to run
```
sh ./configure
```

---

### Post by DevinMcElheran on 2009-04-19
I tried the "Sh ./configure" and the out put said that I can't open it.

---

