---
title: "Omnetpp"
date: 2008-03-20
forum: Education &amp; Science
---

### Post by conrg on 2008-03-20
HI there, i have a path problem and i think its got something to do with my .bashrc file.

I am trying to install omnet on to ubuntu and during the configure stage i am getting warnings during set up. So I get warnings, the warnings tell me to make changes to my bashrc file, i do that and I get rid of all but one warning, below is that warning. 

===============
WARNING: your PATH doesn't contain /home/nikki/omnetpp-3.4b2/bin!
Add the following line to your startup file:
  export PATH=$PATH:/home/nikki/omnetpp-3.4b2/bin  # .(bash_)profile if you use sh/bash
  setenv PATH $PATH:/home/nikki/omnetpp-3.4b2/bin  # .cshrc if you use csh,tcsh etc.
===============


however in my .bashrc i have that path, here is the part of the .bashrc file that contains the path that the warning is asking for.


===============
export PATH=$PATH:/home/nikki/omnetpp-3.4b2/bin
export TCL_LIBRARY=/usr/lib/tcl8.4
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/home/nikki/omnetpp-3.4b2/lib
===============

so as you can see, the first line is the exact same that the warning is asking for, It makes no difference, the warning keeps on coming.

so i continue and try to 'make' build the4 software anyway.
i get the following error


===================
opp_msgc -Xnc -Xns sim_std.msg
make[1]: opp_msgc: Command not found
make[1]: *** [sim_std_m.cc] Error 127
make[1]: Leaving directory `/home/nikki/omnetpp-3.4b2/src/sim'
make: *** [sim] Error 2
nikki@computer:~/omnetpp-3.4b2$ 
===================

iv been on the forums and explanations are given that just dont match the problem that im getting.
I have no clue what is going on here

can you help

thanks for reading

---

### Post by aJayRoo on 2008-03-20
Have you opened up a new terminal and tried this? You need to source the .bashrc file
```
source ~/.bashrc
```
however the most foolproof way of doing this is just to start a new terminal.

---

