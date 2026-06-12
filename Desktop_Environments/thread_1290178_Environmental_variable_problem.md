---
title: "Environmental variable problem"
date: 2009-10-13
forum: Desktop Environments
---

### Post by weshmario on 2009-10-13
Hi,
I'm using a text file to set some environmental variables, here it is:

export ROOTSYS=/home/mtr/root 
export PATH=$ROOTSYS/bin:$PATH
export LD_LIBRARY_PATH=/home/mtr/root/lib:$LD_LIBRARY_PATH
#export LD_LIBRARY_PATH=$ROOTSYS/include/:$LD_LIBRARY_PATH 
#export LMF_HOME=/usr/local/geant/lmf_v3.0 
#export ECAT7_HOME=/usr/local/geant/ecat

export GATEHOME=/usr/share/gate/gate_v5.0.0_p01
export G4VERSION=9.2
export G4INSTALL=/usr/share/geant4/geant4.9.2.p01
source /usr/share/gate/gate_v5.0.0_p01/env_gate.sh

This file is located in my /home/mtr directory(this is my ~ directory), and I just open a terminal, go to ~ and type "source script_GATE" (script_GATE is the name of this text file).
All seems fine,  but when I try to change directory with  cd $ROOTSYS , I'm getting:
: No such file or directory.
But if I type "export ROOTSYS=/home/mtr/root" explicitly to terminal window I have no
problem changing directory with cd $ROOTSYS, why is that ?
I'm new to linux, and was just trying to make some script as a short-cut to typing lines every time.

---

### Post by cholericfun on 2009-10-13
maybe try writing it as a bash script with

```
#!/bin/bash
```

and make it executable

---

### Post by weshmario on 2009-10-13
Do you mean to put  #!/bin/bash as a first line in my script file ?
I have just tried that, and I renamed script_GATE to script_GATE.sh,
the icon of the text file then changed to something with wheels :).
But it did not work, still the same problem.

---

### Post by cholericfun on 2009-10-13
did you make it executable?
```
chmod +x filename.sh
```

---

### Post by weshmario on 2009-10-13
Yes, I did make it executable. I've tried through GUI and by your command line, and then I did rummage that scrip a little bit, and at some point it worked !
That is I can now change directory with cd $ROOTSYS command, but the scrip looks exactly the same as the first one posted here.
I have a copy of old script that did not work, and I changed this script to executable (also using GUI and your command line), but this old scrip did not work.
This scripts look exactly the same, but when I run diff on them this is the output:

2c2
< export ROOTSYS=/home/mtr/root
---
> export ROOTSYS=/home/mtr/root
17d16
< 

maybe they are different ?, but I don't understand diff tool, they look exactly the same thing to me. What is happening here ?:(

---

