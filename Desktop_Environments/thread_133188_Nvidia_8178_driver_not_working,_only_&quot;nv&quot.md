---
title: "Nvidia 8178 driver not working, only &quot;nv&quot; works"
date: 2006-02-19
forum: Desktop Environments
---

### Post by ruddyadam on 2006-02-19
I have a 1000 mhz athlon, k7s5a 3.1 mobo, 256 mb pc133, ubuntu 2.6.12-10-386, asus v8420 ti4200. 

I have tried every howto I can find to get this nvidia driver to load, even this one:  [http://ubuntuforums.org/showthread.php?t=75074]("http://ubuntuforums.org/showthread.php?t=75074") but no luck with anything.  I have  done the CC=gcc-3.4 in root and user and export thing, but no matter what I have done so far, if I change "nv" to "nvidia" in my xorg.conf file, then x will not start.  It ALWAYS will say that it failed to load the nvidia.ko file.  The nvidia installer also doesn't work because, even though it builds the driver, it cannot install it because it says it was built with a different kernel than the one I am using and mentions something about --kernel-source-path.  I suppose that means it wants to know the path to my kernel sources, but I don't exactly what to point it to.  When I change that one line from "nvidia" to "nv" everything is hunky dory and starts upwithout a hitch.  I just know that my videocard is capable of more than it is giving me.

Anyone ran into this same problem?  Any help?  Thanks!
Adam

---

### Post by rjwood on 2006-02-19
did you leave a message on that thread for tseliot? If not then that is what I suggest you do. He knows that stuff real well....Good Luck!!

---

### Post by ruddyadam on 2006-02-19
Thanks for the suggestion - will do!

---

