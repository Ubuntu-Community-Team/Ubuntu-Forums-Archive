---
title: "Matlab cannot find JRE in 9.04"
date: 2009-06-22
forum: Education &amp; Science
---

### Post by TAFKARS on 2009-06-22
Hi all

Attempting to install matlab in 9.04, but fails when it tries to locate the java runtime environment. Weird, as it manages to get most of the way through until it fails when attempting to initialise the activation process.

I have the most recent version of JRE installed on my machine, and this was done through synaptic.

Any help would be great!

---

### Post by spinoza666 on 2009-06-22
I have no experience with installing matlab, but this has worked for me with regards to similar java issues in the past, so might be of interest.

Make sure you have sun-java6-jre installed, and issue this command:

sudo update-alternatives --config java

Choose the sun java jre option, if not already set. You are now choosing wich java version your system should be running.

Try and install matlab.

Cheers:)

---

### Post by TAFKARS on 2009-06-22
Thank-you for the reply, spinoza, but unfortunately this does not work. The complete error message is below (apologies for the length of this):


Extracting ftp files . . . [please wait]
Extracting matlab.common
Extracting matlab.glnx86
Extracting tbx.signal.common
Extracting tbx.signal.glnx86
Extracting tbx.images.common
Extracting tbx.images.glnx86
Finished extracting ftp files.
Starting installer ...
---------------------------------------------------------------------------
Error: Cannot locate Java Runtime Environment (JRE).
The directory /usr/share/matlab2008b/sys/java/jre/glnxa64/jre does not exist.
---------------------------------------------------------------------------
me@-laptop:~/Desktop/mathworks_downloads/R2008b/unix$ matlab
---------------------------------------------------------------------------
Warning: Cannot locate Java Runtime Environment (JRE) . . .
 
         1. Either a correct JRE was not available for redistribution when
            this release was shipped, in which case you should refer to the
            Release Notes for additional information about how to get it.
 
         2. Or you have tried to use the MATLAB_JAVA environment variable
            to specify an alternate JRE, but MATLAB cannot find it.  Please
            run 'matlab -n' to determine what value you are using for
            MATLAB_JAVA and fix accordingly.
---------------------------------------------------------------------------

    matlab: No MATLAB bin directory for this machine architecture.

           ARCH = glnxa64

me@laptop:~/Desktop/mathworks_downloads/R2008b/unix$ matlab -n
------------------------------------------------------------------------
->      (.matlab7rc.sh) sourced from directory (DIR = $MATLAB/bin)
->      DIR = /usr/share/matlab2008b/bin
------------------------------------------------------------------------
        a = argument  e = environment  r = rcfile  s = script
------------------------------------------------------------------------
->  r   MATLAB              = /usr/share/matlab2008b
->      LM_LICENSE_FILE     = (variable not defined)
->      MLM_LICENSE_FILE    = (variable not defined)
->  s   AUTOMOUNT_MAP       = 
->  e   DISPLAY             = :0.0
->  r   ARCH                = glnxa64
->  s   TOOLBOX             = /usr/share/matlab2008b/toolbox
->  r   XAPPLRESDIR         = /usr/share/matlab2008b/X11/app-defaults
->  r   XKEYSYMDB           = /usr/share/matlab2008b/X11/app-defaults/XKeysymDB
->  e   MAX_OPEN_FILES      = 1024
->  s   _JVM_THREADS_TYPE   = 
->  e   MATLAB_JAVA         = 
->  s   MATLAB_MEM_MGR      = 
->  s   MATLAB_DEBUG        = 
->  s   LD_LIBRARY_PATH     = /usr/share/matlab2008b/sys/os/glnxa64:/usr/share/m
atlab2008b/bin/glnxa64:/usr/share/matlab2008b/extern/lib/glnxa64:/lib/amd64/nati
ve_threads:/lib/amd64
->  a   arglist             = 
->  e   SHELL               = /bin/bash
->  e   PATH                = /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:
/sbin:/bin:/usr/games
 
---------------------------------------------------------------------------
Warning: Cannot locate Java Runtime Environment (JRE) . . .
 
         1. Either a correct JRE was not available for redistribution when
            this release was shipped, in which case you should refer to the
            Release Notes for additional information about how to get it.
 
         2. Or you have tried to use the MATLAB_JAVA environment variable
            to specify an alternate JRE, but MATLAB cannot find it.  Check
            the value of MATLAB_JAVA above and fix accordingly.
---------------------------------------------------------------------------
 
->  s   MATLABPATH          = (initial version)
	/usr/share/matlab2008b/toolbox/local
 
 
