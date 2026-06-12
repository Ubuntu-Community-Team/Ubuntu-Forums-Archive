---
title: "OpenFOAM-1.4.1 on ubuntu 7.10"
date: 2008-03-17
forum: Education &amp; Science
---

### Post by usbqw on 2008-03-17
Hi guys.

I'm very new to ubuntu and now I have to install OpenFOAM-1.4.1 for my work.

However I got the following errors :

> idefix@idefix-laptop:~/OpenFOAM/OpenFOAM-1.4.1/bin$ foamInstallationTest 
Executing /home/idefix/OpenFOAM/OpenFOAM-1.4.1/bin/foamInstallationTest:


Checking basic setup...
-------------------------------------------------------------------------------
Shell:              bash
Host:               idefix-laptop
OS:                 Linux version 2.6.22-14-generic
User:               idefix
User_config:        /home/idefix/.bashrc
Foam_config:        /home/idefix/.OpenFOAM-1.4.1/bashrc sourced correctly.

FATAL ERROR Foam install directory not set.

Set correct path to installation 'WM_PROJECT_INST_DIR' in /home/idefix/.foam2.3/bashrc
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

java     1.5.0
libgcj)    
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
Pinging_idefix-laptop    Successful                                   yes 
Pinging_localHost        Successful                                   yes 
Test_rsh:                Unsuccessful_connection_refused*             yes
Test_ssh:                Successful                                   yes
(*) Only one of rsh or ssh is required by the Foam enviroment.

-------------------------------------------------------------------------------

Base configuration ok.

The foam installation contains 2 critical error(s).

Review the output for warning messages and consult 
the installation guide for trouble shooting.


I've done everything just as explained here:
[https://help.ubuntu.com/community/OpenFOAM]("https://help.ubuntu.com/community/OpenFOAM")

How could I fix this problem?
Regards
George

---

### Post by pradeep_345 on 2008-03-18
[http://ubuntuforums.org/showthread.php?t=156298](http://ubuntuforums.org/showthread.php?t=156298) this may be of some help

---

### Post by usbqw on 2008-03-18
Everything is clear now!

I fixed these errors by changing the rights of the OpenFOAM folder in ~/.

so just: ```
sudo chmod 777 -R OpenFOAM/
```

Hope this will be helpful for the other newbies in linux.

---

### Post by basilwatson on 2008-04-07
me to 
confused ,  followed the wiki 
While I can follow my way around ubuntu ( linux ) ,,,as in I can use the basic command line 

I am not a programmer . heres the error message I get when I run foam install check ;

Checking basic setup...
-------------------------------------------------------------------------------
Shell:              bash
Host:               s-desktop
OS:                 Linux version 2.6.22-14-generic
User:               root
User_config:        /root/.bashrc
Foam_config:        /root/.OpenFOAM-1.4.1/bashrc sourced correctly.

FATAL ERROR Foam install directory not set.

Set correct path to installation 'WM_PROJECT_INST_DIR' in /root/.foam2.3/bashrc
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
Test_ssh:                Unsuccessful_connection_refused*             yes
FATAL ERROR: No remote shell available.
             Foam1.4.1 enviroment requires either ssh and/or rsh.
             Contact your system administrator.


-------------------------------------------------------------------------------

The system test has evoked 1 fatal error(s).

The foam installation contains 2 critical error(s).

Review the output for warning messages and consult 
the installation guide for trouble shooting.

root@s-desktop:/home/s/OpenFOAM/linux/OpenFOAM-1.4.1# gedit ~/.bashrc &
[1] 19328
root@s-desktop:/home/s/OpenFOAM/linux/OpenFOAM-1.4.1# 




IS there a deb file !!!! 

I have the live cd from CAElinux , but I much prefer Ubuntu , or a raft of reason 


Can someone point me in the right direction 

btw , i am using a pentiiom 1.7 , 1 gig of ram and a nvidia gforce 520 
graphics card 


thank in advance 

Stephen 
:eek:

---

### Post by basilwatson on 2008-04-07
got a little further by installing ssh 

Stephen

---

