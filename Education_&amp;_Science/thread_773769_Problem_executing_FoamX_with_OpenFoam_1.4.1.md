---
title: "Problem executing FoamX with OpenFoam 1.4.1"
date: 2008-04-29
forum: Education &amp; Science
---

### Post by madad2005 on 2008-04-29
Hey, I'm getting this error message when trying to execute FoamX. My foamInstallationTest when fine with no errors. See below for what I got. Tell me if I'm wrong, but it seems to be a problem executing the java code due to some issue in the C library? 

Cheers,

Adriano

p.s. Btw, I'm new to ubuntu, but I like it a lot! PCLinuxOS was my favourite before, but this looks, feels, and works much better. God bless Free Software!

=====================================================

admin1234@admin1234-desktop:~/OpenFOAM/OpenFOAM-1.4.1/bin$ FoamX
Starting NameServer with inet:admin1234-desktop:1234 ...
Starting FoamX Host Browser with inet:admin1234-desktop:1234 ...
/*---------------------------------------------------------------------------*\
| =========                 |                                                 |
| \\      /  F ield         | OpenFOAM: The Open Source CFD Toolbox           |
|  \\    /   O peration     | Version:  1.4.1                                 |
|   \\  /    A nd           | Web:      [http://www.openfoam.org](http://www.openfoam.org)               |
|    \\/     M anipulation  |                                                 |
\*---------------------------------------------------------------------------*/

Exec   : FoamXHostBrowser 
Date   : Apr 29 2008
Time   : 08:33:11
Host   : admin1234-desktop
PID    : 14246
Root   : 
Case   : 
Nprocs : 1
HostBrowser running.....
Setting LANG to en_EN
Using jar /home/admin1234/OpenFOAM/OpenFOAM-1.4.1/applications/utilities/preProcessing/FoamX/lib/FoamX.jar
Using jar /home/admin1234/OpenFOAM/OpenFOAM-1.4.1/applications/utilities/preProcessing/FoamX/lib/jlfgr-1_0.jar

(.:14250): Gtk-WARNING **: Locale not supported by C library.
	Using the fallback 'C' locale.
Exception in thread "main" java.lang.ExceptionInInitializerError
   at java.lang.Class.initializeClass(libgcj.so.81)
   at java.lang.Class.initializeClass(libgcj.so.81)
   at java.lang.reflect.Method.invoke(libgcj.so.81)
   at javax.swing.UIDefaults.getUI(libgcj.so.81)
   at javax.swing.UIManager.getUI(libgcj.so.81)
   at javax.swing.JTree.updateUI(libgcj.so.81)
   at javax.swing.JTree.<init>(libgcj.so.81)
   at javax.swing.JTree.<init>(libgcj.so.81)
   at FoamX.CaseManagement.CaseBrowserPanel.initComponents(CaseBrowserPanel.java:1136)
   at FoamX.CaseManagement.CaseBrowserPanel.<init>(CaseBrowserPanel.java:133)
   at FoamX.CaseManagement.CaseManager.<init>(CaseManager.java:95)
   at FoamX.App.<init>(App.java:258)
   at FoamX.App.main(App.java:184)
Caused by: java.awt.IllegalComponentStateException: component java.awt.Label not showing
   at java.awt.Component.getLocationOnScreen(libgcj.so.81)
   at java.awt.event.MouseEvent.<init>(libgcj.so.81)
   at java.awt.event.MouseEvent.<init>(libgcj.so.81)
   at javax.swing.plaf.basic.BasicTreeUI.<clinit>(libgcj.so.81)
   at java.lang.Class.initializeClass(libgcj.so.81)
   ...12 more
Killed
runFoamXHB : cleanup
runFoamXHB: Killing name server nsd(pid 14242).
admin1234@admin1234-desktop:~/OpenFOAM/OpenFOAM-1.4.1/bin$

---

### Post by arkangel on 2008-04-29
Are you using the java  that comes with the OpenFoam distribution 
you have to set the java home  in 


../OpenFOAM/OpenFOAM-1.4.1/.bashrc

open the file and look for a "export  JAVA_HOME=/some_dir/java-1.4.something"   , see if it points to the  right directory , 

Personally I dont like FoamX ,  I prefer settign cases by hand ,  anyway I try once with java 1.5  so  first you have to look for where the java is  (/usr/lib/java ... or something )  , once located try by setting the JAVA_HOME in   "../OpenFOAM/OpenFOAM-1.4.1/.bashrc  "

