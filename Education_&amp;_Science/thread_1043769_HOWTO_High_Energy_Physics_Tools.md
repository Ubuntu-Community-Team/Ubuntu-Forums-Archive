---
title: "HOWTO: High Energy Physics Tools"
date: 2009-01-18
forum: Education &amp; Science
---

### Post by Catalyst2Death on 2009-01-18
**[SIZE="4"]High Energy Physics Tools[/SIZE]**

1. ROOT

There are two options for installing ROOT, using a pre-compiled binary and installing from source. I suggest installing from source because it allows you to optimize the binary for your machine which is important when running over large datasets.

To install from source:
```
$ sudo apt-get install checkinstall build-essential libxpm-dev libxpm-dev
$ wget ftp://root.cern.ch/root/root_v5.22.00.source.tar.gz
$ tar -xvf root_v5.22.00.source.tar.gz
$ cd root
$ ./configure -linux
$ make
```

On my laptop the build process usually takes ~30-40 minutes.  A number of subsystems are built, and you may get past the original configure but fail at another.  If this happens just use:
```

$ apt-cache search <failed library>
$ sudo apt-get install <library> <library>-dev

```
I'm pretty sure that most of the libraries which are required are installed automatically with Intrepid, I just compiled a copy a couple days ago and all I needed was libxpm.  Once make is done, you can do:
```

$ sudo checkinstall

```
The traditional way of doing it is to set up root in your .bashrc file. If you decide to just download the binaries, all you need to do is extract the tarball and then edit these variables to point to the extracted path. (if you use tcsh or a different shell, then you should edit that one):
```

#Setup Root 5.22
unset root
export ROOTSYS="$HOME/root"
unset LD_LIBRARY_PATH
export LD_LIBRARY_PATH="$ROOTSYS/lib"
alias root="$ROOTSYS/bin/root"
export PATH="$ROOTSYS/bin:${PATH}"
hash -r
```

For more information visit:
root.cern.ch

User's manual (invaluable!): [http://root.cern.ch/drupal/content/users-guide](http://root.cern.ch/drupal/content/users-guide)