->      $MATLAB/toolbox/local/pathdef.m -
|-----------------------------------------------------------------------
| function p = pathdef
| %PATHDEF Search path defaults.
| %   PATHDEF returns a string that can be used as input to MATLABPATH
| %   in order to set the path.
| 
|   
| %   Copyright 1984-2007 The MathWorks, Inc.
| %   $Revision: 1.4.2.2 $ $Date: 2007/06/07 14:45:14 $
| 
| 
| % DO NOT MODIFY THIS FILE.  IT IS AN AUTOGENERATED FILE.  
| % EDITING MAY CAUSE THE FILE TO BECOME UNREADABLE TO 
| % THE PATHTOOL AND THE INSTALLER.
| 
| p = [...
| %%% BEGIN ENTRIES %%%
| matlabroot,'/toolbox/matlab/general;', ...
| matlabroot,'/toolbox/matlab/ops;', ...
| matlabroot,'/toolbox/matlab/lang;', ...
| matlabroot,'/toolbox/matlab/elmat;', ...
| matlabroot,'/toolbox/matlab/randfun;', ...
| matlabroot,'/toolbox/matlab/elfun;', ...
| matlabroot,'/toolbox/matlab/specfun;', ...
| matlabroot,'/toolbox/matlab/matfun;', ...
| matlabroot,'/toolbox/matlab/datafun;', ...
| matlabroot,'/toolbox/matlab/polyfun;', ...
| matlabroot,'/toolbox/matlab/funfun;', ...
| matlabroot,'/toolbox/matlab/sparfun;', ...
| matlabroot,'/toolbox/matlab/scribe;', ...
| matlabroot,'/toolbox/matlab/graph2d;', ...
| matlabroot,'/toolbox/matlab/graph3d;', ...
| matlabroot,'/toolbox/matlab/specgraph;', ...
| matlabroot,'/toolbox/matlab/graphics;', ...
| matlabroot,'/toolbox/matlab/uitools;', ...
| matlabroot,'/toolbox/matlab/strfun;', ...
| matlabroot,'/toolbox/matlab/imagesci;', ...
| matlabroot,'/toolbox/matlab/iofun;', ...
| matlabroot,'/toolbox/matlab/audiovideo;', ...
| matlabroot,'/toolbox/matlab/timefun;', ...
| matlabroot,'/toolbox/matlab/datatypes;', ...
| matlabroot,'/toolbox/matlab/verctrl;', ...
| matlabroot,'/toolbox/matlab/codetools;', ...
| matlabroot,'/toolbox/matlab/helptools;', ...
| matlabroot,'/toolbox/matlab/demos;', ...
| matlabroot,'/toolbox/matlab/timeseries;', ...
| matlabroot,'/toolbox/matlab/hds;', ...
| matlabroot,'/toolbox/matlab/guide;', ...
| matlabroot,'/toolbox/matlab/plottools;', ...
| matlabroot,'/toolbox/local;', ...
| matlabroot,'/toolbox/shared/controllib;', ...
| matlabroot,'/toolbox/shared/dastudio;', ...
| matlabroot,'/toolbox/matlab/datamanager;', ...
| matlabroot,'/toolbox/images/colorspaces;', ...
| matlabroot,'/toolbox/images/images;', ...
| matlabroot,'/toolbox/images/imdemos;', ...
| matlabroot,'/toolbox/images/imuitools;', ...
| matlabroot,'/toolbox/images/iptformats;', ...
| matlabroot,'/toolbox/images/iptutils;', ...
| matlabroot,'/toolbox/shared/imageslib;', ...
| matlabroot,'/toolbox/shared/spcuilib;', ...
| matlabroot,'/toolbox/signal/signal;', ...
| matlabroot,'/toolbox/signal/sigtools;', ...
| matlabroot,'/toolbox/signal/sptoolgui;', ...
| matlabroot,'/toolbox/signal/sigdemos;', ...
| matlabroot,'/toolbox/shared/siglib;', ...
| %%% END ENTRIES %%%
|      ...
| ];
| 
| p = [userpath,p];
|-----------------------------------------------------------------------
------------------------------------------------------------------------

---

### Post by TAFKARS on 2009-06-23
This problem has now been resolved, please see below.

[http://ubuntuforums.org/showthread.php?t=1194064](http://ubuntuforums.org/showthread.php?t=1194064)

---

### Post by Sef on 2009-06-23
Locked. [Duplicate Post]("http://ubuntuforums.org/showthread.php?t=1194064").

---

