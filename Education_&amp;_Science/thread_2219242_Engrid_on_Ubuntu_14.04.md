---
title: "Engrid on Ubuntu 14.04"
date: 2014-04-23
forum: Education &amp; Science
---

### Post by aerodinesh on 2014-04-23
Hi my dear friends,
I need your help. I successfully compiled [engrid]("https://github.com/enGits/engrid/wiki/%5BenGrid-1.4%5D-Installation") (3D mesh generator for CFD analysis) in Ubuntu 14.04. Everything went smooth till the end. But when I try to open it from command prompt or start menu, nothing happenings.. Whats wrong? Any ideas...


Hi Friends,
i solved this by compiling enGrid from the Source. 


[https://github.com/enGits/engrid/wiki/%5BenGrid-1.4%5D-Installation#Building_enGrid_on_an_Ubuntu_system](https://github.com/enGits/engrid/wiki/%5BenGrid-1.4%5D-Installation#Building_enGrid_on_an_Ubuntu_system)

---

### Post by Gowain on 2014-06-18
Hi there

I am also trying to install engrid on ubuntu 14.04 and have the same problems as you. I would be most grateful if you could tell me how to instal it properly, I have tried installing it via the link you shared and also from the bash script at the top of the page on the link you shared.
any help would be most appreciated!

regards
gowain

---

### Post by Gowain on 2014-06-18
Hi

I have followed the instructions in the above post for installing  engrid; when the programme is compiling I believe the faults are in  these two lines of code:
can someone please assist me and help me to install Engrid on Ubuntu  14.04, I have changed os from fedora 20 just to achieve this. 
What is the problem with engrid scripts and new distros.
I did not have this issue with openfoam.

/usr/bin/ld: cannot find -ltcl8.5
collect2: error: ld returned 1 exit status
make[2]: *** [engrid] Error 1
make[2]: Leaving directory `/home/gowain/software/engrid-release-1.4/src'
make[1]: *** [release] Error 2
make[1]: Leaving directory `/home/gowain/software/engrid-release-1.4/src'
make: *** [sub-engrid-pro-app-make_default-ordered] E

---

### Post by aerodinesh on 2015-05-04
Solved by following this..

[COLOR=#000000][FONT=Tahoma]qmake-qt4 --version[/FONT][/COLOR]
[COLOR=#000000][FONT=Tahoma]qmake-qt5 --version[/FONT][/COLOR]
[COLOR=#000000][FONT=Tahoma]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Tahoma]sudo apt-get install libqt4-dev
make clean[/FONT][/COLOR]
[COLOR=#000000][FONT=Tahoma]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Tahoma]**Go into the folder "engrid/src".**
make clean
rm Makefile* libengrid/Makefile* netgen_svn/Makefile*
source scripts/setup_pathes.bash
export PATH=$PWD/scripts:$PATH[/FONT][/COLOR]
[COLOR=#000000][FONT=Tahoma]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Tahoma]sudo apt-get install tcl8.5 tcl8.5-dev[/FONT][/COLOR]
[COLOR=#000000][FONT=Tahoma]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Tahoma]Continue following the instructions from the step #7[/FONT][/COLOR]

---