and source again

---

### Post by madad2005 on 2008-04-29
Cheers for the reply.

Initially it had problems finding the java compiler that I installed under ~/OpenFoam/linux64 which did exist, but I got round that by editing the .bashrc file to point to /usr so as to find /usr/bin/java and /usr/bin/gcc. I was thinking this may be an issue since I'm using the 64-bit version.

I'll get into file editing by hand after I get through the tutorials. I'm an experienced CFD user (both commercial and research), and I know how fiddly these files can be at times if you don't know what you are doing. That's why I wanted to use FoamX first so as to understand OpenFoam's process first. Unfortunately, the tutorials use FoamX for case setup or am I wrong? Anyway, any other ideas on the issue?


Cheers,

Adriano

---

### Post by arkangel on 2008-04-29
and the output of foamInstallationTest is  with no warnings  and errors ?  can you post it ?
what about setting WM_64  in bashrc?

---

### Post by basilwatson on 2008-04-29
well I had the same problem 

but I tried to install a Cam file and my screen went south 
So I re installed 7;10 and the first thing I did was install open foam exaxtly how the read me said .

all ok 

so I can confirm it runs on 7.10 ( though FoamX , I am still not sure shos the blockmesh ?) 

if there is any part of the code you need to look at such as the .bashrc file . please ask ,,I can copy and paste 

Stephen

---

### Post by arkangel on 2008-04-29
OpenFoam  should work even if you have a mere console and Java installed (for FoamX  only),  the only thing I might think is not working is the java engine  openfoam uses an old 1.4.*  , but   just download another one and put it in /opt/ for example  

can you put  the output of 
%uname -a 

and 

upload your "../OpenFoam-1.4.1/.OpenFoam-1.4.1/.bashrc"  and "./OpenFoam-1.4.1/.baschrc" 

another stuff is the compiler  Ubuntu8.4  uses a 4.3,  while opemfoam works well with 4.2 , and there was a change on the libstdc++ (to support the new iso c++ std)  so It might be that your binaries were linked with the old libstdc++ and during run time  they load the new libstdc++ (whose interface  might be different, i need to read the documentation, idont know  ). I'll try  at home tonite

---

### Post by madad2005 on 2008-04-29
I already have the 64-bit option included in the .bashrc file. I had no errors at all in my foamInstallationTest. I'll upload it tonight. The first time I tried to run FoamX I was linking to the java binaries from the OpenFoam website. However, when I tried to run FoamX I was getting the error <directory path>/java : not found. However, the java binary did exist and the file path was correct (a quick copy and paste of the path reported in the error message confirmed this). I got avoided this error message by changing the file paths for the gcc and java compilers to /usr. That specific error stopped and foamInstallationTest reported no errors again. However, I now get the error reported above. Maybe it is a problem with the java installed in /usr ? If I remember correctly, the gcc compiler in ubuntu 8.04 is gcc-1.4.2, which is the same as supplied by OpenFoam. I'm not sure about the Java one. Maybe I'm missing some Java libraries. 

I'm at work at the moment so I can't do anymore debugging till I get home. I'll post the output of the foamInstallationTest too.

Cheers,

Adriano

