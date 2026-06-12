---
title: "how exactly are &quot;executables&quot; managed in linux"
date: 2009-02-07
forum: General Help
---

### Post by aaronLund on 2009-02-07
I'm using 8.10 although I'm not too sure it really matters for my question....

The reason I'm asking is this:

I installed a trial version of Komodo a while back and although I thought that I have uninstalled it, apparently, I have not.

I can still open it but it seems more than broken (probably due to the fact that I searched for any references to it and trashed them.......not good, I know).  

If I were in Windows, I could find my 'exe' file in C://program files but I don't see how this is managed in linux.  To me, it doesn't seem like there is a set folder for the linux 'exe' (I'm aware that linux doesn't use 'exe' files, by the way) file.  I've found stuff in usr/lib, user/bin, etc.

This really makes uninstalling anything pretty difficult.  As well as tracking something down.

So what are the conventions?  Is there a way to make things like this easier?  Say, like, "I put all my executable files in XXXXX because that way I can keep track of them".

Thanks for any advice.

---

### Post by Alterax on 2009-02-07
That's the real beauty of using package managers (like synaptic) rather than compiling from source.  Hindsight is 20/20 though.  First, let's start with where binaries are usually kept:

Linux binaries are usually kept in three places:  /sbin has the system executables.  /bin is usually system tools shared by all users.  /usr/bin usually contains programs.  /usr/local/bin is usually those that are installed from source, but that's not exactly standardized.

Could you tell me how you installed this program?  Was it a .deb package?  An .rpm that you had to convert?  A .tar.gz that you had to install with "make install"?  Knowing this can make it much easier to track down the rogue files and dispensing with them.

---

### Post by kayvortex on 2009-02-07
Basically, the convention is that system programs are installed in subdirectories of /usr, and programs that you compile or install yourself are installed in subdirectories of /usr/local; the thinking being that the two should be separate in case the latter cause problems. (Edit: It's a bit more complicated than this depending on the nature of the program: fundamental programs are installed to /bin, maintenance programs are installed in "sbin" installed of "bin" directories, some programs may include scripts in /etc, or even install to /opt...but this is the basic convention).

So, if you installed komodo yourself, look in /usr/local/bin for your binary (executable) files, /usr/local/share for any docs etc.

However, if you did install komodo yourself, then the installation programs and scripts should have provided you with a way of uninstalling the program as well. How did you install komodo?

---

### Post by aaronLund on 2009-02-07
First, thanks for the replies.

Second, please forgive the "noobishness" of my replies to your questions.  (ugh...here goes)

I'm pretty sure I installed komodo by downloading the tar file and then...somehow making some file in there executable???  (something with chmod+x......it's been a while).

That brings me to other questions though:  
-What is the difference between "compiling" a program yourself?
-Installing via synaptic?
-Installing via apt-get?
-Installing via SVN or the like?
-What is a .deb file and how does it pertain to installing software vs., say, apt-get?

Thanks again, everyone.

---

### Post by jocko on 2009-02-07
[This wikipedia article]("http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard") explains where you find different files in the filesystem.

In short: executable files are usually found in folders named "bin" or "sbin" (/bin, /sbin, /usr/bin, /usr/sbin, /usr/local/bin, /usr/local/sbin, ...).

But why are you uninstalling by finding and deleting the files?
Anything installed through synaptic can be removed from synaptic as well.

If you have installed anything from source code by running this command:
```
sudo make install
```
It can usually be removed by running this command from the source directory:
```
sudo make uninstall
```
And most things that are installed by an installer program can usually be uninstalled using the same installer program (but you may need to find out the specific command to run yourself).

---

### Post by beyboo on 2009-02-07
since you are sure that it was named komodo, try a system level search like this

from gnome-terminal

cd /
sudo find | grep komodo

This will find all the komodo files all over, open another terminal and check out each file which gets thrown up by search.

---

### Post by kayvortex on 2009-02-07
To compile a program means to create it from scratch from simple text commands instructing how the program should work. This is what people are on about when they talk about "source code": the source code is just those text files. Virtually every program is compiled from text because it easier than creating binaries directly (what *nix people called .exe files), but often when you download/install programs this has already been done for you.

Apt-get essentially derives from the way binary (.exe) files work. Basically, if two programs share some functionality (i.e. both programs could, say, copy one file from one place to another in exactly the same way), then that particular bit can be cut from both executables and just stored in one place where both programs have access to it. This saves space on your system because that bit of your executable file is not duplicated separately on both binaries. This is what libraries are: bits of code that can be used by another other program to do certain common tasks. However, these libraries then need to be "managed": since the individual programs don't contain that code themselves, they need tell the system, "Hey, I need this particular library to work." Also, since the programs don't delete the library after they themselves have been removed (because other programs might need that library), what happens when *all* the programs that need that library are removed? That library is now not being used, but is still on your system taking up space. Apt-get is, essentially, this system that is needed to manage your libraries. What it allows you to do is simply say, "install this program," and then it will automatically configure and install your program, install all the libraries it needs etc. and make sure that it will work. It also allows you to say, "uninstall this program," and it will remove all the files that it installed automatically and remove any unused libraries.
Long story short, apt-get is a program that manages the installation and removal of programs because there's a lot of subtleties involved.

.deb files are just files used by apt-get to install what's in that .deb file. They contain the things to install (obviously!), but also instructions on where to install them and what other programs/libraries are needed in order for the program to work. They're very useful because if you have a .deb file, you then have a way to let apt-get do all the dirty work for you.

SVN is basically just a place to acquire programs, be they in the form of .deb files, or source code that you have to compile and install yourself.

---

### Post by jocko on 2009-02-07
> **aaronLund said:**
> That brings me to other questions though:  
-What is the difference between "compiling" a program yourself?
-Installing via synaptic?
-Installing via apt-get?
-Installing via SVN or the like?
-What is a .deb file and how does it pertain to installing software vs., say, apt-get?

Compiling usually means you convert the source code of a program into binary files, which can be installed and run on your computer. This is complicated, but is usually simplified by a number scripts that automates parts of the process so the user only have to run a few commands.

Synaptic, apt-get, aptitude, adept *et al* are different front ends for the dpkg system (**d**ebian **p**ac**k**a**g**e management). They connect to repositories which contain **.deb** files and allow you to download, install, uninstall and upgrade packages as well as show information about the available packages. They also keep track of which packages contain which files, which packages depend on which other packages and which packages are in conflict with which other packages. So when you install anything from a .deb file, the package manager will automatically try to solve all dependencies or let you know what needs to be installed or uninstalled to be able to continue.

Subversion (svn), git, bazaar, mercurial *et al* are revision control systems which enables developers to upload their code and keep track of all changes, and users to download snapshots of the source code to compile and install on their own machines.

If you install anything from source code, you have to find out yourself which packages you need to install in order to be able to compile the code, and which you need in order to run the program once it's installed. You will also need to make sure you keep those dependencies installed and don't install anything that will overwrite files from what you installed from source, as there is nothing that keeps track of the dependencies (and the dpkg system is not aware of things that are installed in any other way).

---

### Post by kayvortex on 2009-02-07
Right, I've downloaded Komodo version 5.0.3 (which is probably not the version you have, but still) and it uses python to install. Now, (although I don't know python) I think it will simply install to a directory from where you ran the install script. So, do you have a directory called Komodo-... on your home or Desktop directory, or wherever it was that you downloaded it to?

---

