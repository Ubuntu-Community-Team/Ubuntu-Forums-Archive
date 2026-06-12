---
title: "How to install Scibuntu on 8.10?"
date: 2009-03-09
forum: General Help
---

### Post by shateredsoul on 2009-03-09
Has anyone installed Scibuntu on Ubuntu 8.10?

I tried to download the file, but it took forever so I clicked on the direct download link. I was then sent to a page with a bunch of text.. so I copied it to a text file. The file was changed to a script.. and I made it so it can run as a program.

I clicked, a window with the options "run, display, etc.." popped up. I clicked on run. Nothing happened. Any advice?

Has anyone else tried the recent versions? I've heard stories about it breaking Ubuntu.

---

### Post by shateredsoul on 2009-03-09
I finally downloaded it.. does any one know how to tell if this will break any of the programs in Ubuntu 8.10?  Here's the text in the document.

#!/bin/bash
# scibuntu - scientific extensions for Ubuntu 6.04 LTS
# by Urban Anjar
#    GUI code and inspiration mostly by Troels Kofoed Jacobsen
# Copyleft, all rights reversed
# Ver: 0.1          061023 - First version
# Ver: 0.2          061030 - More programs, deb-installation loop
# Ver: 0.21         061106 - qalculate-gtk added
# Ver: 0.3-testing  061109 - Allmost total rewrite,
#                            GUI, choice, lots of new programs
# Ver: 0.3-paraxe   061113 - Removed rkward and treeviewx (missing in dapper repository), 
#                            edited spelling error on tree-puzzle
#                            Changed phylo_win-installation according to scibuntu022-alpha
#                   061117   Above fixes by paraxe + improved logging + new license: GPL
#                            see urban.it.hik.se/scibuntu/COPYING
#                   061130   Added ACRODEB to install Acrobat Reader from the
#                            repository instead of downloading from Adobe.com.
#                   061130   Added JabRef and Sun Java
#                   061203   Fixed som typos. Close Synaptic and apt-get. Changed TRUE to FALSE so 
#                            users actively have to choose what to install.
#                   061204   Addet ipython, python-matplotlib and python-scipy.
# Ver 0.4-beta      061210   Celebrating the first Swede in space and all Nobel lauriates we now release our first beta version.
# Ver 0.41-beta     070605   Bug fix thanks to Gastón Paris

VER="0.41"
LOG=".scibuntu_log"
TEMPDIR="/tmp/scibuntu-install"

## DEB-packages to be installed

MATHDEB="qalculate-gtk grace octave gnuplot labplot r-base wxmaxima" 
PHYSDEB="celestia cernlib cernlib-base cernlib-core cernlib-core-dev cernlib-extras cernlib-montecarlo"
CHEMDEB="chemtool gromacs gromacs-doc rasmol pymol t-coffee openbabel"
BIODEB="ncbi-tools-x11 ncbi-tools-bin blast2 clustalw clustalx tree-puzzle" 
DEVDEB="emacs21 build-essential g77 gfortran gpc sharutils binutils sysutils bioperl python-biopython"
PUBDEB="tetex-base tetex-bin tetex-extra kile gs gv"
ACRODEB="acroread acroread-plugins mozilla-acroread"
SCIPYDEB="ipython python-scipy python-matplotlib"

function logtouch {
     DATE=`date +%y-%m-%d__%H_%M_%S`
     LOG=$LOG$DATE
     touch $LOG
}

function logstart {
     logtouch
     echo "DATE" >> $LOG
     date >> $LOG
     echo -e "\nSCIBUNTU VERSION">> $LOG
     echo $VER >> $LOG
     echo -e "\nUBUNTU VERSION" >>$LOG
     cat /etc/issue >>$LOG
     echo -e "\nCPU VERSION" >> $LOG
     cat /proc/cpuinfo >> $LOG
     echo -e "\nRAM MEMORY" >> $LOG
     free >> $LOG
     echo -e "\nDISK UTILISATION">>$LOG
     df >> $LOG
}

function logstop {
     echo "DATE" >> $LOG
     date >> $LOG
     echo -e "\nDISK UTILISATION">>$LOG
     df >> $LOG
}

function debinstall {
   for P in $PACKAGES; do
       #echo Installing $P
       apt-get install $P -qy | tee --append $LOG | zenity --progress --pulsate --auto-close --text "INSTALLING $P"
       #echo $P ready
   done
}

