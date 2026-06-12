---
title: "Problem running Gaussview on Ubuntu"
date: 2007-12-07
forum: Education &amp; Science
---

### Post by shyuep on 2007-12-07
I am having a major problem running Gaussview 3.09 (a quantum chemistry tool) on Ubuntu Gusty.  As I only have the binaries, recompiling is not an option.  Basically, Gaussview requires libXft1, which I promptly installed from the relevant packages.  While Gaussview will run, the program windows do not refresh properly during usage.  For example, when I drag and move a molecule window, the window does not refresh and shows whatever is in the background.  The only way I can "refresh" the window is to do a rotation of the molecule.  This is severely crimping my efficiency with this software.  Please see the screenshot below for an example.
 
[IMG]http://jynnsp.com/Temp/Screenshot.png[/IMG]

Can someone give me some advice on how I can get round this problem?  I suspect it has something to do with the libraries that can with Gaussview itself. No other program has this problem.  For info, I am using a Dell 640m laptop with a Intel i810 graphics card.

Thanks in advance for any advice given.

---

### Post by agapito on 2008-01-22
I have Gaussview 03 installed on several Ubuntu machines and it runs perfectly (even in my 64 bit laptop, which has a 945GM Express Chipset). Try disabling the desktop effects, if they are on.

---

### Post by shyuep on 2008-01-22
Hi agapito,

Thanks for the advice.  Yes, the desktop effects are already disabled but I still face the same problem.  I actually installed Gaussview on another UBuntu machine with an ATI graphcis card and the same problem occurs.  May I know what version of Gaussview you are using? 

I suspect it is something to do with the libXft.so.1 that Gaussview uses.  It is not part of UBuntu and I had to get the binary from an RPM for Red Hat instead.  I can't seem to find libXft.so.1 for Debian distributions anywhere.

---

### Post by agapito on 2008-01-22
I have Gaussview 3.08. Yes, maybe it's the libXft.so.1 I remember having to get one, but I don't remember from where...
Here is the link to the libXft.so.1 I use:
[http://www.mediafire.com/?2djtldj2xyj]("http://www.mediafire.com/?2djtldj2xyj")

---

### Post by shyuep on 2008-01-28
Thanks very much!  I tried using this libXft.so.1 but unfortunately it still doesn't work.  I am at a loss now.  Gaussview does not refresh properly on two different computers with completely different graphics cards and tried with two different libXft.so.1 .  I wonder where the problem can lie.

---

### Post by knowname on 2008-12-08
I've just installed GaussView and have this same issue. Has anyone figured out a solution?

---

### Post by phenolholic on 2010-05-29
is there a solution to this? i'm thinking of going back to ubuntu after a hiatus. gaussview is absolutely essential to my well-being. what lines of work do you folks do, obviously its something in the neck of computational chemistry.

---

### Post by phenolholic on 2010-05-29
*bump*
calling all computational chemists

---

### Post by knowname on 2010-05-29
I did get it to run on a previous machine, and I kept good notes while I did it. I have pasted them below. Note I have separate notes on installing the g03 executable.

I no longer run Gaussian. I am doing everything in [Atomic Simulation Environment]("https://wiki.fysik.dtu.dk/ase/") these days, which I prefer quite a bit over Gaussian since it is built in python and has a pure python interface. It supports 14 different calculators, like GPAW, Dacapo/Jacapo and VASP. It does not have a wrapper for Gaussian, but I would think it would be quite straightforward to use it to create Gaussian input files. The GUI for it is functional for viewing, but building of molecules is done more via python scripts than through the GUI.

My notes from installing GaussView are below, for what they are worth. I think I did this on Ubuntu 8.04, so who knows if it will work with newer versions of Gaussview and Ubuntu.

Installed gaussview. This was complicated.
1.Copied GV_309_LINUX.TAZ to the directory /usr/chem
2.Extracted it with: cat GV_309_LINUX.TAZ | zcat | tar xvf -
3.Changed the variable GV_DIR in /usr/chem/gv/init_gv.bash so that it points to 'usr/chem/gv'
4.Ran this script with . init_gv.bash
5.Tried to run gaussview with gv, but got an error: “ /usr/chem/gv/gview: error while loading shared libraries: libstdc++-libc6.2-2.so.3: cannot open shared object file: No such file or directory”
6.This doesn't exist in the 8.04 repositories, so I had to get it from the Gutsy repositories. I installed libstdc++2.10-glibc2.2_2.95.4-24_i386.deb from [http://packages.ubuntu.com/gutsy/libstdc%2B%2B2.10-glibc2.2](http://packages.ubuntu.com/gutsy/libstdc%2B%2B2.10-glibc2.2)
7.Tried to run gaussview with 'gv', but got another error: “/usr/chem/gv/gview: error while loading shared libraries: libXft.so.1: cannot open shared object file: No such file or directory ”
8.Copied a version of libXft.so.1, that I found on the internet, to /usr/chem/gv/lib/ and changed its permissions to look like the other libraries in there. Note this is better than putting it in the general libraries directory, /etc/lib/, which would have put it there for all files to use.
9.Now it seems to run.
10.Added ” . $g03root/gv/init_gv.bash “ to my .bashrc file.
11.Like for g03, I needed to modify this so that it does not modify the LD_LIBRARY_PATH variable. This was a little simpler than for g03. I commented out most of init_gv.bash so that the only functional line left is 
export GV_DIR='/usr/chem/gv'
12.I added the following function to my .bashrc (/home/aap/.bashrc):
gv () { LD_LIBRARY_PATH=$g03root"/gv/lib" $g03root/gv/gview; }

---

