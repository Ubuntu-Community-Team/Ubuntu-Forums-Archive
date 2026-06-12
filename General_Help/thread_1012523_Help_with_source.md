---
title: "Help with source"
date: 2008-12-15
forum: General Help
---

### Post by DracoNyon on 2008-12-15
Okay so I have 8.10, even though this happened with 8.04. I cd into the correct file. doing cd /home/"name"/Desktop/(name of extracted file folder) and i get "Command line not found" when I type in ./configure  it is very depressing since I cannot install anything. Can someone please tell me what I am doing wrong?

---

### Post by cdtech on 2008-12-15
What are you trying to install? Could you not find it in the "Synaptic Package Manager"?

To move into a directory:
```
cd /home/user/Desktop/folder
```

---

### Post by DracoNyon on 2008-12-15
I did that. It is in the SPM but I can never find out where it installed to. And please I am still going to need this skill so i would like to learn it now.Instead of just avoiding it.

---

### Post by cdtech on 2008-12-15
Ok, so first lets see how you downloaded the file, from a site using firefox?

If so lets look at your home directory. It could have downloaded the file to "/home/user/Downloads". If you do "ls -la" on the command line you will see all folders, even the hidden ones.

**UPDATE::.**
Do you just want to know where the "SPM" installs it?
If so just type "whereis programname" on the command line and it will show you where it is installed.

---

### Post by iponeverything on 2008-12-15
> **DracoNyon said:**
> Okay so I have 8.10, even though this happened with 8.04. I cd into the correct file. doing cd /home/"name"/Desktop/(name of extracted file folder) and i get "Command line not found" when I type in ./configure  it is very depressing since I cannot install anything. Can someone please tell me what I am doing wrong?

Not every thing that needs to be compiled uses configure.

Look in the directory for a Readme. Also look for instructions on the site where you downloaded the source. Failing that, upload a directory listing from the directory and someone will be able to tell you what is going on.

---

### Post by DracoNyon on 2008-12-15
thats not the problem, I used firefox, or Opera and the tar.gar is own the desktop. I extract it and I navigate to the folder that was the extracted file. btw that Is-la thing didn't work.

okay so I am trying to install Visualboy Advance because the one that came with the add/remove was tooo slow so i am trying to downgrade and this is what was in the REadme.

Compiling the sources

---------------------



See the INSTALL file for compiling instructions. Please note the following

requisites to compile:



- GCC must be 3.x or greater in order to compile GBA.cpp with -O2. Earlier

  versions have a problem during optimization that requires an absurd

  ammount of memory and usually ends up crashing the compiler/computer

- On Windows, Microsoft Visual C++ 6 or later is needed. Please note that

  some of the source code will not compile with the shipped header files.

  You will need to install the most recent Platform SDK from Microsoft.



Installing

----------



The easiest installation is to place all files in the distribution in the

same directory.



but there is no install readme

---

### Post by cdtech on 2008-12-15
> **DracoNyon said:**
> thats not the problem, I used firefox, or Opera and the tar.gar is own the desktop. I extract it and I navigate to the folder that was the extracted file. btw that Is-la thing didn't work.

Thats "ell ess" not "eye ess" lol

---

### Post by cdtech on 2008-12-15
Did you read the "See the INSTALL file for compiling instructions" and you may need to uninstall the current version first.

---

### Post by DracoNyon on 2008-12-17
Bump. Besides if you read all my post you would have found out that there was no INSTALL file.

---

### Post by Ayuthia on 2008-12-17
Can you post the listing of:
```
ls -la
```
They are lower case L not one's or I's.  It will help us see what commands might be able to be used.

---

### Post by oldos2er on 2008-12-17
I just downloaded VisualBoyAdvance-1.7.2, and there is both a README and INSTALL file. Among other things, it says you need these dependencies:

The following software is needed in order to compile:

- libpng: [http://www.libpng.org/pub/png/libpng.html](http://www.libpng.org/pub/png/libpng.html)
- zlib: [http://www.gzip.org/zlib/](http://www.gzip.org/zlib/)
- libSDL: [http://www.libsdl.org](http://www.libsdl.org)
- nasm (optional for x86 MMX support): [http://nasm.sourceforge.net/](http://nasm.sourceforge.net/)
- GCC 3.x: in order to compile VBA, you will GCC 3.x or greater because of
  a really bad bug in GCC 2.95 where it allocates an immense amount of
  memory in order to compile GBA.cpp. If you really want to test it with
  GCC 2.95, try exporting CXXFLAGS=-g to avoid optimizations (or try
  different levels of optimization like -O1 or -O0)

Extra software needed to compile the GTK+ GUI:

- gtkmm (>= 2.0): [http://www.gtkmm.org/](http://www.gtkmm.org/)
- libglademm (>= 2.1): [http://www.gtkmm.org/](http://www.gtkmm.org/)

 and of course you'll need to install build-essential as well if you haven't already.

---

### Post by cdtech on 2008-12-17
just seen that

---

