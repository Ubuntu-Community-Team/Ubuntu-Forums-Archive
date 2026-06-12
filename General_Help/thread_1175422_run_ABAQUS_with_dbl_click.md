---
title: "run ABAQUS with dbl click"
date: 2009-06-01
forum: General Help
---

### Post by bajsi on 2009-06-01
I need to run ABAQUS with a dbl click on a .cae file so that it runs in proper dir.
I created a script to do the job:

#! /bin/bash
PATH=${1%/*}
FILE=${1##*/} 
cd $PATH
XLIB_SKIP_ARGB_VISUALS=1 /opt/abaqus/6.7-1/exec/abq671.exe cae database=$FILE

In nautilus I edited properties for .cae files so that it opens with this script. 
It appears to be working fine (opens the file in proper dir), but it (ABAQUS) fails spawning a new process (I think) to run calculations. 
Running "XLIB_SKIP_ARGB_VISUALS=1 /opt/abaqus/6.7-1/exec/abq671.exe cae" from terminal (in a proper dir) works beautifully.

The script runs without a terminal window, so I cannot see what could be the problem, how can I change that?

I also tried to modify the script with:

RUN="XLIB_SKIP_ARGB_VISUALS=1 /opt/abaqus/6.7-1/exec/abq671.exe cae database="+$FILE
xterm -e $RUN &

but with no luck.

Any help appreciated.

---

