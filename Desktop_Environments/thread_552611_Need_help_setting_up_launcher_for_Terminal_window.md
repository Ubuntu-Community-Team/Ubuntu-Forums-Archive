---
title: "Need help setting up launcher for Terminal window"
date: 2007-09-16
forum: Desktop Environments
---

### Post by inverouglas on 2007-09-16
Hello --

For various reasons, I am migrating from Windows to Ubuntu.  In Windows, I can write a shell script (known there as a "batch") which will set up the environment in a terminal.  Then I can set up a "shortcut" (looks like a Gnome launcher) which opens a shell, runs the setup script, and stays open, allowing me to enter commands.

The closest I can get in Gnome is to set up a launcher, which then flashes momentarily before closing.

Here is what I want to do in Gnome:

(1) write an executable script named  startup.sh  which will set some environment variables and echo a  string or two.  

  Example: ------------------------------
  #!/bin/sh
  ## startup.sh -- set up the environment
  export xxMYFILE=$1
  echo Target file is: $1
  echo Environment has been set up
  ---------------------------------------
  
  This first step seems pretty straightforward.  I know about making the script executable.

(2) set up a launcher which will open a terminal window, execute the startup.sh,
and leave the terminal open for other commands.

The best I can do is get the terminal to open and close.  I have tried things like:
gnome-terminal --window-with-profile=xxstart -x bash -c ~/somedir/startup.sh

This works, but the terminal is frozen (I cannot enter a command)

------------------------------------------------------------------------
Here is what works under Windows:

In Windows, I enter the following command in the "shortcut":
%comspec% /kC:\somedir\startup.bat

%comspec% pulls in  cmd.exe  (the shell executable)

/k        option which "K"eeps the shell open after treating the remainder of
          the line as a command
          
C:\somedir\startup.bat
          fully qualified name of script

------------------------------------------------------------------------

Any direct suggestions, or references would be a great help.  I looked at the output from  man bash .  (I am confused by login vs non-login shells, and some of the launcher options.)

-- Inverouglas

---

### Post by ddrichardson on 2007-09-17
I see where you are going but its a very convoluted way of solving the problem. The file to consider is .bashrc that sets up environment variables and two other files: .login that's executed when the shells opened and .logout thats surprisingly enough the opposite.

Unless there is a reason to open multiple terms with different environment variables?

---

### Post by inverouglas on 2007-09-18
Thanks!  Your suggestion was helpful in focusing my attention
on  .bashrc  and similar setup files, and on the subject of what happens
when  bash  is invoked.  The  --rcfile FILE  option of  bash  seems
to be the feature I need in order to invoke a custom setup script
for each application in my toolbox.

I guess this is the feature closest to the  -k"COMMAND"  option of the
Windows command shell ( cmd.exe ) .  Using that option, it is possible
to specify a script which sets up the environment inside a shell.
(In case anyone is wondering, the alternative option is
-c"COMMAND"  , which will execute a script and exit the shell.)



Based on your suggestion, I proceeded as follows to create a launcher
which will open a terminal window set up the way I need for a program
library called  Application1 :

(1) Set exeutable flag for  ~/.bashrc , so I can call it during setup.

(2) Created a setup script named  ~/work/app1setup.sh
contents of script:
-------------------------------------------------------
~/.bashrc
export app1lib=~/work/app1lib
cd ~/work/app1work
echo Welcome to Application 1 -- $0 $1 $2
-------------------------------------------------------

The idea is to call the regular  .bashrc  before doing setup specific
to  Application1 .  In this case, we set an environment variable
so the app can find the programs, then switch to a work directory, and
finally print a welcome message including the actual command line.


(2) Set up a Launcher with the following command: 
bash --rcfile ~/work/app1startup.sh -i -s

When I click on the launcher, a terminal window opens, the
setup display is correct, and I am able to continue entering commands.

This is pretty much the goal of asking my question, and the result seems
usable (despite issues noted below).  I can therefore mark the
thread "SOLVED".

Issues
------
Please note that despite the  -i  option being present, I get a message
during  .bashrc  which complains about the  return  statement on line 6
of the standard  .bashrc .  Apparently a  bash  invokes the setup
script in a mode which cannot "return" from a script.  I assume this means
that the rest of  .bashrc  does not get executed.

It appears that  bash  considers itself to be non-interactive at that point.


It does not appear that I need to invoke  gnome-terminal  explicitly.
Perhaps this is part of the "convolution" you mentioned.

Remaining issues (to be the subject of a new question)
------------------------------------------------------
Under Windows, the drag-and-drop functionality of the GUI
appears to work by appending the filename of the dropped object
as a parameter of the executable under the drop target.
This applies not only when dropping is done with a mouse, but
also when selecting possible targets from a  SendTo  menu.

As an example, a user can add three launchers to a general SendTo menu,
each specifying the executable file for an editor (say: a line editor,
a GUI text editor, and a hex editor.)  In the file browser
(called the "Explorer" in Windows) one can right click on a file, select
SendTo, and click on one of the icons in the list, which would
include three editor icons just mentioned.

When the user clicks on the choice,  the name of the file from the
file browser is appended to the command in the launcher.  The result
might look like:

"C:\Program Files\guieditplus.exe"  "D:\myfiles\proj1\letter.txt"

This has worked superbly under Windows for setting up various
command-line utilities so that they can be used from the GUI
filesystem browser.  A script can switch the current directory
to that of the selected file, and add a specific program library
to the PATH.  (This approach allows me to have several versions
of the same library installed, and also keeps the PATH free of
applications not needed in the current context.)

So far, I do not see Nautilus passing anything to a launcher in this way.
As mentioned above this will be the subject of a new question.

Again, many thanks for getting me started on sorting out the behavior
of  bash.

---

### Post by ddrichardson on 2007-09-18
> **inverouglas said:**
> Issues
------
Please note that despite the  -i  option being present, I get a message
during  .bashrc  which complains about the  return  statement on line 6
of the standard  .bashrc .  Apparently a  bash  invokes the setup
script in a mode which cannot "return" from a script.  I assume this means
that the rest of  .bashrc  does not get executed.

You don't show the script, so I can't help! I suspect thought that its simply that unlike windows batch files, you can set programs to run in the background without expectin a return by using "&" after the command.

---

