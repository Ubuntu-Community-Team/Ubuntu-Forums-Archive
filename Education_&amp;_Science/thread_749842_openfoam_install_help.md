---
title: "openfoam install help"
date: 2008-04-08
forum: Education &amp; Science
---

### Post by basilwatson on 2008-04-08
Have tried to follow the how to but I am not sure how to set up the variables ...here is the output test file ;

Setting the home directory I think is the problem ...but how do I do that .

any Ideas on the problem 

Kind regards Stephen 


Try to relax and enjoy the crisis.
                -- Ashleigh Brilliant
bash: /home/s/OpenFOAM/OpenFOAM-1.4.1/.OpenFOAM-1.4.1/bashrc: No such file or directory
s@s-desktop:~$ /home/s/OpenFOAM/linux/OpenFOAM-1.4.1/bin/foamInstallationTest
Executing /home/s/OpenFOAM/linux/OpenFOAM-1.4.1/bin/foamInstallationTest:


Checking basic setup...
-------------------------------------------------------------------------------
Shell:              bash
Host:               s-desktop
OS:                 Linux version 2.6.22-14-generic
User:               s
User_config:        /home/s/.bashrc
Foam_config:        /home/s/.OpenFOAM-1.4.1/bashrc sourced correctly.

FATAL ERROR Foam install directory not set.

Set correct path to installation 'WM_PROJECT_INST_DIR' in /home/s/.foam2.3/bashrc
-------------------------------------------------------------------------------


Checking main FOAM env variables...
-------------------------------------------------------------------------------
Environment_variable Set_to_file_or_directory                Valid      Crit
-------------------------------------------------------------------------------
$WM_PROJECT_INST_DIR --------- env variable not set ---------            yes
$WM_PROJECT_USER_DIR --------- env variable not set ---------            no
$FOAM_JOB_DIR        --------- env variable not set ---------            yes
-------------------------------------------------------------------------------


Checking the FOAM env variables set on the PATH...
-------------------------------------------------------------------------------
Environment_variable Set_to_file_or_directory                Valid Path Crit
-------------------------------------------------------------------------------
$WM_PROJECT_DIR      --------- env variable not set ---------            yes

$FOAM_USER_APPBIN    --------- env variable not set ---------            no
$FOAM_APPBIN         --------- env variable not set ---------            yes
$WM_DIR              --------- env variable not set ---------            yes
$FOAMX_PATH          --------- env variable not set ---------            yes
$CEI_HOME            --------- env variable not set ---------            no

$JAVA_PATH           --------- env variable not set ---------            no
$MICO_ARCH_PATH      --------- env variable not set ---------            yes
$LAM_ARCH_PATH       --------- env variable not set ---------            yes
$MPICH_ARCH_PATH     --------- env variable not set ---------            no
-------------------------------------------------------------------------------


Checking the FOAM env variables set on the LD_LIBRARY_PATH...
-------------------------------------------------------------------------------
Environment_variable Set_to_file_or_directory                Valid Path Crit
-------------------------------------------------------------------------------
$FOAM_LIBBIN         --------- env variable not set ---------            yes
$FOAM_USER_LIBBIN    --------- env variable not set ---------            no
$LAM_ARCH_PATH       --------- env variable not set ---------            yes
-------------------------------------------------------------------------------


Software versions
-------------------------------------------------------------------------------
Software Version   Location 
-------------------------------------------------------------------------------
gcc      4.1.3    
WARNING:  Conflicting installations:
          foam settings: /bin/gcc
          current path : /usr/bin/gcc
          CRITICAL ERROR

java     1.6.0_03 
WARNING:  Conflicting installations:
          foam settings: /bin/java
          current path : /usr/bin/java

gzip     1.3.12    /bin/gzip                                                
tar      1.3.12    /bin/tar                                                 
icoFoam  *** not installed ***
          CRITICAL ERROR

-------------------------------------------------------------------------------


Checking file/directory permissions...
-------------------------------------------------------------------------------
File/directory                                    Set  Reqd Crit
-------------------------------------------------------------------------------


Checking networking...
-------------------------------------------------------------------------------
Action                   Result                                       Crit
-------------------------------------------------------------------------------
Pinging_s-desktop        Successful                                   yes 
Pinging_localHost        Successful                                   yes 
Test_rsh:                Unsuccessful_connection_refused*             yes
Test_ssh:                Successful                                   yes
(*) Only one of rsh or ssh is required by the Foam enviroment.

-------------------------------------------------------------------------------

Base configuration ok.

The foam installation contains 2 critical error(s).

Review the output for warning messages and consult 
the installation guide for trouble shooting.

s@s-desktop:~$

---

### Post by basilwatson on 2008-04-10
recieved some help from the open foam forum ,  But still no joy( I moved the fiiles checked everything  )  Just need to set that working directory 