function phylowininstall {
#Installing non-ubuntu packages
#   echo "Installing phylo_win"
   mkdir $TEMPDIR
   cd $TEMPDIR
   wget [ftp://pbil.univ-lyon1.fr/pub/mol_phylogeny/phylo_win/phylo_winlinuxPC.tgz](ftp://pbil.univ-lyon1.fr/pub/mol_phylogeny/phylo_win/phylo_winlinuxPC.tgz) | zenity --progress --pulsate --auto-close --text "Downloading Phylo_win"
   tar -xvf phylo_winlinuxPC.tgz  | zenity --progress --pulsate --auto-close --text "Unpacking Phylo_win"
   rm phylo_winlinuxPC.tgz
   mkdir /usr/local/phylo_win
   mv phylo_win*  /usr/local/phylo_win
   mv protein.mase  /usr/local/phylo_win
   ln -s /usr/local/phylo_win/phylo_win /usr/local/bin
   cd -
   rm -rf $TEMPDIR
#   echo "phylo_win ready"
# TODO: Add phylo_win to program menu
}

function jabrefinstall {
   mkdir $TEMPDIR
   cd $TEMPDIR
   wget [http://heanet.dl.sourceforge.net/jabref/JabRef-2.1.jar](http://heanet.dl.sourceforge.net/jabref/JabRef-2.1.jar) | zenity --progress --pulsate --auto-close --text "Downloading JabRef"
   mkdir /usr/local/jabref
   mv JabRef* /usr/local/jabref
   ln -s /usr/local/jabref/JabRef-2.1.jar /usr/local/bin/jabref
# TODO: Add "java -jar /usr/local/bin/jabref" to program menu
   cd -
   rm -rf $TEMPDIR
}

function javainstall {
   xterm -T 'Installing Sun Java' -e 'apt-get install -qy sun-java5-jre;update-alternatives --set java /usr/lib/jvm/java-1.5.0-sun/jre/bin/java;echo -e "Press Enter to close this window";read x;exit'
}

#[http://kent.dl.sourceforge.net/sourceforge/salstat/salstat.20031022.tar.gz](http://kent.dl.sourceforge.net/sourceforge/salstat/salstat.20031022.tar.gz)

function acrobatinstall {
   #echo "Installing Adobe Reader"
   mkdir $TEMPDIR
   cd $TEMPDIR
   wget [http://ardownload.adobe.com/pub/adobe/reader/unix/7x/7.0.8/enu/AdobeReader_enu-7.0.8-1.i386.tar.gz|](http://ardownload.adobe.com/pub/adobe/reader/unix/7x/7.0.8/enu/AdobeReader_enu-7.0.8-1.i386.tar.gz|) zenity --progress --pulsate --auto-close --text "Downloading AcrobatReader"
   tar -xvf AdobeReader*.tar.gz | zenity --progress --pulsate --auto-close --text "Unpacking AcrobatReader"
   cd AdobeReader
   xterm -e ./INSTALL
   cd -
   rm -rf $TEMPDIR
   #echo "AdobeReader ready"
}

function choose {
       RET=`zenity --list --checklist --width=400 --height=400 \
               --title "Choose applications" \
               --column="" --column $"Function" --column $"Description" \
               FALSE    $"math" $"Mathematics, statistics and plotting"\
               FALSE    $"phys" $"Physics applications"\
               FALSE    $"chem" $"Chemistry applications"\
               FALSE    $"bio" $"Bioinformatics applications"\
               FALSE    $"devel" $"Development and console tools"\
               FALSE    $"publ" $"Scientific publishing"\
               FALSE    $"jabref" $"Reference Manager (with Sun Java)"\
               FALSE    $"acroread" $"Adobe Reader (unfree)"\
               FALSE    $"scipy" $"Python scientific modules (scipy) and ipython interactive shell"`

       if echo "$RET" | grep $"math"; then
               math
       fi
       if echo "$RET" | grep $"phys"; then
               phys
       fi
       if echo "$RET" | grep $"chem"; then
               chem
       fi
       if echo "$RET" | grep $"bio"; then
               bio
       fi
       if echo "$RET" | grep $"devel"; then
               devel
       fi
       if echo "$RET" | grep $"publ"; then
               publ
       fi
       if echo "$RET" | grep $"jabref"; then
               jabref
       fi
       if echo "$RET" | grep $"acroread"; then
#              acrobatinstall
               acroread
       fi
}

function math {
   PACKAGES=$MATHDEB
   debinstall
}

function phys {
   PACKAGES=$PHYSDEB
   debinstall
}

function chem {
   PACKAGES=$CHEMDEB
   debinstall
}

function bio {
   PACKAGES=$BIODEB
   debinstall
   phylowininstall
}

function devel {
   PACKAGES=$DEVDEB
   debinstall
}
function publ {
   PACKAGES=$PUBDEB
   debinstall
}
function scipy {
   PACKAGES=$SCIPYDEB
   debinstall
}
function jabref {
    javainstall
    jabrefinstall
}
function acroread {
   PACKAGES=$ACRODEB
   debinstall
}

###MAIN###
logstart
if  test $USER = "root"
then
       if test `ps ax | grep synaptic | wc -l` -gt 1
       then
           zenity --info --title "Scibuntu" --text "Please close all instances of Synaptic or apt-get"
       fi
       choose
       zenity --info --title "Scibuntu" --text "Installation finished"
else
       zenity --info --title "Scibuntu" --text "USAGE: sudo $0"
fi
logstop

---

### Post by shateredsoul on 2009-03-11
for some who may run across this .. download the file.  If that doesn't work try different mirrors.  If that doesn't work copy and paste that weird code you get if you try to download now (or whatever that is called) and paste it in a simple text document (name it scibuntu.sh) and if you downloaded the file just relabel it with a .sh at the end.

Go to terminal type in "cd Desktop" and then "sudo ./nameoffile.sh" of coures relabel the nameoffile to whatever you named it.  

It takes about an hour to install.

---

