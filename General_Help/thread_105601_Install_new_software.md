---
title: "Install new software"
date: 2005-12-18
forum: General Help
---

### Post by Jared on 2005-12-18
Ok, I feel about as dumb as a rock right now......I used to consider myself very computer literate.

I am new to linux, and installed ubuntu 5.10 with the XFCE desktop on a computer that I received for free from my mother.  I think it has 320MB of RAM, and it is running a K6 AMD processor (it originally came with Windows 98).  I got Ubuntu up and running, and I got the XFCE desktop to open up, but my problem is that for the life of me I can't install software on it.

I have downloaded files that end in .tar.gz, I untar them from the command line, and then I end up with a subdirectory full of files.  I then tried running ./configure and I get an error message that "no suitable C compiler was found in the path".  I type "gcc", and it gives me an error message.  I downloaded firefox 1.5 and when I untar it the "./configure" command doesn't do anything, and if I type "firefox" from the directory, then firefox 1.0 pops up.

Also - can I download and use .rpm or .deb packages, and how would I go about doing that?

I feel like a complete idiot, but I need step-by-step instructions for downloading and installing new software.  Everything I read seems like it is assuming I know more than I actually know.

Any help would be greatly appreciated.

Thanks,

Jared

---

### Post by arctic on 2005-12-18
Hehehe... well, you are making things more complicated as they are. In Ubuntu, you have two options for installing software (Most distros arethe same in this respect). Either, you can install stuff from a command line (not recommended for complete newbies newbies) and you can use a tool called Synaptic. Synaptic offers you access to several software mirrors on the net from where you can install thousands of packages with two mouseclicks. The packages it downloads are preconfigure .deb packages that will run instantly on your system. All you need is a working network-connection and to set up your mirrors using the top-menu bar.

If you want to install stuff from a terminal, type 
apt-get --help
and
man apt-get

This will answer most of your questions, I guess.

Oh... about gcc: When you try to compile things from scratch (=using source packages) you need to install the development software, e.g. the libraries for gcc. It's just like home-constructing. You cannot build a new roof without owning the necessary tools for the job.

---

### Post by DJ_Max on 2005-12-18
[QUOTE=Jared]Ok, I feel about as dumb as a rock right now......I used to consider myself very computer literate.
[/QUOTE]
I've come to the conclusion that being Windows literate and actual computer literate are two different things.

As for the GCC compiler, you need to install the *build-essential* meta-package.
[http://help.ubuntu.com/starterguide/C/ch03s08.html#id2531297](http://help.ubuntu.com/starterguide/C/ch03s08.html#id2531297)

---

### Post by maglis on 2005-12-19
[quote=Jared]

I have downloaded files that end in .tar.gz, I untar them from the command line, and then I end up with a subdirectory full of files. I then tried running ./configure and I get an error message that "no suitable C compiler was found in the path". I type "gcc", and it gives me an error message. I downloaded firefox 1.5 and when I untar it the "./configure" command doesn't do anything, and if I type "firefox" from the directory, then firefox 1.0 pops up.
[/quote] 
tar archives (or even gziped tar archives) are an archiving and /or compression method used for packaging toghether many files. These files are not necessarily in an "installable" condition. They can be program source files (like your first case) or ready to run on the spot binary (=executable) files (like your second case). Or they could be anything really.

Ubuntu has enormous repositories of ready to download, install and use packages (= programs or libraries of code) that can help you do all sorts of usefull things with your computer. This is the "preferred" ubuntu way and certainly "newbie safe". It is not the only way to install and run code on the system, it is a reliable, secure and safe way to manage your system. It is also one of the biggest selling points of any Debian based distribution like Ubuntu.

[quote=Jared]
Also - can I download and use .rpm or .deb packages, and how would I go about doing that?
[/quote] 
Alternative ways to install software:[LIST]
[*]deb: you run ```
dpkg -i your_package.deb
``` The deb package is a sofisticated type of installation file that not only includes all binary code and configuration files but also a program that checks if all necessary software is already installed in your system before it installs the current one. It aborts with an informative message otherwise. It also knows where and how to install your package if everything is ok, and creates all necessary records in the "installed in your system" database for you or other programs to know. It finally may do (depending on the program type) nice things like create menu entries for you to click. It still is a bothersome way to install deb packages, for you need to resolve all unmet dependencies by hand. Use synaptic, or even "Add Applications" menu.
[*]tar(gz).[LIST]
[*]If you get source code (in a compiled computer language like C) in this format, you need to have pre-installed all necessary developer(ing) tools need by the specific program. Usually, but not allways, the developer that supplied you with the code was polite enough to create automated configuration scripts for you. You find what tools you need each time by running the ./configure script which checks the existance in your system of all necessary tools. It warns you for each absense. ./configure script gives you control of other options you need/want to set before you compile Then you run ```
make
```. And finally run ```
sudo make install
```.
[*]If you get binary code you can simply unpack the archive and run the code in place or move the entire directory to the path (= directory in your computer filesystem) that you want to run it from.
[*]If you get source code in an interpreted (non compiled) language (like python, perl, php etc) you simply feed the corresponding interpreter with your file. For example, if you have a python script myscipt.py you run```
python myscript.py
```.[/LIST] 
[*]rpm: This is an alien form of pre-packaged binary format that is not native in debian based distributions. There is a way to install these through the "alien" package. Locate in synaptic and install alien (and all its dependencies) and read its manual before you try this method. It is equivalent in steps (not in quality) to .deb method above. The problem is that these rpm packages have been built in alien systems, that have different versions of all system software from ubuntu. It is uncertain that they will run or even install. Avoid them.[/LIST]It is unlikely that you'll need something that is not already in the Ubuntu repositories (synaptic). Use these only!

The only reason I see for you to use other installation methods is if you need to compile/test/debug the cutting-edge version of a program. These are usally in tar.gz format. There is a possible rare case that you really need to use a program that you only find in say rpm format. Then you need to test installation carefully and manage it manually thereafter(=pain).

I hope I helped. :smile:

---

### Post by Jared on 2005-12-21
I havn't had any problems with the apt-get function, I used it to install XFCE on my computer.  I really want to learn how to build programs from the sourcecode because that seems to be the standard disitribution method.  I am a student in Electrical Engineering in my final semester and want to run ngspice.  I found ngsice as a .tar.gz sourcecode.  

How hard is it to install gcc and other required libraries to build programs from source?

---

### Post by anil_robo on 2005-12-21
[quote=Jared]How hard is it to install gcc and other required libraries to build programs from source?[/quote]

I dread command like more than anyone else, but after following numerous instructions on command line in these forums, I can tell you that if you know what you're typing, compiling is a child's play! ;)

if you want to install something, you can use the command:
sudo apt-get install something

If you want to remove something, you can use the command:
sudo apt-get remove something

If you have only the source code, and want to compile, then you can do ./configure, followed by make, followed by make install. Bingo! :)

If stuck, just search in these forums, and you'll find the necessary info, like I did! :)

---

### Post by aysiu on 2005-12-21
Read the second link of my sig.

---