any Ideas anyone 

Stephen 

I have 2 bashrc
>
> .bashrc~ and bashrc also bashrc~~

What happened to ~/.bashrc ?
The ones with the tildes on the ends are backups.

> (snip)
> . /home/s/OpenFOAM/OpenFOAM-1.4.1/.OpenFOAM-1.4.1/bashrc

That looks okay, but what file is it in?

> He is now rising from affluence to poverty.
> -- Mark Twain
> bash: > /home/s/OpenFOAM/OpenFOAM-1.4.1/.OpenFOAM-1.4.1/bashrc: No such file or directory

This is a clue. It can't find the file.

> s@s-desktop:~$
> /home/s/OpenFOAM/linux/OpenFOAM-1.4.1/bin/foamInstallationTest Executing
> /home/s/OpenFOAM/linux/OpenFOAM-1.4.1/bin/foamInstallationTest:

You've untarred the OpenFOAM software into the linux subdirectory of the OpenFOAM directory.
That's the wrong place.

Try this:

mv ~/OpenFOAM/linux/OpenFOAM-1.4.1 ~/OpenFOAM/

Maybe you'll have better results if you put it where it's supposed to be.

---

### Post by GijsW on 2008-06-22
Hi basilwatson,

The reason you now have .bashrc~ and .bashrc~~ is that you opened and closed them, with or without change. The ~ extension is just an indicator that something active happened to it. It is still the same file.

