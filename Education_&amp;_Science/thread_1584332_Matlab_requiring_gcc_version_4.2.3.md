---
title: "Matlab requiring gcc version 4.2.3"
date: 2010-09-29
forum: Education &amp; Science
---

### Post by jdvdas on 2010-09-29
Hi,
I have installed Matlab2010a in Ubuntu 10.04(LTS). 
I made a very simple state-flow model named sf1.mdl. But,whenever I am starting the simulation it shows the following error. I am new to both Ubuntu and using state-flow. I have posted this in the Matlab Central Newsgroup as well. But cannot find any solution. Plz help. 



Making simulation target "sf1_sfun", ... 


/usr/local/Matlab2010/bin/mex -c -O -DMATLAB_MEX_FILE -I/usr/local/Matlab2010/toolbox/stateflow/stateflow/../../../simulink/include -I/usr/local/Matlab2010/toolbox/stateflow/stateflow/../../../extern/include -I/usr/local/Matlab2010/stateflow/c/mex/include -I/usr/local/Matlab2010/stateflow/c/debugger/include sf1_sfun.c

Warning: You are using gcc version "4.4.3-4ubuntu5)". The version
         currently supported with MEX is "4.2.3".
         For a list of currently supported compilers see: 
         [http://www.mathworks.com/support/compilers/current_release/](http://www.mathworks.com/support/compilers/current_release/)

/usr/local/Matlab2010/bin/mex -c -O -DMATLAB_MEX_FILE -I/usr/local/Matlab2010/toolbox/stateflow/stateflow/../../../simulink/include -I/usr/local/Matlab2010/toolbox/stateflow/stateflow/../../../extern/include -I/usr/local/Matlab2010/stateflow/c/mex/include -I/usr/local/Matlab2010/stateflow/c/debugger/include sf1_sfun_registry.c

Warning: You are using gcc version "4.4.3-4ubuntu5)". The version
         currently supported with MEX is "4.2.3".
         For a list of currently supported compilers see: 
         [http://www.mathworks.com/support/compilers/current_release/](http://www.mathworks.com/support/compilers/current_release/)

/usr/local/Matlab2010/bin/mex -c -O -DMATLAB_MEX_FILE -I/usr/local/Matlab2010/toolbox/stateflow/stateflow/../../../simulink/include -I/usr/local/Matlab2010/toolbox/stateflow/stateflow/../../../extern/include -I/usr/local/Matlab2010/stateflow/c/mex/include -I/usr/local/Matlab2010/stateflow/c/debugger/include c1_sf1.c

Warning: You are using gcc version "4.4.3-4ubuntu5)". The version
         currently supported with MEX is "4.2.3".
         For a list of currently supported compilers see: 
         [http://www.mathworks.com/support/compilers/current_release/](http://www.mathworks.com/support/compilers/current_release/)


/usr/local/Matlab2010/bin/mex -silent LDFLAGS="\$LDFLAGS " -output sf1_sfun.mexglx sf1_sfun.o sf1_sfun_registry.o c1_sf1.o /usr/local/Matlab2010/stateflow/c/mex/lib/glnx86/sfc_mex.a /usr/local/Matlab2010/stateflow/c/debugger/lib/glnx86/sfc_debug.a -L/usr/local/Matlab2010/bin/glnx86 -lfixedpoint -lut -lmwmathutil -lemlrt -lmwblascompat32 -L/usr/local/Matlab2010/bin/glnx86 -lippmwipt

Warning: You are using gcc version "4.4.3-4ubuntu5)". The version
         currently supported with MEX is "4.2.3".
         For a list of currently supported compilers see: 
         [http://www.mathworks.com/support/compilers/current_release/](http://www.mathworks.com/support/compilers/current_release/)

/usr/bin/ld: cannot find -lstdc++
collect2: ld returned 1 exit status

    mex: link of ' "sf1_sfun.mexglx"' failed.

gmake: *** [sf1_sfun.mexglx] Error 1

---

### Post by dirghrabadia on 2010-09-29
I am not quite sure of what you might need here. You might want to try Octave ([http://www.gnu.org/software/octave/](http://www.gnu.org/software/octave/)). Its compatible with Matlab for most cases :)

---

### Post by jdvdas on 2010-09-29
I am not sure. But I think this is something to do with the version of the gcc that these are using, as evident from the warning.

Warning: You are using gcc version "4.4.3-4ubuntu5)". The version
currently supported with MEX is "4.2.3".

---

### Post by jdvdas on 2010-09-29
Hi,

I found a way out. Installation of gcc-4.2 using apt-get solves the problem.

Thanks

---

