---
title: "Installation quetsion..."
date: 2005-12-13
forum: General Help
---

### Post by wham on 2005-12-13
I just downloaded two files from the gtkpod site and now have these on my desktop:

libgpod-0.3.0.tar.gz
gtkpod-0.99.0.tar.gz

I have no clue as what to do next to actually get them installed.

---

### Post by teaker1s on 2005-12-13
gkpod is a package you can install from repositories with
'sudo synaptic'

you will need 'build-essential' before you compile if you want to compile your files as they may be a later version
then I just click on files and extract or you can use comandline

then terminal
cd into the directory
eg.
'cd /home/daniel/Desktop'

'./configure'
if it goes well and nothing reports missing
'make'
sudo make install


I prefer 'checkinstall' found and installed with synaptic as it's easier to find and remove unwanted programs later -instead of 'sudo make install 'sudo checkinstall'

---

### Post by wham on 2005-12-13
I think maybe I should've asked in the "Absolute Beginner" section because I'm lost now. I already have gtkpod on here, but this is the latest release that supports video.
I'm sorry.

---

### Post by brynjarh on 2005-12-13
[QUOTE=wham]I just downloaded two files from the gtkpod site and now have these on my desktop:

libgpod-0.3.0.tar.gz
gtkpod-0.99.0.tar.gz

I have no clue as what to do next to actually get them installed.[/QUOTE]
First you must realize you are going to be compiling this software, which is different from installing a .deb file.

Step.1: Extract
GUI: Right click libgpod-0.3.0.tar.gz, choose Extract Here, and the same with the other one.
CLI: Open up a terminal by doing Applications > Accessories > Terminal, from there go to the location of the files, example **cd /home/user_a/tmp/** and there do **tar -zxf libgpod-0.3.0.tar.gz** and the same with the other file.

Step2: ./configure , make, sudo make install
  CLI: go to the directory that was extracted of ether software, example **cd libgpod-0.3.0**, there you should read the INSTALL file by doing for example **cat INSTALL** or **gedit INSTALL**, and it will probably tell you to do **./configure**, then **make** and then **make install** but that's incorrect, you should end with **sudo make install**. Hopefully it will also tell you what dependencies the software has so you can install that first. Then do the same with gtkpod.

It's not going to work if you don't fulfill the dependencies, you might also run into more problems like needing to switch to an earlier version of the compiler and so on so forth.

---

### Post by wham on 2005-12-13
I got as far as 'Extract Here.' After that I opened a terminal up and nothing happened.

---

### Post by brynjarh on 2005-12-13
[QUOTE=wham]I got as far as 'Extract Here.' After that I opened a terminal up and nothing happened.[/QUOTE]
You mean like the terminal didn't even start? Or that it did but you expected something more? It seams kind of odd that the terminal wouldn't start..

CLI(Command Line Interface), you should learn to use that before going any further if you haven't already, the best place I know of to start at is [http://www.linuxcommand.org/]("http://www.linuxcommand.org/"). That is, if you want to be able to use the command line.

I don't know of any compiling guides, though a quick look without reading anything tells me this here might be useful [http://www.aboutdebian.com/compile.htm]("http://www.aboutdebian.com/compile.htm").

---

### Post by wham on 2005-12-13
Step.1: Extract
GUI: Right click libgpod-0.3.0.tar.gz, choose Extract Here, and the same with the other one.

**I did this.**

CLI: Open up a terminal by doing Applications > Accessories > Terminal, from there go to the location of the files, example **cd /home/user_a/tmp/** and there do **tar -zxf libgpod-0.3.0.tar.gz** and the same with the other file.

**The terminal opened and then I typed in 'cd /home/crap/tmp' (was that even what I was supposed to type?) and it says no such file or directory.**

Step2: ./configure , make, sudo make install
CLI: go to the directory that was extracted of ether software, example **cd libgpod-0.3.0**, there you should read the INSTALL file by doing for example **cat INSTALL** or **gedit INSTALL**, and it will probably tell you to do **./configure**, then **make** and then **make install** but that's incorrect, you should end with **sudo make install**. Hopefully it will also tell you what dependencies the software has so you can install that first. Then do the same with gtkpod.

[B]I read the INSTALL file and didn't understand what anything meant.
Thanks for being patient with me.[/B]

---

### Post by brynjarh on 2005-12-13
I recommend that you learn how to operate the command line interface/shell/terminal better and then figure out/learn/get help on how to compile software, where [http://www.linuxcommand.org/]("http://www.linuxcommand.org/") would be a good start.

Compiling is complicated if you don't know what your doing and even more complicated if you haven't learned how to use the command line. I personally try to stay as far away from compiling as I can, I only use it for survival purposes, not entertainment purposes and never on my **main ultra clean, usable, default and secure desktop**, just on my secondary machines.

The *nix world can be a complicated place though Ubuntu and many many other projects are doing a great job at making it more user friendly. ;)

---

### Post by wham on 2005-12-14
Ok, thanks for all the help.

One last question. How long will it take before this is available in the synaptic package manager so I can install it from there? It was released on December 12th. Is there a certain amount of time or how does that work?

---

### Post by RAOF on 2005-12-14
Ooops, double post.  Check the next page.

---

### Post by RAOF on 2005-12-14
It's not going to be in the official repositories.  The only additions there will be bug-fixes & security updates (I really should find the Ubuntu policy page for this :))

It's possible that it will get in to Dapper, and be added to the (semi-official) backports repository, but it's not even in Dapper (the development branch), so it will be some time.  If you really need the video capabilities of gtkpod, you will have to compile from source, at least for now.  Here's a full guide for compiling gtkpod, assuming that the two files are on your desktop.

At a terminal: (A useful hint - pressing the "tab" button will automatically complete partial commands.  For example, try cp ~/Des (tab) /libg (tab).  It should produce cp ~/Desktop/libgpod-0.3.0.tar.gz)
```
cd ~
mkdir Temp
cd Temp
cp ~/Desktop/libgpod-0.3.0.tar.gz .
cp ~/Desktop/gtkpod-0.99.0.tar.gz .
tar xzvf libgpod-0.3.0.tar.gz
tar xzvf gtkpod-0.99.0.tar.gz
sudo apt-get update
sudo apt-get build-dep gtkpod
sudo apt-get install build-essential checkinstall
cd libgpod-0.3.0
./configure --prefix=/usr
make
sudo checkinstall
(Add in the information it asks for.  It doesn't really matter what you put in here)
cd ..
cd gtkpod-0.99.0
./configure --prefix=/usr
make
sudo checkinstall
(Once again, add stuff in)

```
This should configure, compile, & install gtkpod.  Plus, by using checkinstall, it will show up in synaptic if you ever want to uninstall it.

---

### Post by wham on 2005-12-14
It seems to be going fine and then this happens;

'After unpacking 34.3MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Abort.'

Why is it aborting if I type Y?

---

### Post by RAOF on 2005-12-14
No idea.  Try just pressing enter instead of typing Y? (Enter will accept the default, which is yes)

---

### Post by wham on 2005-12-14
No, it still says abort. Am I supposed to uninstall the current gtkpod already installed?

---

### Post by RAOF on 2005-12-14
No, it should end up just replacing the existing package.

Try a reboot?

---

### Post by stuporglue on 2005-12-14
Do you have the 34+ Mb of disk space free?

---

### Post by wham on 2005-12-14
Yeah, I have the space.

---

