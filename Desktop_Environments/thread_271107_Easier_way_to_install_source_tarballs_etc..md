---
title: "Easier way to install source tarballs etc."
date: 2006-10-04
forum: Desktop Environments
---

### Post by PacShady on 2006-10-04
Hey

After sifting through through the forums for a while, running searches etc, I'm wanting to find out if there is a nifty little program that, if I throw it a source tarball (like one you find on a website somewhere), it will configure, install, and take care of dependencies and all the other stuff it needs to install correctly?

I'm sick of all the problems I have trying to compile programs, for some reason I've never had much luck with it, and I try to avoid it if at all possible, preferring greatly to stick with debs. However, there are far too many programs that are out there that don't offer debs, only source packages, which must be compiled to use. But whenever I try to compile anything, it usually ends up in some kind of an error or another, even after trying to sift through the copious amount of text that make spits out at me, trying to install what I think are dependent packages required to compile whatever it is I'm trying to compile.

The closest thing I could find was apt-build, but if I'm not mistaken this relies on using source packages from repositories. I need something I can throw plain and simple tarballs at that I've downloaded from a website that can do all the compiling for me without me being thrown into dependency hell.

PLEASE tell me such a wonderous program exists!

'Shady

---

### Post by someguyouknow on 2006-10-04
I would like to know also although i highly, highly doubt it...

compiling from source isnt that bad though. most times when there is a problem, it can be easily found in the readMEs
but 8 times out of 10 its just a ./configure, make, make install.

---

### Post by PacShady on 2006-10-04
Sadly, it's just the opposite for me, 8 times out of 10 either the program simply won't install, or else it nearly breaks my system. 

It's not that I'm against the CONCEPT of compiling, I can see how it can be a powerful tool in making programs work better with a given system. However, the problem with hidden dependencies, tempremental config files and the risk of irreversible damage makes the source tarball a beast tameable only by someone with a university degree in 76 different computer programming languages! The format simply isn't uniform enough, it allows for far too many variables depending on what system one TRIES to install it on.

I'll always prefer deb files, but sometimes compiling from source is unavoidable. And for the average user who DOESN'T have a degree in quantum binary mechanics, I strongly believe that there MUST be an easier way than spending hours and hours trying to make a 20k program work properly!

'Shady

---

### Post by someguyouknow on 2006-10-04
lol what programs are you trying to install?
maybe it has to do with specific programs?
you do have build-essential right?

I am very much a noob but i have installed a few programs from source with little problems.

---

### Post by doobit on 2006-10-04
The configuration script is the key to the compilation process. When you run ./configure that script outputs everything (hopefully) you have to know to successfully make an install executable. Watch what comes out on the terminal when you run it. Scroll back through the output and you will see if and what the dependancies are and if you will be successful when you compile. If it looks for something that it needs for the compiled program to work, and can't find it, then it will tell you that and you have to go get it and install it ( a dev package or a language package, for example).

Almost every bit of source code out there has already been compiled as a .deb package however, so try to find that first, then you don't need to worry about compiling it your self.

---

### Post by public_void on 2006-10-04
If the ./configure fails it will usually tell you in the last 2-3 lines. Most the time it will say something along the lines of "xxxxxxxxx is missing". If so have a look in synaptic for the package. Most the time this works for all missing dependencies, otherwise you may have to hunt round for the missing one and, yes, compile that too.

---

### Post by dyous87 on 2006-10-04
I to must say that I've also had bad experiences with istalling from source and now I simply rely on .debs. I think it would be great if some type of automated script was written to automatically complie and take care of all the dependancies automatically. It would def allow for greater linux adaption and I think would also give people and easier time looking for software they need...

---

### Post by aidanr on 2006-10-04
well theres kompile for kde, which automatically extracts, configures, makes and installs but doesn't take care of dependencies, although when i was using it i found it worked about 50% of the time even though in most cases the dependencies were filled, because i needed to pass extra options to configure

---

### Post by dyous87 on 2006-10-04
that's interesting...and you're saying it didn't work veyr well anway?

---

### Post by aidanr on 2006-10-04
as far as i remeber the version i was using didn't let you add any options to ./configure so you'd have to do it in the terminal anyway, and the terminal was also faster anyway

this could have changed since though

---

### Post by dyous87 on 2006-10-04
ohh i see...hmm I think I program such as this would be great if it worked correctly and it was able to fetch dependancies from apt.

---

### Post by andb on 2006-10-04
Once or twice Ive had to edit the ./configure script to find what wasnt working, but that is really the exception, not the rule. Ive compilled all of what I concider non-standard apps, to keep up with latest versions. So that means well over 50 versions of various programs, and only had one or two problems. I do often look at the configure scripts before, just to really see what the options are, the defaults, and what may make problems. For example, as I have my own compiled kernel, I cant let scripts depend on kernel-header .deb packages. The advantage of compiling manually instead of a progam doing it is that you can deal with specialized cases. How would the program know all the options? The best, of course is to get the .deb package, as youve found.

Could you please post -specificaly- with which program sources you've had the problems? I, and Im sure others, would like to look into it for you. Maybe there is something that yuo cuold change about your system or the way you are doing it that could make it work better for you.

---

### Post by dyous87 on 2006-10-04
> **andb said:**
> Could you please post -specificaly- with which program sources you've had the problems? I, and Im sure others, would like to look into it for you. Maybe there is something that yuo cuold change about your system or the way you are doing it that could make it work better for you.

