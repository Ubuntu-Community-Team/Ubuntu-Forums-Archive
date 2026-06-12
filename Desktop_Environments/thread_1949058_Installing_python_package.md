---
title: "Installing python package"
date: 2012-03-29
forum: Desktop Environments
---

### Post by kifcaliph on 2012-03-29
Hi

I'd like to know which way is executed when I type the following command in the terminal
**[COLOR="Green"]sudo apt-get install python-matplotlib[/COLOR]**
Is it **pip** or **easy_install**??

---

### Post by nutrapi on 2012-03-29
> **kifcaliph said:**
> Hi

I'd like to know which way is executed when I type the following command in the terminal
**[COLOR="Green"]sudo apt-get install python-matplotlib[/COLOR]**
Is it **pip** or **easy_install**??

Your best bet to have up to date packages is just to use pip or easy_install in the first place.

You might want to take a look at this post on using virtualenv, yolk, and pip..
[http://www.saltycrane.com/blog/2009/05/notes-using-pip-and-virtualenv-django/](http://www.saltycrane.com/blog/2009/05/notes-using-pip-and-virtualenv-django/)

---

### Post by scottstensland on 2012-03-29
I do not believe it is either.  Here is the terminal console output :

```
 sudo apt-get install python-matplotlib

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  blt libglade2-0 python-glade2 python-matplotlib-data python-pyparsing python-support python-tk python-tz tcl8.5 tk8.5 ttf-lyx
Suggested packages:
  blt-demo python-gtk2-doc dvipng ipython python-configobj python-excelerator python-matplotlib-doc python-qt3 python-qt4 python-scipy python-traits
  texlive-extra-utils texlive-latex-extra tix python-tk-dbg tclreadline
The following NEW packages will be installed:
  blt libglade2-0 python-glade2 python-matplotlib python-matplotlib-data python-pyparsing python-support python-tk python-tz tcl8.5 tk8.5 ttf-lyx
0 upgraded, 12 newly installed, 0 to remove and 0 not upgraded.
Need to get 8,446 kB of archives.
After this operation, 27.7 MB of additional disk space will be used.
Do you want to continue [Y/n]? 
Get:1 http://mirror.symnds.com/ubuntu/ precise/main libglade2-0 amd64 1:2.6.4-1ubuntu1 [52.7 kB]
Get:2 http://mirror.symnds.com/ubuntu/ precise/universe ttf-lyx all 2.0.2-1ubuntu2 [151 kB]
Get:3 http://mirror.symnds.com/ubuntu/ precise/main tcl8.5 amd64 8.5.11-1ubuntu1 [1,098 kB]
Get:4 http://mirror.symnds.com/ubuntu/ precise/main tk8.5 amd64 8.5.11-1 [1,003 kB]
Get:5 http://mirror.symnds.com/ubuntu/ precise/main blt amd64 2.4z-4.2ubuntu1 [1,717 kB]
Get:6 http://mirror.symnds.com/ubuntu/ precise/main python-glade2 amd64 2.24.0-3 [10.3 kB]
Get:7 http://mirror.symnds.com/ubuntu/ precise/universe python-matplotlib-data all 1.1.0-1 [1,948 kB]
Get:8 http://mirror.symnds.com/ubuntu/ precise/universe python-pyparsing all 1.5.2-2ubuntu1 [586 kB]
Get:9 http://mirror.symnds.com/ubuntu/ precise/main python-tz all 2011k-0ubuntu5 [44.9 kB]
Get:10 http://mirror.symnds.com/ubuntu/ precise/universe python-support all 1.0.14ubuntu2 [26.1 kB]
Get:11 http://mirror.symnds.com/ubuntu/ precise/universe python-matplotlib amd64 1.1.0-1 [1,781 kB]
Get:12 http://mirror.symnds.com/ubuntu/ precise/main python-tk amd64 2.7.3-1 [28.2 kB]
Fetched 8,446 kB in 1s (5,806 kB/s)
Selecting previously unselected package libglade2-0.
(Reading database ... 169888 files and directories currently installed.)
Unpacking libglade2-0 (from .../libglade2-0_1%3a2.6.4-1ubuntu1_amd64.deb) ...
Selecting previously unselected package ttf-lyx.
Unpacking ttf-lyx (from .../ttf-lyx_2.0.2-1ubuntu2_all.deb) ...
Selecting previously unselected package tcl8.5.
Unpacking tcl8.5 (from .../tcl8.5_8.5.11-1ubuntu1_amd64.deb) ...
Selecting previously unselected package tk8.5.
Unpacking tk8.5 (from .../tk8.5_8.5.11-1_amd64.deb) ...
Selecting previously unselected package blt.
Unpacking blt (from .../blt_2.4z-4.2ubuntu1_amd64.deb) ...
Selecting previously unselected package python-glade2.
Unpacking python-glade2 (from .../python-glade2_2.24.0-3_amd64.deb) ...
Selecting previously unselected package python-matplotlib-data.
Unpacking python-matplotlib-data (from .../python-matplotlib-data_1.1.0-1_all.deb) ...
Selecting previously unselected package python-pyparsing.
Unpacking python-pyparsing (from .../python-pyparsing_1.5.2-2ubuntu1_all.deb) ...
Selecting previously unselected package python-tz.
Unpacking python-tz (from .../python-tz_2011k-0ubuntu5_all.deb) ...
Selecting previously unselected package python-support.
Unpacking python-support (from .../python-support_1.0.14ubuntu2_all.deb) ...
Selecting previously unselected package python-matplotlib.
Unpacking python-matplotlib (from .../python-matplotlib_1.1.0-1_amd64.deb) ...
Selecting previously unselected package python-tk.
Unpacking python-tk (from .../python-tk_2.7.3-1_amd64.deb) ...
Processing triggers for fontconfig ...
Processing triggers for man-db ...
Processing triggers for doc-base ...
Processing 1 added doc-base file...
Registering documents with scrollkeeper...
Setting up libglade2-0 (1:2.6.4-1ubuntu1) ...
Setting up ttf-lyx (2.0.2-1ubuntu2) ...
Setting up tcl8.5 (8.5.11-1ubuntu1) ...
update-alternatives: using /usr/bin/tclsh8.5 to provide /usr/bin/tclsh (tclsh) in auto mode.
Setting up tk8.5 (8.5.11-1) ...
update-alternatives: using /usr/bin/wish8.5 to provide /usr/bin/wish (wish) in auto mode.
Setting up blt (2.4z-4.2ubuntu1) ...
Setting up python-glade2 (2.24.0-3) ...
Setting up python-matplotlib-data (1.1.0-1) ...
Setting up python-pyparsing (1.5.2-2ubuntu1) ...
Setting up python-tz (2011k-0ubuntu5) ...
Setting up python-support (1.0.14ubuntu2) ...
Setting up python-matplotlib (1.1.0-1) ...
Setting up python-tk (2.7.3-1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for python-support ...

```

---