p.s. Btw, sorry for the late reply, had a total f**ker of a day :-(. Who needs CFD!?! :-p I do appreciate your help.

---

### Post by madad2005 on 2008-04-29
Output from my foam installation test:

==========================================================


admin1234@admin1234-desktop:~$ foamInstallationTest 
Executing /home/admin1234/OpenFOAM/OpenFOAM-1.4.1/bin/foamInstallationTest:


Checking basic setup...
-------------------------------------------------------------------------------
Shell:              bash
Host:               admin1234-desktop
OS:                 Linux version 2.6.24-16-generic
User:               admin1234
User_config:        /home/admin1234/.bashrc
Foam_config:        /home/admin1234/.OpenFOAM-1.4.1/bashrc sourced correctly.
-------------------------------------------------------------------------------


Checking main FOAM env variables...
-------------------------------------------------------------------------------
Environment_variable Set_to_file_or_directory                Valid      Crit
-------------------------------------------------------------------------------
$WM_PROJECT_INST_DIR /home/admin1234/OpenFOAM                 yes       yes
$WM_PROJECT_USER_DIR /home/admin1234/OpenFOAM/admin1234-1.4.1  yes       no
$FOAM_JOB_DIR        /home/admin1234/OpenFOAM/jobControl      yes       yes
-------------------------------------------------------------------------------


Checking the FOAM env variables set on the PATH...
-------------------------------------------------------------------------------
Environment_variable Set_to_file_or_directory                Valid Path Crit
-------------------------------------------------------------------------------
$WM_PROJECT_DIR      /home/admin1234/OpenFOAM/OpenFOAM-1.4.1  yes  yes  yes

$FOAM_USER_APPBIN    ...4.1/applications/bin/linux64GccDPOpt  yes  yes  no
$FOAM_APPBIN         ...4.1/applications/bin/linux64GccDPOpt  yes  yes  yes
$WM_DIR              ...in1234/OpenFOAM/OpenFOAM-1.4.1/wmake  yes  yes  yes
$FOAMX_PATH          ...ations/utilities/preProcessing/FoamX  yes   no  yes
$CEI_HOME            /usr/local/ensight/CEI                   no        no

$JAVA_PATH           /usr                                     yes  yes  no
$MICO_ARCH_PATH      ...ico-2.3.12/platforms/linux64GccDPOpt  yes  yes  yes
$LAM_ARCH_PATH       .../lam-7.1.2/platforms/linux64GccDPOpt  yes  yes  yes
$MPICH_ARCH_PATH     --------- env variable not set ---------            no
-------------------------------------------------------------------------------


Checking the FOAM env variables set on the LD_LIBRARY_PATH...
-------------------------------------------------------------------------------
Environment_variable Set_to_file_or_directory                Valid Path Crit
-------------------------------------------------------------------------------
$FOAM_LIBBIN         ...M/OpenFOAM-1.4.1/lib/linux64GccDPOpt  yes  yes  yes
$FOAM_USER_LIBBIN    .../admin1234-1.4.1/lib/linux64GccDPOpt  yes  yes  no
$LAM_ARCH_PATH       .../lam-7.1.2/platforms/linux64GccDPOpt  yes  yes  yes
-------------------------------------------------------------------------------


Software versions
-------------------------------------------------------------------------------
Software Version   Location 
-------------------------------------------------------------------------------
gcc      4.2.3     /usr/bin/gcc                                             
java     1.5.0
libgcj)     /usr/bin/java                                            
gzip     1.3.12    /bin/gzip                                                
tar      1.3.12    /bin/tar                                                 
icoFoam            ...penFOAM-1.4.1/applications/bin/linux64GccDPOpt/icoFoam
-------------------------------------------------------------------------------


Checking file/directory permissions...
-------------------------------------------------------------------------------
File/directory                                    Set  Reqd Crit
-------------------------------------------------------------------------------


Checking networking...
-------------------------------------------------------------------------------
Action                   Result                                       Crit
-------------------------------------------------------------------------------
Pinging_admin1234-desktop Successful                                   yes 
Pinging_localHost        Successful                                   yes 
Test_rsh:                Unsuccessful_connection_refused*             yes
Test_ssh:                Successful                                   yes
(*) Only one of rsh or ssh is required by the Foam enviroment.

-------------------------------------------------------------------------------

Base configuration ok.

Critical systems ok.


admin1234@admin1234-desktop:~$

---

### Post by madad2005 on 2008-04-30
Ok, I installed then uninstalled a sound driver (then instlaled it again). OSS I think it was, last night, I now get this error message when trying to execute FoamX:

admin1234@admin1234-desktop:~/OpenFOAM$ FoamX
Starting NameServer with inet:admin1234-desktop:1234 ...
Starting FoamX Host Browser with inet:admin1234-desktop:1234 ...
FoamXHostBrowser: error while loading shared libraries: libPstream.so: cannot open shared object file: No such file or directory
runFoamXHB : cleanup
runFoamXHB: Killing name server nsd(pid 8558).
/home/admin1234/OpenFOAM/OpenFOAM-1.4.1/bin/FoamX: 1: 0: not found

Where can I download libPStream.so from? Could someone even e-mail me this file or should it be on the installation cd?

---