Well it's just stuff that I've tried in the past as I haven't really tried compiling and program since I switched over from Mandrake to Ubuntu about a years ago or so. I guess I'm just scared of it since I'm not really used to it. For example what happens if it breaks my system, or if i don't like the program how to I uninstall it. Also I'd have to keep track of the version myself to see if I need to upgrade it and if so how do I upgrade a program that I've compiled myself?? I'm pretty much a noob in this area lol.

---

### Post by cmost on 2006-10-04
When I was an avid KDE user, I swore by the use of Kompile.  Being a KDE application, i'm not sure if it's possible to utilize Kompile in Gnome, but considering that other KDE apps work fine, perhaps this one will too.  Kompile is a KDE interface for automatic execution of configurations, compilation and installation of source tarball.

The latest version is 0.3, and this is considered a testing release.  Don't be scared off by the low version number, however, I used this since version 0.1 without any problems.

The major innovation of version 0.3 is profiles system. Now Kompile always use a profile to perform an installation/uninstallation.
You can define a custom profile for install an application or use default profile to do it. If you use default profile, Kompile will
create a package's profile based on options specified in your default profile.
Some profiles options are:
- Source tarball backup for uninstallation
- Packages informations (name, version, release, license, description)
- Temporary decompression folder options
- Source configuration options (prefix, enable/disable warnings, enable disable libs such as Qtopia, etc.)
- Compiler options (c/c++/fortran compilers flags, executables, prerocessor flags,linker flags, etc.)
- Simple user (= non root) installation options
- Use checkinstall instead make install (and specify checkinstall options)

To learn more, please see here:
[http://www.kde-apps.org/content/show.php?content=30223](http://www.kde-apps.org/content/show.php?content=30223)

---

### Post by Ramses de Norre on 2006-10-04
One very good tool is auto-apt:```
sudo aptitude install auto-apt
sudo auto-apt update
sudo auto-apt updatedb
sudo auto-apt update-local
sudo auto-apt run ./configure
./configure
make
sudo make install
```

This will download all dependencies asked for by ./configure. The update commands can take a bit of time but are necessary for auto-apt to work correctely.

---

### Post by DougieFresh4U on 2006-10-04
Hi every one! I to am having problems with tar zip's. I tried following auto apt and I believe I made a mess   sorry for butting into your thread PacShady :confused:                                    dougie@DougiesToyBox:~$ sudo aptitude install auto-apt
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
dougie@DougiesToyBox:~$ sudo auto-apt update
Downloading [http://archive.ubuntu.com/ubuntu/dists/edgy](http://archive.ubuntu.com/ubuntu/dists/edgy) Contents-i386.gz ...
tail: Warning: "+number" syntax is deprecated, please use "-n +number"

put: 1775460 files,  2669250 entries
Downloading [http://archive.ubuntu.com/ubuntu/dists/edgy-security](http://archive.ubuntu.com/ubuntu/dists/edgy-security) Contents-i386.gz ...
tail: Warning: "+number" syntax is deprecated, please use "-n +number"

Downloading [http://archive.ubuntu.com/ubuntu/dists/edgy-updates](http://archive.ubuntu.com/ubuntu/dists/edgy-updates) Contents-i386.gz ...
tail: Warning: "+number" syntax is deprecated, please use "-n +number"

Downloading [http://archive.ubuntu.com/ubuntu/dists/edgy-backports](http://archive.ubuntu.com/ubuntu/dists/edgy-backports) Contents-i386.gz ...
tail: Warning: "+number" syntax is deprecated, please use "-n +number"

Downloading [http://archive.canonical.com/ubuntu/dists/dapper-commercial](http://archive.canonical.com/ubuntu/dists/dapper-commercial) Contents-i386.gz ...
tail: Warning: "+number" syntax is deprecated, please use "-n +number"
100%[====================================>] 680           --.--K/s             

15:24:35 (16.63 MB/s) - `archive.canonical.com_ubuntu_dists_dapper-commercial_Contents-i386.gz' saved [680/680]


Downloading [http://wine.lowvoice.nl/apt/dists/dapper](http://wine.lowvoice.nl/apt/dists/dapper) Contents-i386.gz ...
tail: Warning: "+number" syntax is deprecated, please use "-n +number"

put: 1778286 files,  2672285 entries done (188 sec)
dougie@DougiesToyBox:~$ sudo auto-apt updatedb
put: 1777487 files,  2671463 entries





put: 1778286 files,  2672285 entries done (68 sec)
dougie@DougiesToyBox:~$ sudo auto-apt update-local
local file list mode
put: 144620 files,  193308 entries done (33 sec)
dougie@DougiesToyBox:~$ sudo auto-apt run ./configure
Entering auto-apt mode: ./configure
Exit the command to leave auto-apt mode.
/usr/bin/auto-apt: line 115: type: ./configure: not found
E: Exec ./configure failed, auto-apt failed
dougie@DougiesToyBox:~$ ./configure
bash: ./configure: No such file or directory
dougie@DougiesToyBox:~$ make
make: *** No targets specified and no makefile found.  Stop.
dougie@DougiesToyBox:~$ sudo make install
make: *** No rule to make target `install'.  Stop.
dougie@DougiesToyBox:~$ sudo make install

---

