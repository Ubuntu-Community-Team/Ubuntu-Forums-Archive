---
title: "d2x-xl rar file not extracting"
date: 2010-03-19
forum: Gaming &amp; Leisure
---

### Post by Affrikka on 2010-03-19
I recently stumbled upon [d2x-xl](http://sourceforge.net/projects/d2x-xl) and installed the rar file.

I go to extract the rar file into a separate d2x-xl folder, and it says that all files have been successfully extracted, but only half of them are.

The rar file contains:

console
d2x-trackir
effects
gameio
gamesmodes
iff
include
input
intel
io
libmve
lighting
main
maths
mem
menus
misc
models
network
objects
ogl
physics
render
setup
src
VC6
VC8
VC9
weapons (those are all folders) (these next ones are files)
.cproject
.project
conf.h
d2x-w32.ico
d2x-xl-2.ico
d2x-xl-banner.bmp
d2x-xl-makefiles.rar
d2x-xl.ico
d2x.w32.rc
descent.ico
INSTALL
LICENSE
resource.h

------

the only things extracting is

console
Intel
menus
objects
physics
setup
VC6
VC8
VC9

-----

yes, i've clicked show hidden folders, and i've tried extracting through a terminal, and in the terminal it just shows everything as "Failed" and when i go to extract just one file, for example, INSTALL, it just shows something about "unrar --k failed, use unrar --help or unrar --usage for more help"

so yeah..... what do i do? :P


thanks!




Mathieu

---

### Post by hikaricore on 2010-03-19
Sounds like a corrupt archive.  Try downloding it again or from another location.

---

### Post by Affrikka on 2010-03-19
i've downloaded it both from sourceforge and the official website itself, and softpedia, same result, same folders.

---

### Post by hikaricore on 2010-03-20
Link me the file and I'll test it out.

---

### Post by Affrikka on 2010-03-20
[http://sourceforge.net/projects/d2x-xl/](http://sourceforge.net/projects/d2x-xl/)

---

### Post by DoktorSeven on 2010-03-20
You might need the non-free version of unrar from the repos, try that.

---

### Post by Affrikka on 2010-03-20
thanks!!!! that solved it :)

---

