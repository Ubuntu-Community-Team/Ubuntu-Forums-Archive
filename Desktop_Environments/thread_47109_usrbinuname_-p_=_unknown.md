---
title: "/usr/bin/uname -p = unknown"
date: 2005-07-07
forum: Desktop Environments
---

### Post by cotcot on 2005-07-07
When I try to compile something I sometimes get (config.log): 

/usr/bin/uname -p = unknown
/bin/uname -X     = unknown

/bin/arch              = i686
/usr/bin/arch -k       = unknown
/usr/convex/getsysinfo = unknown
hostinfo               = unknown
/bin/machine           = unknown
/usr/bin/oslevel       = unknown
/bin/universe          = unknown

This was for instance the case with PanoTools. The command 'uname' and 'arch' are in my  /bin , not in /usr/bin. 
Other reasons for stopping the compiling are command G++ or C++ not found although GCC 3.4 is installed. (I do not add the config.log since it is quite long) I only hope somebody recognises this and has a tip or suggestion.

What is wrong ?

---

### Post by intangible on 2005-07-07
uname -p or -X aren't valid options for uname, dunno if they ever were, but the page I found for PanoTools ([http://www.path.unimelb.edu.au/~dersch/](http://www.path.unimelb.edu.au/~dersch/)) hasn't been updated since 2001... they may need to update their sources to be compatible with the newer linuxes.

---

### Post by forger on 2006-10-13
I have the same problem:

$ uname -i
unknown
$ uname -p
unknown

then i found out a quick solution:
$ cat /proc/cpuinfo | grep "model name"
model name      : AMD Sempron(tm)   2500+

the problem is.. how do i get only "AMD Sempron(tm)   2500+" ? :\

---

### Post by forger on 2006-10-13
hmmm with a bit of reading and a hint to use sed, i made this:
cat /proc/cpuinfo | grep "model name" | sed -e 's/model name\t: //' -e 's/\s\s\s/ /'

:)

---

