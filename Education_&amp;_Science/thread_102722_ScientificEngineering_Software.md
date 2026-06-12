---
title: "Scientific/Engineering Software?"
date: 2005-12-12
forum: Education &amp; Science
---

### Post by jmooney on 2005-12-12
Just found out about Code-Aster and Salome.  Has anyone successfully installed this on an Ubuntu box?  Anybody think they can make a .dpkg?

While I'm at it, perhaps I should open the thread for other suggestions for scientific/engineering software?

---

### Post by ekarni on 2005-12-12
Obviously depends on what flavor of science/engineering you're doing ;) (I'm an aero eng. grad student).  Most of what I've been doing lately is working with F77 programs for school, so I use Kate to edit source and g77 to compile.  Octave is nice to have laying around as a matlab surrogate.  Labplot looks like an ok plotting package, but I haven't really played with it.  Likewise, QCad looks like a decent 2D cad package, but again I haven't used it much.  Looking forward to see what else anyone has found!

---

### Post by parktownprawn on 2005-12-12
If you know about good Scientific/Engineering software you can add it to the wiki

[https://wiki.ubuntu.com/UbuntuScientists](https://wiki.ubuntu.com/UbuntuScientists)

---

### Post by blair on 2005-12-12
I'm not familiar with many specific packages, but there are whole distros devoted to mathematical packages. Check this out:

[http://www.livecdlist.com/](http://www.livecdlist.com/)

Select the "LiveCDs with a function of..." drop down list to see distros focused on different subjects.

---

### Post by jmooney on 2005-12-13
[QUOTE=ekarni]Obviously depends on what flavor of science/engineering you're doing ;) (I'm an aero eng. grad student).  Most of what I've been doing lately is working with F77 programs for school, so I use Kate to edit source and g77 to compile.  Octave is nice to have laying around as a matlab surrogate.  Labplot looks like an ok plotting package, but I haven't really played with it.  Likewise, QCad looks like a decent 2D cad package, but again I haven't used it much.  Looking forward to see what else anyone has found![/QUOTE]

Well, I'm and aero engineer and I use Octave routinely, usually as an inferior session inside of XEmacs/Emacs.  That's a great little math package.

F77....wow....I used that (through VI on a VAX system) back when I was an undergrad about {mumble mumble} years ago.

amazing.

---

### Post by Roobert on 2005-12-13
For open sourced Geographical Information System, the king, GRASS GIS:

[http://grass.itc.it/]("http://grass.itc.it/")

Used in many government and private sector companies worldwide for a multitude of scientific applications and analysis.

---

### Post by ziad on 2005-12-30
my 2 cents:

fluid dynamicist with lots of CFD. Lately I took a liking to OpenFoam which you can find at [www.openfoam.org](www.openfoam.org)

it's state of the art and in fact more advanced than several leading proprietary CFD codes out there, not pointing any fingers... ;) it also has several very interesting solvers in it. installs easily as the provided binaries are fully compatible with ubuntu.

jmooney,

I saw your thread at the salome website. I am trying to install salome as well but haven't succeeded yet. If you want a decent FEA solver try as well Calculix. I have aster installed. Did it the easy way by just installing the binaries :) no hurdles there... I'll keep you posted with the salome thing. Hopefully it should be fixed in a few days.

Z.

---

### Post by jmb365 on 2006-03-28
Hi,

I have installed Code_Aster 8.2.0-4 in Breezy (by compiling from full sources) , with little or no issues.  

However, my attempts at installing Salome-2.2.8 have been unsuccessful.  I was able install both on a RH FC3 machine successfully.  Has anybody accomplished installing Salome in Breezy?  If so could you post some notes (or lessons learnt) here, please?

Thanks
JMB

[QUOTE=ziad]my 2 cents:

fluid dynamicist with lots of CFD. Lately I took a liking to OpenFoam which you can find at [www.openfoam.org](www.openfoam.org)

it's state of the art and in fact more advanced than several leading proprietary CFD codes out there, not pointing any fingers... ;) it also has several very interesting solvers in it. installs easily as the provided binaries are fully compatible with ubuntu.

jmooney,

I saw your thread at the salome website. I am trying to install salome as well but haven't succeeded yet. If you want a decent FEA solver try as well Calculix. I have aster installed. Did it the easy way by just installing the binaries :) no hurdles there... I'll keep you posted with the salome thing. Hopefully it should be fixed in a few days.

Z.[/QUOTE]

---

### Post by jmb365 on 2006-03-28
Hi,

I have installed Code_Aster 8.2.0-4 in Breezy (by compiling from full sources) , with little or no issues.  It was amazingly simple.  If you want some notes on how I did it, here they are:

# su -          
(I am not sure that it will work as any ordinary user, but you are welcome to try)
# mkdir ~/somedirectoy
# cd ~/somedirectory
# wget -nd [http://www.code-aster.org/FICHIERS/aster-full-src-8.2.0-4.tar.gz](http://www.code-aster.org/FICHIERS/aster-full-src-8.2.0-4.tar.gz)	
# gunzip -cd /home/LinuxDownLoads/FEA/aster-full-src-8.2.0-4.tar.gz | tar -xvf -
# cd aster-src-8.2.0
# python setup.py test
# apt-get install nedit flex bison python-dev lapack3-dev (along with  recommended packages)
# python setup.py install    (Runs for a long time, be patient!)
# cd /opt/aster/STA8.2
# /opt/aster/ASTK/ASTK_SERV/bin/as_run forma01a.export	(Test the code)

Get the command files, etc. for code_aster from:
[http://www.code-aster.org/forum/download.php?f=11&file=helpers.tar.gz](http://www.code-aster.org/forum/download.php?f=11&file=helpers.tar.gz)
# cd /opt
# gunzip -cd /home/LinuxDownLoads/FEA/salome/helpers.tar.gz | tar -xvf -
/opt/helpers/CreateJob.py	
(Is the program to create a new ASTK job. It is the equivalent to clicking "New FE Analysis" icon mentioned in IntroductionTutorial1.pdf)
One may create a desktop shortcut pointing to this python script.  
The *.comm files mentioned in that tutorial are in /opt/helpers/Templates

ASTK: tool to set the analysis parameters; analysis directory, command and results files, amount of memory: 
# /opt/aster/ASTK/ASTK_CLIENT/bin/astk

EFICAS: very useful tool to write the command file: 
# /opt/aster/outils/eficas

All jobs are "PENDing" - click on the "Actualiser" Button to submit them! 
 Cannot see the error or output files via "nedit"
 Astk uses a remote display to edit / view in interactive mode the computation
 files. If you can not edit the error or output file maybe your system is not
 configured for it :
 
 in a console try 
# 	nedit -display localhost:0.0
If you don't see any nedit window : it means that your system is not
 configured to display remote windows. Try
# 	xhost +
if it still doesn't work you must edit the file : /etc/X11/gdm/gdm.conf and
set the option "disallowTCP" to "false". Then Reboot the PC
 
After you should be able to edit the output or error files.
"nedit -display localhost:0.0" now works, but not for ASTK :(
in case it doesn't work you can view the output file on your own : 
# 	less ~/flasheur/"job_name".o"job_number"    for output file
if you want to see it updated during the computation : 
# 	tail -f ~/flasheur/"job_name".o"job_number"

If jobs do not run via ASTK, the work around is:
~/flasheur/piston1.uXXXXX	(Execute this script manually)

-------------------------------------------------------------------------------------
NOTE: Please try these procedures at your own risk or on a test PC.  They worked for me, but may not (or even destroy data) for you!

However, my attempts at installing Salome-2.2.8 have been unsuccessful. I was able install both on a RH FC3 machine successfully.  Will be glad to hear the experience of others in this forum!

However as of now, there is a compatibilty problem between the HDF & MED libraries used in Salome v/s Code_Aster, such that result files written by Code_Aster (Ver  8.2.0-4) are unreadable in Salome (Ver 2.2.8)!  I have not overcome that problem yet.  My interim solution has been to run the Code-Aster solver in a CAELinux LiveCD enabled machine & transferring the result files into my RH FC3 machine.  Joel CUGNONI (author of CAELinux LiveCD, I believe) mentioned using the HFD & MED libraries of Code_Aster when recompiling Salome, but I have not figured that out yet.  Hopefully somebody from the Code_Aster forums can guide / help me with that.

Good Luck,
JMB


[QUOTE=jmooney]Just found out about Code-Aster and Salome.  Has anyone successfully installed this on an Ubuntu box?  Anybody think they can make a .dpkg?

While I'm at it, perhaps I should open the thread for other suggestions for scientific/engineering software?[/QUOTE]

---

### Post by cg_linux on 2006-08-31
Hello...
I need instructions to install and to run Fluent 6.2 in Ubuntu 6.06 for 64-bit(AMD Athlon).

---

### Post by jmb365 on 2006-08-31
> **jmooney said:**
> Just found out about Code-Aster and Salome.  Has anyone successfully installed this on an Ubuntu box?  Anybody think they can make a .dpkg?

While I'm at it, perhaps I should open the thread for other suggestions for scientific/engineering software?

Apart from my email in this forum about installing Code-Aster in Ubuntu Breezy, I have installed Salome as well in Breezy as well.  See "http://www.code-aster.org/forum/read.php?f=11&i=1765&t=1765" in the Code-Aster forum or search keyword "ubuntu" in the "Installation of Code-Aster" forum of the Code-Aster forums

Good Luck
JMB

---

### Post by proximityinfotech6 on 2010-07-06
# gunzip -cd /home/LinuxDownLoads/FEA/salome/helpers.tar.gz | tar -xvf -
/opt/helpers/CreateJob.py	
(Is the program to create a new ASTK job. It is the equivalent to  clicking "New FE Analysis" icon mentioned in IntroductionTutorial1.pdf)
One may create a desktop shortcut pointing to this python script.  
The *.comm files mentioned in that tutorial are in  /opt/helpers/Templates

ASTK: tool to set the analysis parameters; analysis directory, command  and results files, amount of memory: 
# /opt/aster/ASTK/ASTK_CLIENT/bin/astk

EFICAS: very useful tool to write the command file: 
# /opt/aster/outils/eficas
______________________________________________________________
[ Ben 10 Games ](http://www.kingofgames.net/ben-10-games)

---

