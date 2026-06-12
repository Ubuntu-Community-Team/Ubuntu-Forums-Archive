---
title: "Arcexplorer setup help"
date: 2006-07-14
forum: Desktop Environments
---

### Post by michaeljb2005 on 2006-07-14
Hi i'm trying to install Arcexplorer but i'm confused about some of the installation instructions and am not savvy enough to know what to do.  The instructions are as such:

Downloading ArcExplorer 9.1 for Linux

System Requirements

    * Operating System: Linux-Intel Red Hat Enterprise Server AS/ES 3.0, SUSE Linux Enterprise Server 9
    * Disk Space: 24 MB
    * JDK/JRE: 1.4.2_06 (included in download)

Download ArcExplorer 9.1 (ArcExplor9.1_linux.tar)
File Size: 33.3 MB

Installing ArcExplorer 9.1 for Linux
After downloading the ArcExplor9.1_linux.tar, move it to the directory where you wish to install ArcExplorer 9.1, and then tar:

      %tar xvf ArcExplor9.1_linux.tar
      %cd Linux 

The "install" command has four options:

Usage: install <-help | -load | -remove | -verify>

Type "install -help" to read more about the installation procedure.

To start the ArcExplorer 9.1 installation, type the following command in the directory where you downloaded the files on your system:

      %./install -load 

This starts the dialog for the ArcExplorer 9.1 software installation procedure, which is menu driven.

Default selections are noted in brackets [ ]. To obtain a list of options or online help, type "?" at any prompt. You can quit the installation procedure at any time by typing "quit" or "q". To return to a previous question, type the caret, "^".

Setting up your Account

ESRI recommends that you execute ArcExplorer 9.1 from a C shell. The following instructions are for a C shell environment setup.

To use ArcExplorer 9.1, add the following lines to your .login or .cshrc file:

      setenv AEJHOME <path to installation directory>/aej91exe
      setenv LD_LIBRARY_PATH $AEJHOME/lib 

Make sure that $AEJHOME/bin is in the PATH.

      set path = ( $path $AEJHOME/bin ) 

To enable the changes, type:

      % source <.login or .cshrc> 

Starting ArcExplorer 9.1 on Linux

With $AEJHOME/bin included in your PATH, start ArcExplorer by typing:

      aejava 

The part I have a problem with is when it says:

"Setting up your Account

ESRI recommends that you execute ArcExplorer 9.1 from a C shell. The following instructions are for a C shell environment setup.

To use ArcExplorer 9.1, add the following lines to your .login or .cshrc file:

      setenv AEJHOME <path to installation directory>/aej91exe
      setenv LD_LIBRARY_PATH $AEJHOME/lib 

Make sure that $AEJHOME/bin is in the PATH.

      set path = ( $path $AEJHOME/bin ) 

To enable the changes, type:

      % source <.login or .cshrc> "

What is sentev?  Where the heck is .login or .cshrc?  Help?

---

### Post by ayoli on 2006-07-14
i guess you can set these nvironement vars in your ~/.bashrc  (.cshrc must be an rc file for a csh shell) and setenv is the command in tcsh to set environement variables, but it's not the same in bash, so if you use ~/.bashrc it will look like this:
```
AEJHOME="<path to installation directory>/aej91exe"
LD_LIBRARY_PATH="$AEJHOME/lib"
PATH="$PATH:$AEJHOME/bin"
export AEJHOME LD_LIBRARY_PATH PATH
```
hope it helps a bit,
regards.

---

### Post by michaeljb2005 on 2006-12-23
> **ayoli said:**
> i guess you can set these nvironement vars in your ~/.bashrc  (.cshrc must be an rc file for a csh shell) and setenv is the command in tcsh to set environement variables, but it's not the same in bash, so if you use ~/.bashrc it will look like this:
```
AEJHOME="<path to installation directory>/aej91exe"
LD_LIBRARY_PATH="$AEJHOME/lib"
PATH="$PATH:$AEJHOME/bin"
export AEJHOME LD_LIBRARY_PATH PATH
```
hope it helps a bit,
regards.

So I just create a file called ~/.bashrc and put all the stuff you said to put in there, of course substituting for personalized system?

---

### Post by michaeljb2005 on 2007-03-24
When I put this in and run from terminal it gives me an error message 
** JAVA_HOME must be defined

What do I do now?

---