### Post by madad2005 on 2008-04-30
Ok, this file is actually in /OpenFoam/OpenFoam-1.4.1/lib/openmpi/ but for some reason libOpenFoam.so can't find it. I'll try and reinstall it all again tonight :-(.

---

### Post by arkangel on 2008-04-30
Ok  seems to be a problem  with your settings  , something is messed up 

first the sound driver, printer driver or the like has absolutely nothing to do  with OFoam.

LibStream.so is the OpenFOAM's communication library so , if you haven't cleaned  it is located where the rest of libraries are 

the best way to test is OF is working is 
-  take a look at this directory 
  "/home/admin1234/OpenFOAM/OpenFOAM-1.4.1/lib/linux64GccDPOpt/"

about the linux64GccDP...  I am not so sure because it changes with the architecture/compiler  combination (this is the one for 64 amd ?) 
inside you will see a lot of dynamic libraries  in a subdirectory mpi is libPstream.so  if you have them all is ok , if not  either you recompile all over gain or  download and do a fresh install 


- issue this command 
echo $LD_LIBRARY_PATH
and this env variable has to point to the directory  mentioned above  and 
/home/admin1234/OpenFOAM/linux64/gcc-4.2./lib  , and many other 

- then go to the tutorial /home/admin1234/OpenFOAM/OpenFoam1.4.1/tutorials/icoFoam

en icofoam  you will find a cavity directory

so just run ./Allrun   and must do something  see the log inside this directorie 

good luck :)

---

### Post by madad2005 on 2008-04-30
Cool! I'll give that a try at lunchtime today. If it fails, I'll do a reinstall again and retry! :-) Cheers for the help!

---

### Post by madad2005 on 2008-04-30
Ok, got it working!

The issue with libPstream.so is a bug, I believe. My foamInstallationTest has been fine every time. However, to turn on the LAM parallel processing code I had added WM_****="LAM" to the start of /OpenFoam/OpenFoam-1.4.1/.bashrc and /OpenFoam/OpenFoam-1.4.1/.OpenFoam-1.4.1/bashrc. When attempting to start FoamX I then got the libPstream.so error. Upon removing this shortcut from /OpenFoam/OpenFoam-1.4.1/.bashrc and replacing it with OPENMPI (which i don't think is important.. as long as you remove it), FoamX started up without a problem.

the initial problem I was having must be related to the order I installed the packages. I have deleted and reinstalled everything about 6 times now, but it is now officially working. The only issue now is that ParaView cannot find libtcl8.4.so. I'm going to install a separate paraview and see if i can get it to work that way. 

nonetheless, problem solved. I don't think ive been too clear in what I've written. If anyone needs further clarification, please ask. :-) 

Anyway, thanks for the help Arkangel. It is much appreciated! 

p.s. Btw, blockMesh works as well. Not got time to run the solver tonight, but ill be giving it a go tomorrow.

---

### Post by arkangel on 2008-05-02
by default  LibPstream is compiled against openmpi and not with lam  

can you post the ouput  of this 

"ldd libPstream.so"


Look  compiling paraview is a very tricky business 
[http://openfoamwiki.net/index.php/Howto_compile_OpenFOAM#Compiling_and_installing_ParaView](http://openfoamwiki.net/index.php/Howto_compile_OpenFOAM#Compiling_and_installing_ParaView)

but   try to be sure  if the environment is correct,   
-first  try to find out if libPstream is compiled against libmpi.so  of Openmpi  (with ldd)

-then you have to locate the libtcl8.4.so  that  most probably is located  inside the linux64/paraview/lib  or something 
(use  : cd ../linux64/paraview-vernum    ;  find  . -name libtcl8.4.so)  

See how the AddPath  and AddlibPath work in .bashrc  (which are equivalent to export PATH=bla..:$PATH and export LD_LIBRARY_PATH=bal...:%LD_LIBRARY_PATH ) 

   I dont know  why are you having so many troubles please  be sure you are donwloading the right binaries for the right arch/Platform  ..  


Hope it helps:)

---

### Post by madad2005 on 2008-05-03
I got Paraview to work as well. I copied that library file from a precompiled package into the version supplied with OpenFoam's ./lib directory and it works fine now! I'm a bit busy this morning, but I'll check library dependency f libPStream soon.

---

### Post by mgz1985 on 2008-07-17
frpelikan@Techn-028:~$ FoamX
Starting NameServer with inet:Techn-028:1234 ...
/home/frpelikan/OpenFOAM/OpenFOAM-1.4/bin/runFoamXHB: 130: nsd: not found


i get this error when i am trying to run FoamX.....i m just working in linux for the first time..it has been more than 2 weeks now since i m trying to install open foam on my system...and yes does it make a difference if neither of my **ssh or rsh **connection are successful..both of them are refusing connection.......please help me..it is desperate times here in my internship

---

