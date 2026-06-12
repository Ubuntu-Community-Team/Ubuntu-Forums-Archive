---
title: "Compile/Make errors-"
date: 2009-02-20
forum: General Help
---

### Post by TristanM-Tx on 2009-02-20
During the installation of 3d Desktop (c++), there were several libraries I had to locate/google in order to get ./configure to finish without errors.  Now that I have gotten it finished with the configure part, I proceeded to run make, and noticed alot of errors in the code which produced "deprecated conversion from string constant to ‘char*’" errors all over the place in the functions they are implementing.  This is from the source that I downloaded from FreshMeat today, so to be told that something is deprecated seems a little weird.  Make terminates with

make[1]: *** [3ddeskd.o] Error 1
make[1]: Leaving directory `/home/admin2/3ddesktop-0.2.9'
make: *** [all] Error 2

Is it possible that the package is indeed fine, but that I would need more libraries or something?  I am more familiar with configure than with make (as far as how they work).  I suspect that there would be some command line option to implement to interpret these deprecated code errors, and that this would not be specific to the code that I am working with.

Anyone faced this before?
Thanks

---

### Post by snova on 2009-02-20
> **TristanM-Tx said:**
> I proceeded to run make, and noticed alot of errors in the code which produced "deprecated conversion from string constant to &#8216;char*&#8217;" errors all over the place in the functions they are implementing.

Those should only be warnings, not errors. It's fine.

> Make terminates with

make[1]: *** [3ddeskd.o] Error 1
make[1]: Leaving directory `/home/admin2/3ddesktop-0.2.9'
make: *** [all] Error 2

Re-run make, and post it's output. That'll repeat the error; we need a bit more context.

---