General install instructions:
[http://root.cern.ch/root/Install.html](http://root.cern.ch/root/Install.html)

2. LaTeX

Here is a list of the latex packages I have installed:
```
sudo apt-get install texlive texlive-base texlive-base-bin texlive-bibtex-extra texlive-common texlive-extra-utils texlive-font-utils texlive-fonts-extra texlive-fonts-recommended texlive-formats-extra texlive-full texlive-generic-recommended texlive-latex-base texlive-latex-extra texlive-latex-recommended texlive-latex3 texlive-math-extra texlive-pictures texlive-publishers texlive-science

```
It is probably overkill, but It lets me compile all of the science related documents in latex that I've needed.

3. Kerberos

I've included instructions for kerberos because its odd at FNAL.  First you'll want ssh:

$ sudo apt-get install openssh-client

Then you want the **MIT Kerberos**, the Heimdal distribution will work in principal, but I've had trouble, and not using the MIT distribution may lead to authentication problems:

$ sudo apt-get install krb5-user

Then copy the latest krb5.conf to /etc/:

$ wget [http://security.fnal.gov/krb5.conf](http://security.fnal.gov/krb5.conf)
$ sudo mv /etc/krb5.conf{,.orig}
$ sudo mv krb5.conf /etc/

More instructions here: [https://fermilinux.fnal.gov/documentation/security/kerberos-newer-linux/](https://fermilinux.fnal.gov/documentation/security/kerberos-newer-linux/)

**NOTE:** You may need a certificate to see that page

---

### Post by rifak on 2009-04-28
hello, thank you for posting this...but I am running into some real problems when installing Root 5.22/00.

I get the tar, unpack it, then run ./configure linux. it configures and says to run make. i run make and the error it gives is in the .txt file i posted here. the whole beginning is just a huge list of copying the files, so i didnt put all that in the text file, just the end where it throws the error. im not sure how to get past this point. any help would be great

---

### Post by ssam on 2009-04-29
best to use texlive instead of tetex (see [http://www.tug.org/tetex/](http://www.tug.org/tetex/) ). you should not notice much difference, apart from there being more modules available.

the tetex packages in ubuntu are just transitional packages that install texlive.

---

### Post by Catalyst2Death on 2009-04-29
> **switham said:**
> hello, thank you for posting this...but I am running into some real problems when installing Root 5.22/00.

I get the tar, unpack it, then run ./configure linux. it configures and says to run make. i run make and the error it gives is in the .txt file i posted here. the whole beginning is just a huge list of copying the files, so i didnt put all that in the text file, just the end where it throws the error. im not sure how to get past this point. any help would be great

I think the issue here is that you need to set $ROOTSYS and $LD_LIBRARY_PATH before compiling.  This was already taken care of on my installation because I was upgrading to a newer version... Please try this, and if it works, I'll update the instructions:

```
sudo apt-get install checkinstall build-essential libxpm-dev libxpm-dev
wget ftp://root.cern.ch/root/root_v5.22.00.source.tar.gz
tar -xvf root_v5.22.00.source.tar.gz
cd root
unset root
export ROOTSYS="$HOME/root"
unset LD_LIBRARY_PATH
export LD_LIBRARY_PATH="$ROOTSYS/lib"
./configure -linux
make
alias root="$ROOTSYS/bin/root"
export PATH="$ROOTSYS/bin:${PATH}:"

```

---

### Post by rifak on 2009-04-29
thanks for the reply. i did exactly what you said and here is what happens during the make command:

/usr/bin/ld: /usr/local/lib/libz.a(crc32.o): relocation R_X86_64_32 against `a local symbol' can not be used when making a shared object; recompile with -fPIC
/usr/local/lib/libz.a: could not read symbols: Bad value
collect2: ld returned 1 exit status
make: *** [lib/libASImage.so] Error 1
rm core/utils/src/RStl_tmp.cxx core/utils/src/rootcint_tmp.cxx


after a long list of bin/rmkdepend and g++ commands running, it always ends in this. the original post was fixed by running "make distclean" (to basically refresh the configure). here is exactly what i am working with:
macbook core duo
ubuntu 8.04 64-bit
root 5.17 has been installed through repos by adding the sources (i have tried to remove that before building source and still same error)

so that is that. the other method that i tried was just using the binary, and this is what i get when i try to run a macro or plot a .root:


root [0] 
Attaching file dca-thick-thin-pixel.root as _file0...
root [1] .ls
TFile**		dca-thick-thin-pixel.root	
 TFile*		dca-thick-thin-pixel.root	
  KEY: TCanvas	c1;1	c1
root [2] c1->Draw()
dlopen error: libtiff.so.3: cannot open shared object file: No such file or directory
Load Error: Failed to load Dynamic link library /usr/local/root/lib/libASImage.so
Error in <TGHScrollBar::TGHScrollBar>: arrow_*.xpm not found
Error in <TGVScrollBar::TGVScrollBar>: arrow_*.xpm not found

 *** Break *** segmentation violation
(no debugging symbols found)
Attaching to program: /proc/4661/exe, process 4661
(no debugging symbols found)...done.
(no debugging symbols found)...done.
(no debugging symbols found)...done.
(no debugging symbols found)...done.
[Thread debugging using libthread_db enabled]
[New Thread 0xf6c996c0 (LWP 4661)]
(no debugging symbols found)...done.
(no debugging symbols found)...done.
(no debugging symbols found)...done.
(no debugging symbols found)...done.
(no debugging symbols found)...done.
(no debugging symbols found)...done.
(no debugging symbols found)...done.
(no debugging symbols found)...done.
(no debugging symbols found)...done.
(no debugging symbols found)...done.
(no debugging symbols found)...done.
(no debugging symbols found)...done.
(no debugging symbols found)...done.
(no debugging symbols found)...done.
(no debugging symbols found)...done.

warning: Lowest section in system-supplied DSO at 0xffffe000 is .hash at ffffe0b4
(no debugging symbols found)
0xffffe410 in __kernel_vsyscall ()
error detected on stdin
The program is running.  Quit anyway (and detach it)? (y or n) [answered Y; input not from terminal]
Detaching from program: /proc/4661/exe, process 4661



this installation of root was done by downloading the 5.22.00 version of Linux SLC5 x86. i unpacked the tar and placed it in /usr/local/ and added the file in /usr/local/bin/ to link the root executable. why would this be happening? is this not the right version of download for ubuntu 8.04?

---

### Post by Catalyst2Death on 2009-04-29
OK

A couple questions:  Does the version from the repositories work?  5.17 is relatively recent by root standards, and you should have a lot of what you need unless there is something specific from 5.22 releases onwards.

Second:  Are you setting $ROOTSYS and $LD_LIBRARY_PATH to point to the binaries you untarred?  It looks like LD_LIBRARY_PATH is either not set, or set incorrectly.

This may be an obvious point, but have you tried installing libtiff3 from the repositories?  

Another issue that I just noticed is that the binaries you downloaded are for the x86 processors (ie 32bit) and you are running 64bit. Try the 64bit binaries if they're available.

I have little to no experience compiling ROOT on 64bit machines, but I'm guessing that you may have to softlink some libraries to fool ROOT into using the correct ones.

One final note:  to remove all traces of root from the repositories run:
```
sudo apt-get purge <root_packages>
```
Then try and recompile after untarring the source in a new directory.  I know that make clean and make distclean are supposed to reset everything, but root is notorious for odd quirks, and sometimes its easiest to start from the beginning.

---

### Post by rifak on 2009-05-03
ha, i got it! your mention of libtiff3 threw up a flag. I have libtiff4 (i guess its the newer version? i have no clue). but the error in root says that it cannot load libtiff.so.3 and rightly so considering i don't have libtiff3 on my computer. so i just simply copied the libtiff.so.4 to libtiff.so.3 and it seems to be working. a little sketchy, i agree but hey it seems to be working. thank you for your help and i may be posting back in the future so keep yours eyes out haha but seriously thanks

---

### Post by Catalyst2Death on 2009-05-09
ROOT is very quirky about these things.  Sometimes hacks like this work, and sometimes they don't.  If something blows up later on involving libtiff, you know where to go hunting first.

 - Catalyst

---

