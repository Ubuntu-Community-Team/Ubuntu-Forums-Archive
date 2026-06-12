---
title: "Coventor"
date: 2009-11-05
forum: Education &amp; Science
---

### Post by edmurper on 2009-11-05
Hi, I'm a student trying to use Coventor, is great when U want to simulate micro electro mechanical systems, so I was speaking with the coventor people, they sent me my license for 30 days to try an evaluation license and also I just installed Ubuntu (so, I&#7743; kind of a noob right now), the fact is that I haven't been able to install the linux version of coventor in ubuntu (designed for red hat 4, or 5), could anyone please help me installing and running it? 

cheers!

---

### Post by Lateralis on 2009-11-05
Hi there edmurper - welcome to Uuntu and the forums!  

Just a quick question: are you trying to install the program from source (source code which will need compiling) or installing using a pre-compiled binary file?

---

### Post by edmurper on 2009-11-05
Thank you for your welcome to ubuntu ^.^ and also thanks for the fast reply, I have two files, the installation file is the kind of "script on c shell?" and another one kind of .tgz file, when I click on the first one, Ubuntu ask me if I want to execute it on the terminal, but the terminal never opens, and thus the file is not executed. I have tried also to reach this file from my bash terminal, however I'm sucha a noob that I dont know how to move around the terminal

---

### Post by Lateralis on 2009-11-06
Hi there!  

Firstly, there are different types of shell: the Bourne shell (sh), Bourne again shell (bash, based on sh), the C shell (csh) and the TENEX C shell (tcsh, based on csh).  If you have a shell script written for one type of shell it might not work in any of the others, especially if there are commands used that are specific to that particular shell.  Thus, trying to execute a c shell script in Ubuntu (bash shell) might not work.  I know you can download and install the c shell from the Ubuntu software repositories.  I've never done this before (as I have no need) so don't know what the wider implications of doing this are (but having checked out a few things I don't believe there are any) but you can install the c shell by typing the following into the command line: 

```
sudo aptitude install csh
```

I'll assume that you don't know much about the command line, but this basically tells the operating system to use the programme apitude (sometimes people say to use *apt-get* install of *aptitude*... the two are equivalent) to install the package called *csh*.  The *sudo* command is ubiquitous in Ubuntu - it grants the user "super user" privileges allowing you to make changes to the system.  Without using *sudo[I/] you cannot make *any* changes to the system.  You will be required to type your password into the command line after you use [I]sudo*.  

To navigate around using the command line, you can use the following commands:  

*ls* - list the visible contents of your current directory 
*ls <directory>* - list the constents of <directory>
*ls -a* - list all files, visible and hidden, in the current directory
*cd <directory>* - change from current directory to <directory>.  For example 

*cd ..* (means change to parent directory)
*cd /home/* (means change to the home directory)
*cd /* (means change to the "root" directory)
etc ad nauseum.  

If you want to execute a shell script or executable, you prefix the filename with a dot slash (./).  So if you have the file *chocolate.sh* which you want to execute, type *sudo ./chcolate.sh* in the directory in which *chocolate.sh* is located.  

NOTE: In some cases, ./ doesn't work and then you'll need to type *sudo sh chocolate.sh*
NOTE: Sometimes the file isn't set such that you have permission to execute the file.  If that is the case then you can use the command *sudo chmod +x <filename>*.  


OK, so now you can navigate around the command line to find the correct directory and execute shell scripts.  What of the tgz file?  This file is a compressed file in Linux (much like .zip is a compressed file in Windows). To uncompress the file there is a programme called "tar" built into every linux distribution.  To uncompress the file, type 

```
tar -xvzf <filename>
```

This command instructs tar to uncompress <filename> with the xvzf options;  x means "extract", v means "verbose" (it will tell you what it is uncompressing), whilst z and f tells tar what type of file it is you are trying to uncompress.  (Just as there are different types of compressed files in Windows, ie. .zip and .rar, there are different types of compressed files in Ubuntu, and we have to tell tar what type of file it is trying to uncompress.) 


OK, I hope that helps!

---

