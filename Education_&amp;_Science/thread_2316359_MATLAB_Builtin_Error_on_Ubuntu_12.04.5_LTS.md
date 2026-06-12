---
title: "MATLAB Builtin Error on Ubuntu 12.04.5 LTS"
date: 2016-03-07
forum: Education &amp; Science
---

### Post by manyboringevenings on 2016-03-07
Hi,

I have a Lenovo N586 running Ubuntu 12.04.5 LTS. I recently installed MATLAB 2015b using the instructions here: [https://help.ubuntu.com/community/MATLAB](https://help.ubuntu.com/community/MATLAB). (I installed the matlab-support package as per the instructions above, and when it came time to rename the gcc libraries, I opted to do so.)

When MATLAB starts up, the following error is dispalyed in the Command Window:
```
Warning: Initializing Java preferences failed in matlabrc.
This indicates a potentially serious problem in your MATLAB setup, which should be resolved as soon as possible.  Error detected was:
MATLAB:dispatcher:loadLibrary
Can't load '/usr/local/MATLAB/R2015b/bin/glnxa64/libmwwkspintrospect.so': /usr/lib/x86_64-linux-gnu/libstdc++.so.6: version `GLIBCXX_3.4.17' not found (required by /usr/local/MATLAB/R2015b/bin/glnxa64/libmwwkspintrospect.so)
```

In addition, any time a command is executed, I get a pop-up window which says the following:
```
Error using builtin can't reload '/usr/local/MATLAB/R2015b/bin/glnxa64/libmwwkspintrospect.so'
```

I have successfully installed older MATLABs on other Ubuntu systems following the above instructions, but I can't remember if I've opted to rename the gcc libraries. Thinking that this was the issued, I tried removing the matlab-support package (sudo apt-get remove matlab-support), but I doubt it changed the names back to their old ones. (What would be the command to do this?) In any case, it hasn't fixed the problem. Does anyone know how I can fix this issue, or completely purge the MATLAB installation I have and start from scratch?

Thanks!

P.S.: One thing I forgot to mention is that everything seems to be working OK, it's just that any command brings up this pop-up window error.

---

### Post by mörgæs on 2016-03-08
Hi, welcome the the fora.

According to [http://se.mathworks.com/support/sysreq/roadmap.html?s_tid=gn_loc_drop](http://se.mathworks.com/support/sysreq/roadmap.html?s_tid=gn_loc_drop) Matlab 2015b is only supported on 14.04. I would suggest that you begin with a fresh install (not upgrade) of this one.

---

### Post by manyboringevenings on 2016-03-08
Thanks for the advice. It was an easy fix apparently: I upgraded to 14.04.4 LTS. Seems to work OK now.

---