You can set the environment variable by first opening the ".bashrc" file in a text editor, e.g. ```
gedit .bashrc &
``` and then add the line ```
. $HOME/OpenFOAM/OpenFOAM-1.4.1/.OpenFOAM-1.4.1/bashrc
``` (don't forget the dot at the start). Then save and close the text editor and the terminal.

The "foamInstallationTest" quite often gives some depressing results. For me it is easier to try and run a small case, such as the lid-driven cavity case called "cavity". It's convenient to first make some kind of working directory for all your cases in the "OpenFOAM" directory by ```
mkdir ~/OpenFOAM/run
``` Then, cd to the "run" directory and copy the case file there by ```
cp -r ~/OpenFOAM/OpenFOAM-1.4.1/tutorials/icoFoam/cavity .
```
In the "run" directory generate the mesh by ```
blockMesh . cavity
``` and run the case by ```
icoFoam . cavity
``` You can view the result in ParaView by ```
paraFoam . cavity
``` In ParaView select the latest time step and click the green "accept" button.
Hopefully this is of any help. If not, just let me know.

Cheers, GijsW

---

### Post by mgz1985 on 2008-07-16
i am having a problem with running "blockmesh . cavity" i get an error command not found. 

while installing i get the following for foamSystemCheck and foamInstallationTest 

Checking basic system...
-----------------------------------------------------------------------
Shell:               bash
Host:                Techn-028
OS:                  Linux version 2.6.24-19-generic
User:                frpelikan


Checking networking...
-----------------------------------------------------------------------
Ping_Techn-028:      Successful
Ping_localHost:      Successful
Test_rsh:            Unsuccessful, connection refused*
**Test_ssh:            Unsuccessful, connection refused***
FATALERROR: No remote shell available.
            FoamX requires passwordless 
            'ssh' and/or 'rsh' to the current host.
            Contact your system administrator if you intend 
            to run FoamX.



System check: FAIL
==================
Your system is not currently compatible with Foam installation 
requirements. Review the error messages and consult the documentation
for further instructions.

frpelikan@Techn-028:~/OpenFOAM/OpenFOAM-1.4/mayank$ foamInstallationTest
Executing /home/frpelikan/OpenFOAM/OpenFOAM-1.4/bin/foamInstallationTest:


Checking basic setup...
-------------------------------------------------------------------------------
Shell:              bash
Host:               Techn-028
OS:                 Linux version 2.6.24-19-generic
User:               frpelikan
User_config:        /home/frpelikan/.bashrc
Foam_config:        /home/frpelikan/.OpenFOAM-1.4/bashrc sourced correctly.

FATAL ERROR Foam install directory not set.

Set correct path to installation 'WM_PROJECT_INST_DIR' in /home/frpelikan/.foam2.3/bashrc
-------------------------------------------------------------------------------


Checking main FOAM env variables...
-------------------------------------------------------------------------------
Environment_variable Set_to_file_or_directory                Valid      Crit
-------------------------------------------------------------------------------
$WM_PROJECT_INST_DIR --------- env variable not set ---------            yes
$WM_PROJECT_USER_DIR --------- env variable not set ---------            no
$FOAM_JOB_DIR        --------- env variable not set ---------            yes
-------------------------------------------------------------------------------


Checking the FOAM env variables set on the PATH...
-------------------------------------------------------------------------------
Environment_variable Set_to_file_or_directory                Valid Path Crit
-------------------------------------------------------------------------------
$WM_PROJECT_DIR      --------- env variable not set ---------            yes

$FOAM_USER_APPBIN    --------- env variable not set ---------            no
$FOAM_APPBIN         --------- env variable not set ---------            yes
$WM_DIR              --------- env variable not set ---------            yes
$FOAMX_PATH          --------- env variable not set ---------            yes
$CEI_HOME            --------- env variable not set ---------            no

$JAVA_PATH           --------- env variable not set ---------            no
$MICO_ARCH_PATH      --------- env variable not set ---------            yes
$LAM_ARCH_PATH       --------- env variable not set ---------            yes
$MPICH_ARCH_PATH     --------- env variable not set ---------            no
-------------------------------------------------------------------------------


Checking the FOAM env variables set on the LD_LIBRARY_PATH...
-------------------------------------------------------------------------------
Environment_variable Set_to_file_or_directory                Valid Path Crit
-------------------------------------------------------------------------------
$FOAM_LIBBIN         --------- env variable not set ---------            yes
$FOAM_USER_LIBBIN    --------- env variable not set ---------            no
$LAM_ARCH_PATH       --------- env variable not set ---------            yes
-------------------------------------------------------------------------------


Software versions
-------------------------------------------------------------------------------
Software Version   Location 
-------------------------------------------------------------------------------
gcc      4.2.3    
WARNING:  Conflicting installations:
          foam settings: /bin/gcc
          current path : /usr/bin/gcc
          CRITICAL ERROR

java     *** not installed ***

[B]gzip     1.3.12    /bin/gzip                                                
tar      1.3.12    /bin/tar                                                 
icoFoam  *** not installed ***
          CRITICAL ERROR[/B]

-------------------------------------------------------------------------------


Checking file/directory permissions...
-------------------------------------------------------------------------------
File/directory                                    Set  Reqd Crit
-------------------------------------------------------------------------------


Checking networking...
-------------------------------------------------------------------------------
Action                   Result                                       Crit
-------------------------------------------------------------------------------
Pinging_Techn-028        Successful                                   yes 
Pinging_localHost        Successful                                   yes 
Test_rsh:                Unsuccessful_connection_refused*             yes
**Test_ssh:                Unsuccessful_connection_refused* **            yes
FATAL ERROR: No remote shell available.
             Foam1.4 enviroment requires either ssh and/or rsh.
             Contact your system administrator.


-------------------------------------------------------------------------------

**The system test has evoked 1 fatal error(s).**

The foam installation contains 2 critical error(s).

Review the output for warning messages and consult 
the installation guide for trouble shooting.

frpelikan@Techn-028:~/OpenFOAM/OpenFOAM-1.4/mayank$ 
frpelikan@Techn-028:~/OpenFOAM/OpenFOAM-1.4/mayank$ 
i have highlighted the places where i think the error could be......

---

### Post by MACHINEaddict on 2008-07-21
I've been having problems with my OpenFOAM 1.5 install.
In step 7 of the readme I try to execute the buildParaView3.3-cvs command and get a long string of errors:

Building ParaView3.3-cvs
    MPI support    : OFF
    Python support : OFF
    MESA support   : OFF
    Source         : /home/dan/OpenFOAM/ThirdParty/ParaView3.3-cvs
    Target         : /home/dan/OpenFOAM/ThirdParty/ParaView3.3-cvs/platforms/linuxGcc
-- Check for working C compiler: /home/dan/OpenFOAM/ThirdParty/gcc-4.3.1/platforms/linux/bin/gcc
-- Check for working C compiler: /home/dan/OpenFOAM/ThirdParty/gcc-4.3.1/platforms/linux/bin/gcc -- broken
CMake Error: The C compiler "/home/dan/OpenFOAM/ThirdParty/gcc-4.3.1/platforms/linux/bin/gcc" is not able to compile a simple test program.
It fails with the following output:
 /usr/bin/make -f CMakeFiles/cmTryCompileExec.dir/build.make CMakeFiles/cmTryCompileExec.dir/build
make[1]: Entering directory `/home/dan/OpenFOAM/ThirdParty/ParaView3.3-cvs/platforms/linuxGcc/CMakeFiles/CMakeTmp'
/home/dan/OpenFOAM/ThirdParty/cmake-2.4.6/platforms/linux/bin/cmake -E cmake_progress_report /home/dan/OpenFOAM/ThirdParty/ParaView3.3-cvs/platforms/linuxGcc/CMakeFiles/CMakeTmp/CMakeFiles 1
Building C object CMakeFiles/cmTryCompileExec.dir/testCCompiler.o
/home/dan/OpenFOAM/ThirdParty/gcc-4.3.1/platforms/linux/bin/gcc   -o CMakeFiles/cmTryCompileExec.dir/testCCompiler.o   -c /home/dan/OpenFOAM/ThirdParty/ParaView3.3-cvs/platforms/linuxGcc/CMakeFiles/CMakeTmp/testCCompiler.c
/home/dan/OpenFOAM/ThirdParty/gcc-4.3.1/platforms/linux/bin/../libexec/gcc/i686-pc-linux-gnu/4.3.1/cc1: error while loading shared libraries: libmpfr.so.1: cannot open shared object file: No such file or directory
make[1]: *** [CMakeFiles/cmTryCompileExec.dir/testCCompiler.o] Error 1
make[1]: Leaving directory `/home/dan/OpenFOAM/ThirdParty/ParaView3.3-cvs/platforms/linuxGcc/CMakeFiles/CMakeTmp'
make: *** [cmTryCompileExec/fast] Error 2


CMake will not be able to correctly generate this project.
-- Configuring done
make: *** No targets specified and no makefile found.  Stop.
done

I'm new to linux, so i'm having trouble figuring out what to do.  The result of this error is that i'm unable to Post-Process any of my data and i'm not exactly in the mood to try to read CFD output directly.  If anybody knows how to convert the output so that another program can display it that would be a great short term fix, but ultimately i'd like to get this thing flying right.
Thanks!

---

### Post by disturbedsaint on 2008-07-22
The error messages are a little chaotic, but it says in this line
> /home/dan/OpenFOAM/ThirdParty/gcc-4.3.1/platforms/linux/bin/../libexec/gcc/i686-pc-linux-gnu/4.3.1/cc1: error while loading shared libraries: libmpfr.so.1: cannot open shared object file: No such file or directory

It needs libmpfr.so.1, if you want to know which package supplies this file just do a search at packages.ubuntu.com (under search contents of a package).
[http://packages.ubuntu.com/search?searchon=contents&keywords=libmpfr.so.1&mode=exactfilename&suite=hardy&arch=any](http://packages.ubuntu.com/search?searchon=contents&keywords=libmpfr.so.1&mode=exactfilename&suite=hardy&arch=any)
It is provided by libmpfr1ldbl

so install that

```
sudo apt-get install libmpfr1ldbl
```

You'll need QT4-dev as well

```
sudo apt-get install libqt4-dev
```

---

### Post by 4merflu on 2008-09-05
I have similar problems on ubuntu ( see below). Any idea why I cannot link gcc to either system or Open Foam. I have tried to set it in settting.sh.
Cheers!

Third party software
-------------------------------------------------------------------------------
Software Version   Location 
-------------------------------------------------------------------------------
WARNING: gcc version does not match gcc supplied with this release of OpenFOAM
         Supplied version: 4.3.1
         User version    : 4.2.3
         Minimum required: 4.2.0

gcc      4.2.3    
WARNING:  Conflicting installations:
          OpenFOAM settings        : /home/robert/OpenFOAM/ThirdParty/gcc-4.3.1/platforms/linux/bin/gcc
          current path             : /usr/bin/gcc
          CRITICAL ERROR

gzip     1.3.12    /bin/gzip                                                
tar      1.19      /bin/tar                                                 
icoFoam           
WARNING:  Conflicting installations:
          OpenFOAM settings        : /home/robert/OpenFOAM/OpenFOAM-1.5/applications/bin/linuxGccDPOpt/icoFoam
          current path             : 
          CRITICAL ERROR

-------------------------------------------------------------------------------


Checking networking...
-------------------------------------------------------------------------------
Action                   Result                                       Crit
-------------------------------------------------------------------------------
Pinging_robertubuntu     Successful                                   yes 
Pinging_localHost        Successful                                   yes 
Test_rsh:                Unsuccessful_connection_refused*             yes
Test_ssh:                Unsuccessful_connection_refused*             yes
FATAL ERROR: No remote shell available.
             OpenFOAM 1.5 enviroment requires either ssh and/or rsh.
             Contact your system administrator.


-------------------------------------------------------------------------------

The system test has evoked 1 fatal error(s).

The foam installation contains 2 critical error(s).

Review the output for warning messages and consult 
the installation guide for trouble shooting.

done.

---

### Post by GijsW on 2008-11-08
Hi MACHINEaddict and 4merflu,

In [this]("http://openfoam.cfd-online.com/forum/messages/1/8918.html?1222736035") (click "this")thread of the  [OpenFOAM Message board]("http://openfoam.cfd-online.com/cgi-bin/forum/discus.cgi") (click "Message board") an enthusiastic OpenFOAM user has posted an install script for Debian distributions:


Try it, it may solve your install problems. :D

---

