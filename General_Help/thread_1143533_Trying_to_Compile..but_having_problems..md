---
title: "Trying to Compile..but having problems."
date: 2009-04-30
forum: General Help
---

### Post by snorbens on 2009-04-30
Hi,
I am for the first time trying to compile a program.
Maybe I am trying to run before I can even crawl let alone walk:confused:

This is what I am doing and the answers I get.

Am I doing something wrong or is there maybe files missing from the source file that I downloaded.

```
mervyn@mervyn-laptop:~$ cd /home/mervyn/fwbackups-1.43.2
mervyn@mervyn-laptop:~/fwbackups-1.43.2$ './configure'
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for python... /usr/bin/python
checking for python version... 2.6
checking for python platform... linux2
checking for python script directory... /usr/lib/python2.6/dist-packages
checking for python extension module directory... /usr/lib/python2.6/dist-packages
checking whether ln -s works... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
./configure: line 2668: AM_GLIB_GNU_GETTEXT: command not found
./configure: line 2669: AC_PROG_INTLTOOL: command not found
checking whether ln -s works... yes
checking for python version... (cached) 2.6
checking for python platform... (cached) linux2
checking for python script directory... (cached) /usr/lib/python2.6/dist-packages
checking for python extension module directory... (cached) /usr/lib/python2.6/dist-packages
configure: creating ./config.status
config.status: creating bin/Makefile
config.status: creating bin/fwbackups
config.status: WARNING:  'bin/fwbackups.in' seems to ignore the --datarootdir setting
config.status: creating help/Makefile
config.status: creating pixmaps/Makefile
config.status: creating po/Makefile.in
config.status: creating src/Makefile
config.status: creating src/fwbackups/Makefile
config.status: creating src/fwbackups/__init__.py
config.status: creating src/fwbackups/const.py
config.status: WARNING:  'src/fwbackups/const.py.in' seems to ignore the --datarootdir setting
config.status: creating Makefile
config.status: creating fwbackups.spec
mervyn@mervyn-laptop:~/fwbackups-1.43.2$ 'make'
Making all in bin
make[1]: Entering directory `/home/mervyn/fwbackups-1.43.2/bin'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/mervyn/fwbackups-1.43.2/bin'
Making all in help
make[1]: Entering directory `/home/mervyn/fwbackups-1.43.2/help'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/mervyn/fwbackups-1.43.2/help'
Making all in po
make[1]: Entering directory `/home/mervyn/fwbackups-1.43.2/po'
make[1]: *** No rule to make target `all'. Stop.
make[1]: Leaving directory `/home/mervyn/fwbackups-1.43.2/po'
make: *** [all-recursive] Error 1
mervyn@mervyn-laptop:~/fwbackups-1.43.2$ 

```

Thanks for any help. Maybe I am too old, or brain dead, to try this stuff, but I am enjoying computing far more than I ever did with Windows. At least this OS allows me to try and use my grey matter.

---

### Post by mb_webguy on 2009-04-30
I don't think it should neccessarily matter, but why do you have "./configure" in single-quotes?

My guess would be you don't have some necessary dependencies, though if that's the case I don't know why it got so far as to create a makefile.  Make sure you have the build-essential and (for this program) gettext packages.

---

### Post by snorbens on 2009-04-30
> **mb_webguy said:**
> I don't think it should neccessarily matter, but why do you have "./configure" in single-quotes?

My guess would be you don't have some necessary dependencies, though if that's the case I don't know why it got so far as to create a makefile.  Make sure you have the build-essential and (for this program) gettext packages.

Thanks..........I put configure in the single quotes as that is what the readme text suggested.

I will maybe download the file again... I do not know much about compiling as I said. I do not want to just give up, but without much understanding, I may have to. It may be that I am to silver haired to understand, or just too slow to learn.:(

---

### Post by mb_webguy on 2009-04-30
Compiling code can be very simple, but it can at times also be very frustrating.  If you have all of the dependencies satisfied, compiling software from source is as simple as:```
./configure
make sudo make install
```Or, to make it easier to manage the software:```
./configure
make
sudo checkinstall
```You'll need to install the checkinstall package for that one, but IMO it's worth it.  Checkinstall creates a deb package for the software and adds it to the package database so that you can manage it with Synaptic or other package managers.  But whether you use "sudo make install" or "sudo checkinstall" to install the compiled software, *if* you've satisfied the dependencies for the software you're trying to compile, it's as simple as those three commands in the terminal.

The biggest frustration in compiling code from source is in satisfying those dependencies.  Examining the output of ./configure will indicate what dependencies aren't currently satisfied, but not necessarily in a way that's easy to track down.  And if software A (which you're trying to compile) depends on software B, and software B is also only available as source code, then you'll have to compile it first.  And of course B might depend on C, which might depend on D, and so on.  

That's why your first course of action when installing software should always be to check the repositories.  Your second should be to check for a PPA that provides the software, or a website that offers the software in a prepackaged form (such as a deb).  Compiling should always be a last resort.  Unfortunately, I've searched all over the place, and can't find a more convenient source for fwbackups.

---

### Post by snorbens on 2009-04-30
Thanks for that.

It may prove impossible for me....On the fwbackups page it says to install QT and CMake both of which I have downloaded.

I used apt-get install cmake which installed it ok, and also got QT from the repos. 

When I tried to use cmake it told me that there was no cmakelists in fwbackups. 

But I will not give up yet as I would love to learn about all of this.


Cheers

---

### Post by snorbens on 2009-04-30
Update:

Well it appeared that I managed to install the program, with it adding an icon to systems/preferences....But when I click on the icon an error box opens.

It states  Could not Launch fwbackups

                            Failed to execute child process "/usr/bin/fwbackups" (No such file or directory)

There appears to be a backups shell script in /home/mervyn/fwbackups-1.43.2/bin.

If this is the correct file:confused: how can I re-install and correct this?

Thanks

---

### Post by snorbens on 2009-04-30
Update 2:

I managed to remove the fwbackup program and icon.

I re-compiled using these instructions and checkinstall :[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

Now I have supposedly installed and have an icon on the system/preferences and when I click on it...it does absolutely nothing.

I do not know now whether to persevere or whether I am still doing somethink wrong or the source code may be faulty.

Cheers

---

### Post by paradigm2 on 2009-04-30
> **snorbens said:**
> Update 2:

I managed to remove the fwbackup program and icon.

I re-compiled using these instructions and checkinstall :[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

Now I have supposedly installed and have an icon on the system/preferences and when I click on it...it does absolutely nothing.

I do not know now whether to persevere or whether I am still doing somethink wrong or the source code may be faulty.

Cheers

Find what command the menu is trying to execute and then execute that command from the terminal to see what is going on.

---

### Post by snorbens on 2009-04-30
> **paradigm2 said:**
> Find what command the menu is trying to execute and then execute that command from the terminal to see what is going on.

This might sound a little stupid (I am a complete newbie at this)but how would I find out which command it was trying to execute??

I did type the name of the program fwbackups in the terminal and it came up with this.

```
mervyn@mervyn-laptop:~$ fwbackups
Traceback (most recent call last):
  File "/usr/share/fwbackups/fwbackups-runapp.pyw", line 34, in <module>
    from fwbackups.const import *
ImportError: No module named fwbackups.const
mervyn@mervyn-laptop:~$ 
```

---

### Post by doug1212 on 2009-04-30
Hi,
Out of curiosity I had a go at building fwbackups and i have it installed but as yet have not used it in anger.

QT development files have to be installed and the dependencies:
plus python-paramiko and python-crypto from the repos.

In the the readme file it says that the configure needs install options:

```
 ./configure --prefix=/usr
```

run make:

```
make
```

To have a reference to the application appear in synaptic I use checkinstall:

```
sudo checkinstall make install
```

or:

```
sudo make install
```

Good luck

Doug.

---

### Post by snorbens on 2009-04-30
> **doug1212 said:**
> Hi,
Out of curiosity I had a go at building fwbackups and i have it installed but as yet have not used it in anger.

QT development files have to be installed and the dependencies:
plus python-paramiko and python-crypto from the repos.

In the the readme file it says that the configure needs install options:

```
 ./configure --prefix=/usr
```

run make:

```
make
```

To have a reference to the application appear in synaptic I use checkinstall:

```
sudo checkinstall make install
```

or:

```
sudo make install
```

Good luck

Doug.

I installed using the prefix=user but I have just found out where it is!!
It is in /usr/local/src/fwbackups-1.43.2/bin  ?? I wonder if I could just create a Desktop icon with that command line??

I did make sure that I had QT installed but have not checked the others you suggest...the readme file did not suggest those to me ...just QT and cmake...cmake did absolutely nothing. I will keep trying and thank you

---

### Post by snorbens on 2009-04-30
Hi,

Just to make sure I am doing this right...I am going to the directory where I have the file.
```
mervyn@mervyn-laptop:~$ cd usr/local/src/fwbackups-1.43.2
bash: cd: usr/local/src/fwbackups-1.43.2: No such file or directory
mervyn@mervyn-laptop:~$ cd /usr/local/src/fwbackups-1.43.2
mervyn@mervyn-laptop:/usr/local/src/fwbackups-1.43.2$ 
```


then  ```
./configure --prefix=/usr

```
                  

then  ```
make[/CODE

then  [CODE]checkinstall make install  
```           


the message after all that is

 Done. The new package has been installed and saved to

 /usr/local/src/fwbackups-1.43.2/fwbackups_1.43.2-1_i386.deb

 You can remove it from your system anytime using: 

      dpkg -r fwbackups

And after all that the icon points to /usr/bin/fwbackups but of course it is not there.

Cheers

---

### Post by snorbens on 2009-04-30
Update:

Well it is now installed at /usr/bin and the icon command is pointing to it correctly but it just does not work..

Click on the icon...nothing have tried to run it from the bin directly and nothing??

Maybe it is just not going to work for me!! Any advice would be welcome.

Thanks

---

### Post by doug1212 on 2009-04-30
What error messages, if any are shown when you start fwbackups from the terminal.
Doug.

---

### Post by doug1212 on 2009-04-30
Here is a list of dependencies taken from the source code:
where it says build requires I'm presuming that the development files are also needed.

BuildRequires:     desktop-file-utils
BuildRequires:     gettext
BuildRequires:     intltool, automake
BuildRequires:     libxml2
BuildRequires:     python-devel >= 2.4
BuildRequires:     scrollkeeper
BuildRequires:     gnome-doc-utils
Requires:          /usr/bin/crontab
Requires:          tar, rsync
Requires:          notify-python, gnome-python2
Requires:          pygtk2, pygtk2-libglade
Requires:          python >= 2.4
Requires:          python-paramiko
Requires(post):    scrollkeeper
Requires(postun):  scrollkeeper

---

### Post by Arndt on 2009-04-30
> **snorbens said:**
> Thanks..........I put configure in the single quotes as that is what the readme text suggested.


Sometimes quotes (double or single) are used to separate computer input or output from the other text, and sometimes they actually belong to the input or output. It may be hard to identify which is the case, if there are no hints like different fonts, especially if the instructions are sloppily written.

In this case, I guess the quotes were of the first kind. It happened to work the same way as without them because in the shell, quotes are used to enclose a piece of text and make it one single unit (a command, or a command argument), and ./configure already is one unit anyway, since it contains no spaces or characters which are special to the shell command line.

---

### Post by snorbens on 2009-05-01
Thanks everybody. Am away for a day or two will check everything out when I get back.

Cheers

---

### Post by snorbens on 2009-05-01
> **doug1212 said:**
> What error messages, if any are shown when you start fwbackups from the terminal.
Doug.

Hi doug,

This is the error message from the terminal:

```
mervyn@mervyn-laptop:~$ fwbackups
Traceback (most recent call last):
  File "/usr/share/fwbackups/fwbackups-runapp.pyw", line 34, in <module>
    from fwbackups.const import *
ImportError: No module named fwbackups.const
mervyn@mervyn-laptop:~$ 
```

---

### Post by doug1212 on 2009-05-01
Not much help I'm afraid but that does look like a build error.

This looks like a similar error message although it's on 1.43.3rc1 with a possible slution:

[HTML]https://bugzilla.redhat.com/show_bug.cgi?id=496828[/HTML]

Suppose it may be possible to use "alien" to convert the RPM to a deb.

pity your not on Hardy or you could try my checkinstall deb file.

Doug.

---

### Post by snorbens on 2009-05-02
> **doug1212 said:**
> Not much help I'm afraid but that does look like a build error.

This looks like a similar error message although it's on 1.43.3rc1 with a possible slution:

[HTML]https://bugzilla.redhat.com/show_bug.cgi?id=496828[/HTML]

Suppose it may be possible to use "alien" to convert the RPM to a deb.

pity your not on Hardy or you could try my checkinstall deb file.

Doug.

Yes a build error looks likely...I think I will give up on it.

I think I have spent enough time on it and I thank everybody for their help and advice.

Cheers

---

### Post by Beno1 on 2009-05-03
Hi,

In order to run fwbackups on 9.04 try:

1. Download and compile:
./configure --prefix=/usr --datadir=/usr/share
make
checkinstall

2. Install packages:
- python-glade2
- python-paramiko
- librsvg2-common

3. Run as:
PYTHONPATH=/usr/lib/python2.6/site-packages/:$PYTHONPATH fwbackups

at least it worked in my case...

Beno

---

### Post by doug1212 on 2009-05-03
@Beno1
Firstly welcome to the forums and thanks for explaining how you installed fwbackups on Jaunty.

The developer suggested this as a possible solution on bugzilla.redhat, glad it works for you :)

Doug.

---

### Post by snorbens on 2009-05-04
> **Beno1 said:**
> Hi,

In order to run fwbackups on 9.04 try:

1. Download and compile:
./configure --prefix=/usr --datadir=/usr/share
make
checkinstall

2. Install packages:
- python-glade2
- python-paramiko
- librsvg2-common

3. Run as:
PYTHONPATH=/usr/lib/python2.6/site-packages/:$PYTHONPATH fwbackups


at least it worked in my case...

Beno

Hi Beno,

Thanks Beno that worked fine. Once again thanks very much.

Snorbens

---

### Post by BillyBob721 on 2009-06-20
Instead of using:

"3. Run as:
PYTHONPATH=/usr/lib/python2.6/site-packages/:$PYTHONPATH fwbackups"

Simply edit .bashrc in your home directory to reflect:

export PYTHONPATH=/usr/lib/python2.6/site-packages/

Then from your cli just use fwbackups OR add the menu item from within 
System > Preferences > Main Menu > (anywhere you see fit)
:D

---

### Post by chmacka on 2009-07-27
Whatever I try I can't get it to work. I always get:

```
Traceback (most recent call last):
  File "/usr/local/share/fwbackups/fwbackups-runapp.pyw", line 34, in <module>
    from fwbackups.const import *
ImportError: No module named fwbackups.const

```

So how I can uninstall it?

---

### Post by firewing1 on 2009-07-27
> **chmacka said:**
> Whatever I try I can't get it to work. I always get:

```
Traceback (most recent call last):
  File "/usr/local/share/fwbackups/fwbackups-runapp.pyw", line 34, in <module>
    from fwbackups.const import *
ImportError: No module named fwbackups.const

```

So how I can uninstall it?
Try running this from the source directory (where you compiled fwbackups)```

make uninstall
```

I wrote the autotools script for fwbackups with Fedora in mind, but I think Ubuntu uses some different variables - I'm going to fix this for 1.43.3rc3. In the mean time, using:```
./configure --prefix=/usr --datadir=/usr/share
```should work around the problem for now.

---

### Post by chmacka on 2009-07-28
> **firewing1 said:**
> Try running this from the source directory (where you compiled fwbackups)```

make uninstall
```I get this:

```
Making uninstall in bin
make[1]: Entering directory `/home/chmacka/Desktop/Downloads/fwbackups/fwbackups-1.43.2-1.fc9.src/fwbackups-1.43.2/bin'
rm -f /usr/bin/fwbackups
rm: cannot remove `/usr/bin/fwbackups': Is a directory
make[1]: *** [uninstall-local] Error 1
make[1]: Leaving directory `/home/chmacka/Desktop/Downloads/fwbackups/fwbackups-1.43.2-1.fc9.src/fwbackups-1.43.2/bin'
make: *** [uninstall-recursive] Error 1

```> I wrote the autotools script for fwbackups with Fedora in mind, but I think Ubuntu uses some different variables - I'm going to fix this for 1.43.3rc3. In the mean time, using:```
./configure --prefix=/usr --datadir=/usr/share
```should work around the problem for now.This is what I get with *./configure --prefix=/usr --datadir=/usr/share*:

```
chmacka@chmacka-desktop:~/Desktop/Downloads/fwbackups/fwbackups-1.43.2-1.fc9.src/fwbackups-1.43.2$ ./configure --prefix=/usr --datadir=/usr/share
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for python... /usr/bin/python
checking for python version... 2.6
checking for python platform... linux2
checking for python script directory... ${prefix}/lib/python2.6/site-packages
checking for python extension module directory... ${exec_prefix}/lib/python2.6/site-packages
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... none
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking locale.h usability... yes
checking locale.h presence... yes
checking for locale.h... yes
checking for LC_MESSAGES... yes
checking libintl.h usability... yes
checking libintl.h presence... yes
checking for libintl.h... yes
checking for ngettext in libc... yes
checking for dgettext in libc... yes
checking for bind_textdomain_codeset... yes
checking for msgfmt... /usr/bin/msgfmt
checking for dcgettext... yes
checking if msgfmt accepts -c... yes
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
checking for xgettext... (cached) /usr/bin/xgettext
checking for msgmerge... /usr/bin/msgmerge
checking for msgfmt... (cached) /usr/bin/msgfmt
checking for perl... /usr/bin/perl
checking for XML::Parser... ok
checking whether ln -s works... yes
checking for python version... (cached) 2.6
checking for python platform... (cached) linux2
checking for python script directory... (cached) ${prefix}/lib/python2.6/site-packages
checking for python extension module directory... (cached) ${exec_prefix}/lib/python2.6/site-packages
configure: creating ./config.status
config.status: creating bin/Makefile
config.status: creating bin/fwbackups
config.status: WARNING:  bin/fwbackups.in seems to ignore the --datarootdir setting
config.status: creating help/Makefile
config.status: creating pixmaps/Makefile
config.status: creating po/Makefile.in
config.status: creating src/Makefile
config.status: creating src/fwbackups/Makefile
config.status: creating src/fwbackups/__init__.py
config.status: creating src/fwbackups/const.py
config.status: WARNING:  src/fwbackups/const.py.in seems to ignore the --datarootdir setting
config.status: creating Makefile
config.status: creating fwbackups.spec
config.status: executing depfiles commands
config.status: executing default-1 commands
./config.status: line 1025: po/Makefile: Permission denied
config.status: executing intltool commands
config.status: executing po/stamp-it commands
chmacka@chmacka-desktop:~/Desktop/Downloads/fwbackups/fwbackups-1.43.2-1.fc9.src/fwbackups-1.43.2$ make
Making all in bin
make[1]: Entering directory `/home/chmacka/Desktop/Downloads/fwbackups/fwbackups-1.43.2-1.fc9.src/fwbackups-1.43.2/bin'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/chmacka/Desktop/Downloads/fwbackups/fwbackups-1.43.2-1.fc9.src/fwbackups-1.43.2/bin'
Making all in help
make[1]: Entering directory `/home/chmacka/Desktop/Downloads/fwbackups/fwbackups-1.43.2-1.fc9.src/fwbackups-1.43.2/help'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/chmacka/Desktop/Downloads/fwbackups/fwbackups-1.43.2-1.fc9.src/fwbackups-1.43.2/help'
Making all in po
make[1]: Entering directory `/home/chmacka/Desktop/Downloads/fwbackups/fwbackups-1.43.2-1.fc9.src/fwbackups-1.43.2/po'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/chmacka/Desktop/Downloads/fwbackups/fwbackups-1.43.2-1.fc9.src/fwbackups-1.43.2/po'
Making all in pixmaps
make[1]: Entering directory `/home/chmacka/Desktop/Downloads/fwbackups/fwbackups-1.43.2-1.fc9.src/fwbackups-1.43.2/pixmaps'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/chmacka/Desktop/Downloads/fwbackups/fwbackups-1.43.2-1.fc9.src/fwbackups-1.43.2/pixmaps'
Making all in src
make[1]: Entering directory `/home/chmacka/Desktop/Downloads/fwbackups/fwbackups-1.43.2-1.fc9.src/fwbackups-1.43.2/src'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/chmacka/Desktop/Downloads/fwbackups/fwbackups-1.43.2-1.fc9.src/fwbackups-1.43.2/src'
Making all in src/fwbackups
make[1]: Entering directory `/home/chmacka/Desktop/Downloads/fwbackups/fwbackups-1.43.2-1.fc9.src/fwbackups-1.43.2/src/fwbackups'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/chmacka/Desktop/Downloads/fwbackups/fwbackups-1.43.2-1.fc9.src/fwbackups-1.43.2/src/fwbackups'
make[1]: Entering directory `/home/chmacka/Desktop/Downloads/fwbackups/fwbackups-1.43.2-1.fc9.src/fwbackups-1.43.2'
make[1]: Nothing to be done for `all-am'.
make[1]: Leaving directory `/home/chmacka/Desktop/Downloads/fwbackups/fwbackups-1.43.2-1.fc9.src/fwbackups-1.43.2'
chmacka@chmacka-desktop:~/Desktop/Downloads/fwbackups/fwbackups-1.43.2-1.fc9.src/fwbackups-1.43.2$ make install
Making install in bin
make[1]: Entering directory `/home/chmacka/Desktop/Downloads/fwbackups/fwbackups-1.43.2-1.fc9.src/fwbackups-1.43.2/bin'
make[2]: Entering directory `/home/chmacka/Desktop/Downloads/fwbackups/fwbackups-1.43.2-1.fc9.src/fwbackups-1.43.2/bin'
make[2]: Nothing to be done for `install-exec-am'.
/bin/bash /home/chmacka/Desktop/Downloads/fwbackups/fwbackups-1.43.2-1.fc9.src/fwbackups-1.43.2/install-sh -d /usr/bin
/usr/bin/install -c -m 755 fwbackups /usr/bin/fwbackups
/usr/bin/install: cannot remove `/usr/bin/fwbackups/fwbackups': Permission denied
make[2]: *** [install-data-local] Error 1
make[2]: Leaving directory `/home/chmacka/Desktop/Downloads/fwbackups/fwbackups-1.43.2-1.fc9.src/fwbackups-1.43.2/bin'
make[1]: *** [install-am] Error 2
make[1]: Leaving directory `/home/chmacka/Desktop/Downloads/fwbackups/fwbackups-1.43.2-1.fc9.src/fwbackups-1.43.2/bin'
make: *** [install-recursive] Error 1
chmacka@chmacka-desktop:~/Desktop/Downloads/fwbackups/fwbackups-1.43.2-1.fc9.src/fwbackups-1.43.2$ 

```

---

### Post by firewing1 on 2009-07-28
Since you're installing to your system (not a local directory in your home), you need to run as root - try prefixing make uninstall and make install with "sudo":```

sudo make uninstall
./configure --prefix=/usr --datadir=/usr/share
make
sudo make install
```

---

### Post by chmacka on 2009-07-28
I already tried with sudo. Same thing happens:

```
chmacka@chmacka-desktop:~$ cd /home/chmacka/Desktop/Downloads/fwbackups/fwbackups-1.43.2-1.fc9.src/fwbackups-1.43.2
chmacka@chmacka-desktop:~/Desktop/Downloads/fwbackups/fwbackups-1.43.2-1.fc9.src/fwbackups-1.43.2$ sudo make uninstall
[sudo] password for chmacka: 
Making uninstall in bin
make[1]: Entering directory `/home/chmacka/Desktop/Downloads/fwbackups/fwbackups-1.43.2-1.fc9.src/fwbackups-1.43.2/bin'
rm -f /usr/bin/fwbackups
rm: cannot remove `/usr/bin/fwbackups': Is a directory
make[1]: *** [uninstall-local] Error 1
make[1]: Leaving directory `/home/chmacka/Desktop/Downloads/fwbackups/fwbackups-1.43.2-1.fc9.src/fwbackups-1.43.2/bin'
make: *** [uninstall-recursive] Error 1
chmacka@chmacka-desktop:~/Desktop/Downloads/fwbackups/fwbackups-1.43.2-1.fc9.src/fwbackups-1.43.2$ ./configure --prefix=/usr --datadir=/usr/share
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for python... /usr/bin/python
checking for python version... 2.6
checking for python platform... linux2
checking for python script directory... ${prefix}/lib/python2.6/site-packages
checking for python extension module directory... ${exec_prefix}/lib/python2.6/site-packages
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... none
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking locale.h usability... yes
checking locale.h presence... yes
checking for locale.h... yes
checking for LC_MESSAGES... yes
checking libintl.h usability... yes
checking libintl.h presence... yes
checking for libintl.h... yes
checking for ngettext in libc... yes
checking for dgettext in libc... yes
checking for bind_textdomain_codeset... yes
checking for msgfmt... /usr/bin/msgfmt
checking for dcgettext... yes
checking if msgfmt accepts -c... yes
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
checking for xgettext... (cached) /usr/bin/xgettext
checking for msgmerge... /usr/bin/msgmerge
checking for msgfmt... (cached) /usr/bin/msgfmt
checking for perl... /usr/bin/perl
checking for XML::Parser... ok
checking whether ln -s works... yes
checking for python version... (cached) 2.6
checking for python platform... (cached) linux2
checking for python script directory... (cached) ${prefix}/lib/python2.6/site-packages
checking for python extension module directory... (cached) ${exec_prefix}/lib/python2.6/site-packages
configure: creating ./config.status
config.status: creating bin/Makefile
config.status: creating bin/fwbackups
config.status: WARNING:  bin/fwbackups.in seems to ignore the --datarootdir setting
config.status: creating help/Makefile
config.status: creating pixmaps/Makefile
config.status: creating po/Makefile.in
config.status: creating src/Makefile
config.status: creating src/fwbackups/Makefile
config.status: creating src/fwbackups/__init__.py
config.status: creating src/fwbackups/const.py
config.status: WARNING:  src/fwbackups/const.py.in seems to ignore the --datarootdir setting
config.status: creating Makefile
config.status: creating fwbackups.spec
config.status: executing depfiles commands
config.status: executing default-1 commands
config.status: executing intltool commands
config.status: executing po/stamp-it commands
chmacka@chmacka-desktop:~/Desktop/Downloads/fwbackups/fwbackups-1.43.2-1.fc9.src/fwbackups-1.43.2$ make
Making all in bin
make[1]: Entering directory `/home/chmacka/Desktop/Downloads/fwbackups/fwbackups-1.43.2-1.fc9.src/fwbackups-1.43.2/bin'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/chmacka/Desktop/Downloads/fwbackups/fwbackups-1.43.2-1.fc9.src/fwbackups-1.43.2/bin'
Making all in help
make[1]: Entering directory `/home/chmacka/Desktop/Downloads/fwbackups/fwbackups-1.43.2-1.fc9.src/fwbackups-1.43.2/help'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/chmacka/Desktop/Downloads/fwbackups/fwbackups-1.43.2-1.fc9.src/fwbackups-1.43.2/help'
Making all in po
make[1]: Entering directory `/home/chmacka/Desktop/Downloads/fwbackups/fwbackups-1.43.2-1.fc9.src/fwbackups-1.43.2/po'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/chmacka/Desktop/Downloads/fwbackups/fwbackups-1.43.2-1.fc9.src/fwbackups-1.43.2/po'
Making all in pixmaps
make[1]: Entering directory `/home/chmacka/Desktop/Downloads/fwbackups/fwbackups-1.43.2-1.fc9.src/fwbackups-1.43.2/pixmaps'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/chmacka/Desktop/Downloads/fwbackups/fwbackups-1.43.2-1.fc9.src/fwbackups-1.43.2/pixmaps'
Making all in src
make[1]: Entering directory `/home/chmacka/Desktop/Downloads/fwbackups/fwbackups-1.43.2-1.fc9.src/fwbackups-1.43.2/src'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/chmacka/Desktop/Downloads/fwbackups/fwbackups-1.43.2-1.fc9.src/fwbackups-1.43.2/src'
Making all in src/fwbackups
make[1]: Entering directory `/home/chmacka/Desktop/Downloads/fwbackups/fwbackups-1.43.2-1.fc9.src/fwbackups-1.43.2/src/fwbackups'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/chmacka/Desktop/Downloads/fwbackups/fwbackups-1.43.2-1.fc9.src/fwbackups-1.43.2/src/fwbackups'
make[1]: Entering directory `/home/chmacka/Desktop/Downloads/fwbackups/fwbackups-1.43.2-1.fc9.src/fwbackups-1.43.2'
make[1]: Nothing to be done for `all-am'.
make[1]: Leaving directory `/home/chmacka/Desktop/Downloads/fwbackups/fwbackups-1.43.2-1.fc9.src/fwbackups-1.43.2'
chmacka@chmacka-desktop:~/Desktop/Downloads/fwbackups/fwbackups-1.43.2-1.fc9.src/fwbackups-1.43.2$ sudo make install
Making install in bin
make[1]: Entering directory `/home/chmacka/Desktop/Downloads/fwbackups/fwbackups-1.43.2-1.fc9.src/fwbackups-1.43.2/bin'
make[2]: Entering directory `/home/chmacka/Desktop/Downloads/fwbackups/fwbackups-1.43.2-1.fc9.src/fwbackups-1.43.2/bin'
make[2]: Nothing to be done for `install-exec-am'.
/bin/bash /home/chmacka/Desktop/Downloads/fwbackups/fwbackups-1.43.2-1.fc9.src/fwbackups-1.43.2/install-sh -d /usr/bin
/usr/bin/install -c -m 755 fwbackups /usr/bin/fwbackups
/usr/bin/install -c -m 755 fwbackups-run.py /usr/bin/fwbackups-run
/usr/bin/install -c -m 755 fwbackups-runonce.py /usr/bin/fwbackups-runonce
make[2]: Leaving directory `/home/chmacka/Desktop/Downloads/fwbackups/fwbackups-1.43.2-1.fc9.src/fwbackups-1.43.2/bin'
make[1]: Leaving directory `/home/chmacka/Desktop/Downloads/fwbackups/fwbackups-1.43.2-1.fc9.src/fwbackups-1.43.2/bin'
Making install in help
make[1]: Entering directory `/home/chmacka/Desktop/Downloads/fwbackups/fwbackups-1.43.2-1.fc9.src/fwbackups-1.43.2/help'
make[2]: Entering directory `/home/chmacka/Desktop/Downloads/fwbackups/fwbackups-1.43.2-1.fc9.src/fwbackups-1.43.2/help'
make[2]: Nothing to be done for `install-exec-am'.
/bin/bash /home/chmacka/Desktop/Downloads/fwbackups/fwbackups-1.43.2-1.fc9.src/fwbackups-1.43.2/install-sh -d /usr/share/gnome/help/fwbackups/C
/usr/bin/install -c -m 644 C/fdl.xml /usr/share/gnome/help/fwbackups/C/fdl.xml
/usr/bin/install -c -m 644 C/gpl.xml /usr/share/gnome/help/fwbackups/C/gpl.xml
/usr/bin/install -c -m 644 C/fwbackups.xml /usr/share/gnome/help/fwbackups/C/fwbackups.xml
/usr/bin/install -c -m 644 ./C/figures/configuration.png /usr/share/gnome/help/fwbackups/C/figures/configuration.png
/usr/bin/install: cannot stat `./C/figures/configuration.png': No such file or directory
/usr/bin/install -c -m 644 C/figures/backup_sets_page.png /usr/share/gnome/help/fwbackups/C/figures/backup_sets_page.png
/usr/bin/install -c -m 644 C/figures/configure_backup_remote.png /usr/share/gnome/help/fwbackups/C/figures/configure_backup_remote.png
/usr/bin/install -c -m 644 C/figures/onetime_configuration.png /usr/share/gnome/help/fwbackups/C/figures/onetime_configuration.png
/usr/bin/install -c -m 644 C/figures/prefs_refresh.png /usr/share/gnome/help/fwbackups/C/figures/prefs_refresh.png
/usr/bin/install -c -m 644 C/figures/restore.png /usr/share/gnome/help/fwbackups/C/figures/restore.png
/usr/bin/install -c -m 644 C/figures/notification.png /usr/share/gnome/help/fwbackups/C/figures/notification.png
/bin/bash /home/chmacka/Desktop/Downloads/fwbackups/fwbackups-1.43.2-1.fc9.src/fwbackups-1.43.2/install-sh -d /usr/share/omf/fwbackups
/usr/bin/install -c -m 644 fwbackups-C.omf /usr/share/omf/fwbackups/fwbackups-C.omf
scrollkeeper-update -p /var/lib/rarian -o /usr/share/omf/fwbackups
make[2]: Leaving directory `/home/chmacka/Desktop/Downloads/fwbackups/fwbackups-1.43.2-1.fc9.src/fwbackups-1.43.2/help'
make[1]: Leaving directory `/home/chmacka/Desktop/Downloads/fwbackups/fwbackups-1.43.2-1.fc9.src/fwbackups-1.43.2/help'
Making install in po
make[1]: Entering directory `/home/chmacka/Desktop/Downloads/fwbackups/fwbackups-1.43.2-1.fc9.src/fwbackups-1.43.2/po'
/bin/sh /home/chmacka/Desktop/Downloads/fwbackups/fwbackups-1.43.2-1.fc9.src/fwbackups-1.43.2/install-sh -d /usr/share/locale
linguas=""; \
    for lang in $linguas; do \
      dir=/usr/share/locale/$lang/LC_MESSAGES; \
      /bin/sh /home/chmacka/Desktop/Downloads/fwbackups/fwbackups-1.43.2-1.fc9.src/fwbackups-1.43.2/install-sh -d $dir; \
      if test -r $lang.gmo; then \
        /usr/bin/install -c -m 644 $lang.gmo $dir/fwbackups.mo; \
        echo "installing $lang.gmo as $dir/fwbackups.mo"; \
      else \
        /usr/bin/install -c -m 644 ./$lang.gmo $dir/fwbackups.mo; \
        echo "installing ./$lang.gmo as" \
         "$dir/fwbackups.mo"; \
      fi; \
      if test -r $lang.gmo.m; then \
        /usr/bin/install -c -m 644 $lang.gmo.m $dir/fwbackups.mo.m; \
        echo "installing $lang.gmo.m as $dir/fwbackups.mo.m"; \
      else \
        if test -r ./$lang.gmo.m ; then \
          /usr/bin/install -c -m 644 ./$lang.gmo.m \
        $dir/fwbackups.mo.m; \
          echo "installing ./$lang.gmo.m as" \
           "$dir/fwbackups.mo.m"; \
        else \
          true; \
        fi; \
      fi; \
    done
make[1]: Leaving directory `/home/chmacka/Desktop/Downloads/fwbackups/fwbackups-1.43.2-1.fc9.src/fwbackups-1.43.2/po'
Making install in pixmaps
make[1]: Entering directory `/home/chmacka/Desktop/Downloads/fwbackups/fwbackups-1.43.2-1.fc9.src/fwbackups-1.43.2/pixmaps'
make[2]: Entering directory `/home/chmacka/Desktop/Downloads/fwbackups/fwbackups-1.43.2-1.fc9.src/fwbackups-1.43.2/pixmaps'
make[2]: Nothing to be done for `install-exec-am'.
/bin/bash /home/chmacka/Desktop/Downloads/fwbackups/fwbackups-1.43.2-1.fc9.src/fwbackups-1.43.2/install-sh -d /usr/share/pixmaps/
/usr/bin/install -c -m 644 fwbackups.svg /usr/share/pixmaps/fwbackups.svg
/usr/bin/install -c -m 644 fwbackups-32.png /usr/share/pixmaps/fwbackups.png
make[2]: Leaving directory `/home/chmacka/Desktop/Downloads/fwbackups/fwbackups-1.43.2-1.fc9.src/fwbackups-1.43.2/pixmaps'
make[1]: Leaving directory `/home/chmacka/Desktop/Downloads/fwbackups/fwbackups-1.43.2-1.fc9.src/fwbackups-1.43.2/pixmaps'
Making install in src
make[1]: Entering directory `/home/chmacka/Desktop/Downloads/fwbackups/fwbackups-1.43.2-1.fc9.src/fwbackups-1.43.2/src'
make[2]: Entering directory `/home/chmacka/Desktop/Downloads/fwbackups/fwbackups-1.43.2-1.fc9.src/fwbackups-1.43.2/src'
make[2]: Nothing to be done for `install-exec-am'.
/bin/bash /home/chmacka/Desktop/Downloads/fwbackups/fwbackups-1.43.2-1.fc9.src/fwbackups-1.43.2/install-sh -d /usr/share/applications
/usr/bin/install -c -m 644 fwbackups.desktop /usr/share/applications/fwbackups.desktop
test -z "/usr/share/fwbackups" || /bin/mkdir -p "/usr/share/fwbackups"
 /usr/bin/install -c -m 644 'BugReport.glade' '/usr/share/fwbackups/BugReport.glade'
 /usr/bin/install -c -m 644 'cronwriter.py' '/usr/share/fwbackups/cronwriter.py'
 /usr/bin/install -c -m 644 'fwbackups.glade' '/usr/share/fwbackups/fwbackups.glade'
 /usr/bin/install -c -m 644 'fwbackups-autostart.desktop' '/usr/share/fwbackups/fwbackups-autostart.desktop'
 /usr/bin/install -c -m 644 'fwbackups-runapp.pyw' '/usr/share/fwbackups/fwbackups-runapp.pyw'
make[2]: Leaving directory `/home/chmacka/Desktop/Downloads/fwbackups/fwbackups-1.43.2-1.fc9.src/fwbackups-1.43.2/src'
make[1]: Leaving directory `/home/chmacka/Desktop/Downloads/fwbackups/fwbackups-1.43.2-1.fc9.src/fwbackups-1.43.2/src'
Making install in src/fwbackups
make[1]: Entering directory `/home/chmacka/Desktop/Downloads/fwbackups/fwbackups-1.43.2-1.fc9.src/fwbackups-1.43.2/src/fwbackups'
make[2]: Entering directory `/home/chmacka/Desktop/Downloads/fwbackups/fwbackups-1.43.2-1.fc9.src/fwbackups-1.43.2/src/fwbackups'
make[2]: Nothing to be done for `install-exec-am'.
test -z "/usr/lib/python2.6/site-packages/fwbackups" || /bin/mkdir -p "/usr/lib/python2.6/site-packages/fwbackups"
 /usr/bin/install -c -m 644 'backend.py' '/usr/lib/python2.6/site-packages/fwbackups/backend.py'
 /usr/bin/install -c -m 644 'config.py' '/usr/lib/python2.6/site-packages/fwbackups/config.py'
 /usr/bin/install -c -m 644 'const.py' '/usr/lib/python2.6/site-packages/fwbackups/const.py'
 /usr/bin/install -c -m 644 'cron.py' '/usr/lib/python2.6/site-packages/fwbackups/cron.py'
 /usr/bin/install -c -m 644 'fwlogger.py' '/usr/lib/python2.6/site-packages/fwbackups/fwlogger.py'
 /usr/bin/install -c -m 644 'guiutils.py' '/usr/lib/python2.6/site-packages/fwbackups/guiutils.py'
 /usr/bin/install -c -m 644 'i18n.py' '/usr/lib/python2.6/site-packages/fwbackups/i18n.py'
 /usr/bin/install -c -m 644 '__init__.py' '/usr/lib/python2.6/site-packages/fwbackups/__init__.py'
 /usr/bin/install -c -m 644 'interface.py' '/usr/lib/python2.6/site-packages/fwbackups/interface.py'
 /usr/bin/install -c -m 644 'remote.py' '/usr/lib/python2.6/site-packages/fwbackups/remote.py'
 /usr/bin/install -c -m 644 'shutil_modded.py' '/usr/lib/python2.6/site-packages/fwbackups/shutil_modded.py'
 /usr/bin/install -c -m 644 'subprocess_killable.py' '/usr/lib/python2.6/site-packages/fwbackups/subprocess_killable.py'
 /usr/bin/install -c -m 644 'widgets.py' '/usr/lib/python2.6/site-packages/fwbackups/widgets.py'
 /usr/bin/install -c -m 644 'winprocess.py' '/usr/lib/python2.6/site-packages/fwbackups/winprocess.py'
Byte-compiling python modules...
backend.py config.py const.py cron.py fwlogger.py guiutils.py i18n.py __init__.py interface.py remote.py shutil_modded.py subprocess_killable.py widgets.py winprocess.py
Byte-compiling python modules (optimized versions) ...
backend.py config.py const.py cron.py fwlogger.py guiutils.py i18n.py __init__.py interface.py remote.py shutil_modded.py subprocess_killable.py widgets.py winprocess.py
make[2]: Leaving directory `/home/chmacka/Desktop/Downloads/fwbackups/fwbackups-1.43.2-1.fc9.src/fwbackups-1.43.2/src/fwbackups'
make[1]: Leaving directory `/home/chmacka/Desktop/Downloads/fwbackups/fwbackups-1.43.2-1.fc9.src/fwbackups-1.43.2/src/fwbackups'
make[1]: Entering directory `/home/chmacka/Desktop/Downloads/fwbackups/fwbackups-1.43.2-1.fc9.src/fwbackups-1.43.2'
make[2]: Entering directory `/home/chmacka/Desktop/Downloads/fwbackups/fwbackups-1.43.2-1.fc9.src/fwbackups-1.43.2'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/chmacka/Desktop/Downloads/fwbackups/fwbackups-1.43.2-1.fc9.src/fwbackups-1.43.2'
make[1]: Leaving directory `/home/chmacka/Desktop/Downloads/fwbackups/fwbackups-1.43.2-1.fc9.src/fwbackups-1.43.2'
chmacka@chmacka-desktop:~/Desktop/Downloads/fwbackups/fwbackups-1.43.2-1.fc9.src/fwbackups-1.43.2$ fwbackups
Traceback (most recent call last):
  File "/usr/local/share/fwbackups/fwbackups-runapp.pyw", line 34, in <module>
    from fwbackups.const import *
ImportError: No module named fwbackups.const
chmacka@chmacka-desktop:~/Desktop/Downloads/fwbackups/fwbackups-1.43.2-1.fc9.src/fwbackups-1.43.2$ 

```

---

### Post by firewing1 on 2009-07-28
Oh, I just realized you're using 1.43.2... 1.43.2 has some bugs regarding the remote backup operations, and I also cleaned up the build procedures in 1.43.3rc2 so this should help with the installation. I've posted some details on how to install it here: [http://ubuntuforums.org/showpost.php?p=7689989&postcount=14](http://ubuntuforums.org/showpost.php?p=7689989&postcount=14)

Running those six command I posted should have you up & running (it did for me at least on my Ubuntu 9.04 test install).

---

### Post by chmacka on 2009-07-28
O. K. First I had to install **intltool**. After that everything went fine until **make && sudo make install**. I had to do it separately (**sudo make** and then **sudo make install**). But it still doesn't work:

```
chmacka@chmacka-desktop:~/fwbackups-1.43.3rc2$ fwbackups
Traceback (most recent call last):
  File "/usr/local/share/fwbackups/fwbackups-runapp.pyw", line 59, in <module>
    from fwbackups import backend
ImportError: cannot import name backend

```EDIT: I can't install[B] glib2-devel:

[/B]```

chmacka@chmacka-desktop:~$ sudo apt-get install glib2-devel
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package glib2-devel
chmacka@chmacka-desktop:~$ 
chmacka@chmacka-desktop:~$ 

```

---

### Post by firewing1 on 2009-07-28
Don't worry about glib2-devel not being found, if it compiled then all is well. Are you sure you ran ./configure with "--datadir=/usr/share" though? It seems it is still installing to /usr/local/share, which is isn't supported in 1.43.3rc2 (the fix for that is in git at the moment). It will work fine if you install to /usr/share.

Sorry again for all the problems, it's the first time I test on Ubuntu (I use Fedora at home) so the patches in git, but haven't made it to a release yet. 1.43.3rc3 will be significantly easier to install on Ubuntu :)

---

### Post by chmacka on 2009-07-28
> **firewing1 said:**
> Are you sure you ran ./configure with "--datadir=/usr/share" though?
Here is the whole process:

```
**chmacka@chmacka-desktop:~$ sudo apt-get install intltool gnome-doc-utils python-paramiko python-notify python-gtk2**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
intltool is already the newest version.
gnome-doc-utils is already the newest version.
python-paramiko is already the newest version.
python-notify is already the newest version.
python-gtk2 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
** chmacka@chmacka-desktop:~$ sudo wget http://downloads.diffingo.com/fwbackups/fwbackups-1.43.3rc2.tar.bz2**
--2009-07-29 00:54:38--  http://downloads.diffingo.com/fwbackups/fwbackups-1.43.3rc2.tar.bz2
Resolving downloads.diffingo.com... 174.142.119.200
Connecting to downloads.diffingo.com|174.142.119.200|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 412234 (403K) [application/x-bzip2]
Saving to: `fwbackups-1.43.3rc2.tar.bz2.3'

100%[======================================>] 412,234      114K/s   in 3.6s    

2009-07-29 00:54:42 (111 KB/s) - `fwbackups-1.43.3rc2.tar.bz2.3' saved [412234/412234]

** chmacka@chmacka-desktop:~$ sudo tar xfj fwbackups-1.43.3rc2.tar.bz2**
** chmacka@chmacka-desktop:~$ cd fwbackups-1.43.3rc2**
** chmacka@chmacka-desktop:~/fwbackups-1.43.3rc2$ sudo ./configure --prefix=/usr --datadir=/usr/share**
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for a Python interpreter with version >= 2.4... python
checking for python... /usr/bin/python
checking for python version... 2.6
checking for python platform... linux2
checking for python script directory... ${prefix}/lib/python2.6/site-packages
checking for python extension module directory... ${exec_prefix}/lib/python2.6/site-packages
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... none
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking locale.h usability... yes
checking locale.h presence... yes
checking for locale.h... yes
checking for LC_MESSAGES... yes
checking libintl.h usability... yes
checking libintl.h presence... yes
checking for libintl.h... yes
checking for ngettext in libc... yes
checking for dgettext in libc... yes
checking for bind_textdomain_codeset... yes
checking for msgfmt... /usr/bin/msgfmt
checking for dcgettext... yes
checking if msgfmt accepts -c... yes
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
checking whether NLS is requested... yes
checking for intltool-update... /usr/bin/intltool-update
checking for intltool-merge... /usr/bin/intltool-merge
checking for intltool-extract... /usr/bin/intltool-extract
checking for xgettext... (cached) /usr/bin/xgettext
checking for msgmerge... /usr/bin/msgmerge
checking for msgfmt... (cached) /usr/bin/msgfmt
checking for gmsgfmt... (cached) /usr/bin/msgfmt
checking for perl... /usr/bin/perl
checking for XML::Parser... ok
configure: creating ./config.status
config.status: creating bin/Makefile
config.status: creating bin/fwbackups
config.status: creating help/Makefile
config.status: creating pixmaps/Makefile
config.status: creating po/Makefile.in
config.status: creating src/Makefile
config.status: creating src/fwbackups/Makefile
config.status: creating src/fwbackups/operations/Makefile
config.status: creating src/fwbackups/__init__.py
config.status: creating Makefile
config.status: creating fwbackups.spec
config.status: executing depfiles commands
config.status: executing default-1 commands
config.status: executing po/stamp-it commands
# INTLTOOL_MAKEFILE
** chmacka@chmacka-desktop:~/fwbackups-1.43.3rc2$ sudo make**
 cd . && /bin/bash /home/chmacka/fwbackups-1.43.3rc2/missing --run automake-1.10 --gnu 
gnome-doc-utils.make:74: if $(DOC_H_FILE: non-POSIX variable name
gnome-doc-utils.make:74: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:77: if $(DOC_H_FILE: non-POSIX variable name
gnome-doc-utils.make:77: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:110: if $(DOC_USER_FORMATS: non-POSIX variable name
gnome-doc-utils.make:110: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:115: if $(filter environment,$(origin LINGUAS: non-POSIX variable name
gnome-doc-utils.make:115: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:115: filter $(LINGUAS: non-POSIX variable name
gnome-doc-utils.make:115: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:144: shell xmllint --format $(2: non-POSIX variable name
gnome-doc-utils.make:144: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:144: notdir $(patsubst %/$(notdir $(2: non-POSIX variable name
gnome-doc-utils.make:144: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:144: if $(_ENABLE_SK: non-POSIX variable name
gnome-doc-utils.make:144: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:160: if $(DOC_MODULE: non-POSIX variable name
gnome-doc-utils.make:160: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:160: wildcard $(_DOC_ABS_SRCDIR: non-POSIX variable name
gnome-doc-utils.make:160: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:164: if $(_DOC_OMF_IN: non-POSIX variable name
gnome-doc-utils.make:164: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:164: foreach lc,C $(_DOC_REAL_LINGUAS: non-POSIX variable name
gnome-doc-utils.make:164: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:173: call db2omf_args,$@,$<,'docbook': non-POSIX variable name
gnome-doc-utils.make:173: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:177: if $(_DOC_OMF_IN: non-POSIX variable name
gnome-doc-utils.make:177: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:177: foreach lc,C $(_DOC_REAL_LINGUAS: non-POSIX variable name
gnome-doc-utils.make:177: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:188: call db2omf_args,$@,$<,'xhtml': non-POSIX variable name
gnome-doc-utils.make:188: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:193: if $(filter docbook,$(_DOC_REAL_FORMATS: non-POSIX variable name
gnome-doc-utils.make:193: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:193: if $(filter html HTML,$(_DOC_REAL_FORMATS: non-POSIX variable name
gnome-doc-utils.make:193: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:206: if $(DOC_MODULE: non-POSIX variable name
gnome-doc-utils.make:206: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:210: foreach ent,$(DOC_ENTITIES: non-POSIX variable name
gnome-doc-utils.make:210: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:214: foreach inc,$(DOC_INCLUDES: non-POSIX variable name
gnome-doc-utils.make:214: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:230: if $(DOC_FIGURES: non-POSIX variable name
gnome-doc-utils.make:230: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:230: foreach fig,$(DOC_FIGURES: non-POSIX variable name
gnome-doc-utils.make:230: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:230: patsubst $(srcdir: non-POSIX variable name
gnome-doc-utils.make:230: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:230: wildcard $(srcdir: non-POSIX variable name
gnome-doc-utils.make:230: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:237: foreach f,                        \
gnome-doc-utils.make:237:     $(shell xsltproc --xinclude             \
gnome-doc-utils.make:237:       --stringparam db.chunk.basename "$(DOC_MODULE: non-POSIX variable name
gnome-doc-utils.make:237: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:248: if $(DOC_MODULE: non-POSIX variable name
gnome-doc-utils.make:248: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:248: foreach lc,$(_DOC_REAL_LINGUAS: non-POSIX variable name
gnome-doc-utils.make:248: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:256: if $(DOC_MODULE: non-POSIX variable name
gnome-doc-utils.make:256: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:256: foreach lc,$(_DOC_REAL_LINGUAS: non-POSIX variable name
gnome-doc-utils.make:256: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:261: foreach lc,$(_DOC_REAL_LINGUAS: non-POSIX variable name
gnome-doc-utils.make:261: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:261: foreach inc,$(_DOC_C_INCLUDES: non-POSIX variable name
gnome-doc-utils.make:261: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:261: notdir $(inc: non-POSIX variable name
gnome-doc-utils.make:261: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:268: foreach lc,$(_DOC_REAL_LINGUAS: non-POSIX variable name
gnome-doc-utils.make:268: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:268: foreach doc,$(_DOC_C_HTML: non-POSIX variable name
gnome-doc-utils.make:268: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:268: notdir $(doc: non-POSIX variable name
gnome-doc-utils.make:268: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:274: if $(filter html HTML,$(_DOC_REAL_FORMATS: non-POSIX variable name
gnome-doc-utils.make:274: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:280: foreach lc,$(_DOC_REAL_LINGUAS: non-POSIX variable name
gnome-doc-utils.make:280: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:280: patsubst C/%,$(lc: non-POSIX variable name
gnome-doc-utils.make:280: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:283: foreach fig,$(_DOC_C_FIGURES: non-POSIX variable name
gnome-doc-utils.make:283: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:283: foreach lc,C $(_DOC_REAL_LINGUAS: non-POSIX variable name
gnome-doc-utils.make:283: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:283: wildcard $(srcdir: non-POSIX variable name
gnome-doc-utils.make:283: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:283: patsubst C/%,%,$(fig: non-POSIX variable name
gnome-doc-utils.make:283: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:288: dir $@: non-POSIX variable name
gnome-doc-utils.make:288: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:318: dir $@: non-POSIX variable name
gnome-doc-utils.make:318: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:319: notdir $@: non-POSIX variable name
gnome-doc-utils.make:319: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:328: if $(DOC_MODULE: non-POSIX variable name
gnome-doc-utils.make:328: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:340: if $(filter html HTML,$(_DOC_REAL_FORMATS: non-POSIX variable name
gnome-doc-utils.make:340: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:343: foreach lc,C $(_DOC_REAL_LINGUAS: non-POSIX variable name
gnome-doc-utils.make:343: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:346: patsubst %.xhtml,%.xml,$@: non-POSIX variable name
gnome-doc-utils.make:346: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:385: if $(_DOC_OMF_IN: non-POSIX variable name
gnome-doc-utils.make:385: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:386: if $(_DOC_DSK_IN: non-POSIX variable name
gnome-doc-utils.make:386: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:387: if $(_DOC_REAL_LINGUAS: non-POSIX variable name
gnome-doc-utils.make:387: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:388: if $(DOC_MODULE: non-POSIX variable name
gnome-doc-utils.make:388: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:505: patsubst C/%,%,$(_DOC_C_FIGURES: non-POSIX variable name
gnome-doc-utils.make:505: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
cd . && /bin/bash /home/chmacka/fwbackups-1.43.3rc2/missing --run autoconf
configure.ac:18: error: possibly undefined macro: AM_GLIB_GNU_GETTEXT
      If this token and others are legitimate, please use m4_pattern_allow.
      See the Autoconf documentation.
make: *** [configure] Error 1
** chmacka@chmacka-desktop:~/fwbackups-1.43.3rc2$ **
/bin/bash ./config.status --recheck
running CONFIG_SHELL=/bin/bash /bin/bash ./configure --prefix=/usr --datadir=/usr/share --no-create --no-recursion
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for a Python interpreter with version >= 2.4... python
checking for python... /usr/bin/python
checking for python version... 2.6
checking for python platform... linux2
checking for python script directory... /usr/lib/python2.6/dist-packages
checking for python extension module directory... /usr/lib/python2.6/dist-packages
checking whether ln -s works... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
./configure: line 2759: AM_GLIB_GNU_GETTEXT: command not found
checking whether NLS is requested... yes
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... none
checking for intltool-update... /usr/bin/intltool-update
checking for intltool-merge... /usr/bin/intltool-merge
checking for intltool-extract... /usr/bin/intltool-extract
checking for xgettext... /usr/bin/xgettext
checking for msgmerge... /usr/bin/msgmerge
checking for msgfmt... /usr/bin/msgfmt
checking for gmsgfmt... /usr/bin/msgfmt
checking for perl... /usr/bin/perl
checking for perl >= 5.8.1... 5.10.0
checking for XML::Parser... ok
configure: creating ./config.status
 /bin/bash ./config.status
config.status: creating bin/Makefile
config.status: creating bin/fwbackups
config.status: creating help/Makefile
config.status: creating pixmaps/Makefile
config.status: creating po/Makefile.in
config.status: creating src/Makefile
config.status: creating src/fwbackups/Makefile
config.status: creating src/fwbackups/operations/Makefile
config.status: creating src/fwbackups/__init__.py
config.status: creating Makefile
config.status: creating fwbackups.spec
config.status: executing depfiles commands
config.status: executing po/stamp-it commands
Making all in bin
make[1]: Entering directory `/home/chmacka/fwbackups-1.43.3rc2/bin'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/chmacka/fwbackups-1.43.3rc2/bin'
Making all in help
make[1]: Entering directory `/home/chmacka/fwbackups-1.43.3rc2/help'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/chmacka/fwbackups-1.43.3rc2/help'
Making all in po
make[1]: Entering directory `/home/chmacka/fwbackups-1.43.3rc2/po'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/chmacka/fwbackups-1.43.3rc2/po'
Making all in pixmaps
make[1]: Entering directory `/home/chmacka/fwbackups-1.43.3rc2/pixmaps'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/chmacka/fwbackups-1.43.3rc2/pixmaps'
Making all in src
make[1]: Entering directory `/home/chmacka/fwbackups-1.43.3rc2/src'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/chmacka/fwbackups-1.43.3rc2/src'
Making all in src/fwbackups
make[1]: Entering directory `/home/chmacka/fwbackups-1.43.3rc2/src/fwbackups'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/chmacka/fwbackups-1.43.3rc2/src/fwbackups'
Making all in src/fwbackups/operations
make[1]: Entering directory `/home/chmacka/fwbackups-1.43.3rc2/src/fwbackups/operations'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/chmacka/fwbackups-1.43.3rc2/src/fwbackups/operations'
make[1]: Entering directory `/home/chmacka/fwbackups-1.43.3rc2'
make[1]: Nothing to be done for `all-am'.
make[1]: Leaving directory `/home/chmacka/fwbackups-1.43.3rc2'
** chmacka@chmacka-desktop:~/fwbackups-1.43.3rc2$ sudo make install**
Making install in bin
make[1]: Entering directory `/home/chmacka/fwbackups-1.43.3rc2/bin'
make[2]: Entering directory `/home/chmacka/fwbackups-1.43.3rc2/bin'
make[2]: Nothing to be done for `install-exec-am'.
/bin/bash /home/chmacka/fwbackups-1.43.3rc2/install-sh -d /usr/bin
/usr/bin/install -c -m 755 fwbackups /usr/bin/fwbackups
/usr/bin/install -c -m 755 fwbackups-run.py /usr/bin/fwbackups-run
/usr/bin/install -c -m 755 fwbackups-runonce.py /usr/bin/fwbackups-runonce
make[2]: Leaving directory `/home/chmacka/fwbackups-1.43.3rc2/bin'
make[1]: Leaving directory `/home/chmacka/fwbackups-1.43.3rc2/bin'
Making install in help
make[1]: Entering directory `/home/chmacka/fwbackups-1.43.3rc2/help'
make[2]: Entering directory `/home/chmacka/fwbackups-1.43.3rc2/help'
make[2]: Nothing to be done for `install-exec-am'.
/bin/bash /home/chmacka/fwbackups-1.43.3rc2/install-sh -d /usr/share/gnome/help/fwbackups/C
/usr/bin/install -c -m 644 C/fdl.xml /usr/share/gnome/help/fwbackups/C/fdl.xml
/usr/bin/install -c -m 644 C/gpl.xml /usr/share/gnome/help/fwbackups/C/gpl.xml
/usr/bin/install -c -m 644 C/fwbackups.xml /usr/share/gnome/help/fwbackups/C/fwbackups.xml
/usr/bin/install -c -m 644 C/figures/backup_sets_page.png /usr/share/gnome/help/fwbackups/C/figures/backup_sets_page.png
/usr/bin/install -c -m 644 C/figures/configure_backup_remote.png /usr/share/gnome/help/fwbackups/C/figures/configure_backup_remote.png
/usr/bin/install -c -m 644 C/figures/onetime_configuration.png /usr/share/gnome/help/fwbackups/C/figures/onetime_configuration.png
/usr/bin/install -c -m 644 C/figures/prefs_refresh.png /usr/share/gnome/help/fwbackups/C/figures/prefs_refresh.png
/usr/bin/install -c -m 644 C/figures/restore.png /usr/share/gnome/help/fwbackups/C/figures/restore.png
/usr/bin/install -c -m 644 C/figures/notification.png /usr/share/gnome/help/fwbackups/C/figures/notification.png
/bin/bash /home/chmacka/fwbackups-1.43.3rc2/install-sh -d /usr/share/omf/fwbackups
/usr/bin/install -c -m 644 fwbackups-C.omf /usr/share/omf/fwbackups/fwbackups-C.omf
scrollkeeper-update -p /var/lib/rarian -o /usr/share/omf/fwbackups
make[2]: Leaving directory `/home/chmacka/fwbackups-1.43.3rc2/help'
make[1]: Leaving directory `/home/chmacka/fwbackups-1.43.3rc2/help'
Making install in po
make[1]: Entering directory `/home/chmacka/fwbackups-1.43.3rc2/po'
/bin/sh /home/chmacka/fwbackups-1.43.3rc2/install-sh -d /usr/share/locale
linguas=""; \
    for lang in $linguas; do \
      dir=/usr/share/locale/$lang/LC_MESSAGES; \
      /bin/sh /home/chmacka/fwbackups-1.43.3rc2/install-sh -d $dir; \
      if test -r $lang.gmo; then \
        /usr/bin/install -c -m 644 $lang.gmo $dir/fwbackups.mo; \
        echo "installing $lang.gmo as $dir/fwbackups.mo"; \
      else \
        /usr/bin/install -c -m 644 ./$lang.gmo $dir/fwbackups.mo; \
        echo "installing ./$lang.gmo as" \
         "$dir/fwbackups.mo"; \
      fi; \
      if test -r $lang.gmo.m; then \
        /usr/bin/install -c -m 644 $lang.gmo.m $dir/fwbackups.mo.m; \
        echo "installing $lang.gmo.m as $dir/fwbackups.mo.m"; \
      else \
        if test -r ./$lang.gmo.m ; then \
          /usr/bin/install -c -m 644 ./$lang.gmo.m \
        $dir/fwbackups.mo.m; \
          echo "installing ./$lang.gmo.m as" \
           "$dir/fwbackups.mo.m"; \
        else \
          true; \
        fi; \
      fi; \
    done
make[1]: Leaving directory `/home/chmacka/fwbackups-1.43.3rc2/po'
Making install in pixmaps
make[1]: Entering directory `/home/chmacka/fwbackups-1.43.3rc2/pixmaps'
make[2]: Entering directory `/home/chmacka/fwbackups-1.43.3rc2/pixmaps'
make[2]: Nothing to be done for `install-exec-am'.
/bin/bash /home/chmacka/fwbackups-1.43.3rc2/install-sh -d /usr/share/pixmaps/
/bin/bash /home/chmacka/fwbackups-1.43.3rc2/install-sh -d /usr/share/fwbackups/
/usr/bin/install -c -m 644 fwbackups.svg /usr/share/pixmaps/fwbackups.svg
/usr/bin/install -c -m 644 fwbackups-32.png /usr/share/fwbackups/fwbackups.png
make[2]: Leaving directory `/home/chmacka/fwbackups-1.43.3rc2/pixmaps'
make[1]: Leaving directory `/home/chmacka/fwbackups-1.43.3rc2/pixmaps'
Making install in src
make[1]: Entering directory `/home/chmacka/fwbackups-1.43.3rc2/src'
make[2]: Entering directory `/home/chmacka/fwbackups-1.43.3rc2/src'
make[2]: Nothing to be done for `install-exec-am'.
/bin/bash /home/chmacka/fwbackups-1.43.3rc2/install-sh -d /usr/share/applications
/usr/bin/install -c -m 644 fwbackups.desktop /usr/share/applications/fwbackups.desktop
test -z "/usr/share/fwbackups" || /bin/mkdir -p "/usr/share/fwbackups"
 /usr/bin/install -c -m 644 'BugReport.glade' '/usr/share/fwbackups/BugReport.glade'
 /usr/bin/install -c -m 644 'cronwriter.py' '/usr/share/fwbackups/cronwriter.py'
 /usr/bin/install -c -m 644 'fwbackups.glade' '/usr/share/fwbackups/fwbackups.glade'
 /usr/bin/install -c -m 644 'fwbackups-autostart.desktop' '/usr/share/fwbackups/fwbackups-autostart.desktop'
 /usr/bin/install -c -m 644 'fwbackups-runapp.pyw' '/usr/share/fwbackups/fwbackups-runapp.pyw'
make[2]: Leaving directory `/home/chmacka/fwbackups-1.43.3rc2/src'
make[1]: Leaving directory `/home/chmacka/fwbackups-1.43.3rc2/src'
Making install in src/fwbackups
make[1]: Entering directory `/home/chmacka/fwbackups-1.43.3rc2/src/fwbackups'
make[2]: Entering directory `/home/chmacka/fwbackups-1.43.3rc2/src/fwbackups'
make[2]: Nothing to be done for `install-exec-am'.
test -z "/usr/lib/python2.6/dist-packages/fwbackups" || /bin/mkdir -p "/usr/lib/python2.6/dist-packages/fwbackups"
 /usr/bin/install -c -m 644 'config.py' '/usr/lib/python2.6/dist-packages/fwbackups/config.py'
 /usr/bin/install -c -m 644 'const.py' '/usr/lib/python2.6/dist-packages/fwbackups/const.py'
 /usr/bin/install -c -m 644 'cron.py' '/usr/lib/python2.6/dist-packages/fwbackups/cron.py'
 /usr/bin/install -c -m 644 'fwlogger.py' '/usr/lib/python2.6/dist-packages/fwbackups/fwlogger.py'
 /usr/bin/install -c -m 644 'i18n.py' '/usr/lib/python2.6/dist-packages/fwbackups/i18n.py'
 /usr/bin/install -c -m 644 '__init__.py' '/usr/lib/python2.6/dist-packages/fwbackups/__init__.py'
 /usr/bin/install -c -m 644 'interface.py' '/usr/lib/python2.6/dist-packages/fwbackups/interface.py'
 /usr/bin/install -c -m 644 'sftp.py' '/usr/lib/python2.6/dist-packages/fwbackups/sftp.py'
 /usr/bin/install -c -m 644 'shutil_modded.py' '/usr/lib/python2.6/dist-packages/fwbackups/shutil_modded.py'
 /usr/bin/install -c -m 644 'subprocess_killable.py' '/usr/lib/python2.6/dist-packages/fwbackups/subprocess_killable.py'
 /usr/bin/install -c -m 644 'widgets.py' '/usr/lib/python2.6/dist-packages/fwbackups/widgets.py'
 /usr/bin/install -c -m 644 'winprocess.py' '/usr/lib/python2.6/dist-packages/fwbackups/winprocess.py'
Byte-compiling python modules...
config.py const.py cron.py fwlogger.py i18n.py __init__.py interface.py sftp.py shutil_modded.py subprocess_killable.py widgets.py winprocess.py
Byte-compiling python modules (optimized versions) ...
config.py const.py cron.py fwlogger.py i18n.py __init__.py interface.py sftp.py shutil_modded.py subprocess_killable.py widgets.py winprocess.py
make[2]: Leaving directory `/home/chmacka/fwbackups-1.43.3rc2/src/fwbackups'
make[1]: Leaving directory `/home/chmacka/fwbackups-1.43.3rc2/src/fwbackups'
Making install in src/fwbackups/operations
make[1]: Entering directory `/home/chmacka/fwbackups-1.43.3rc2/src/fwbackups/operations'
make[2]: Entering directory `/home/chmacka/fwbackups-1.43.3rc2/src/fwbackups/operations'
make[2]: Nothing to be done for `install-exec-am'.
test -z "/usr/lib/python2.6/dist-packages/fwbackups/operations" || /bin/mkdir -p "/usr/lib/python2.6/dist-packages/fwbackups/operations"
 /usr/bin/install -c -m 644 '__init__.py' '/usr/lib/python2.6/dist-packages/fwbackups/operations/__init__.py'
 /usr/bin/install -c -m 644 'backup.py' '/usr/lib/python2.6/dist-packages/fwbackups/operations/backup.py'
 /usr/bin/install -c -m 644 'restore.py' '/usr/lib/python2.6/dist-packages/fwbackups/operations/restore.py'
Byte-compiling python modules...
__init__.py backup.py restore.py
Byte-compiling python modules (optimized versions) ...
__init__.py backup.py restore.py
make[2]: Leaving directory `/home/chmacka/fwbackups-1.43.3rc2/src/fwbackups/operations'
make[1]: Leaving directory `/home/chmacka/fwbackups-1.43.3rc2/src/fwbackups/operations'
make[1]: Entering directory `/home/chmacka/fwbackups-1.43.3rc2'
make[2]: Entering directory `/home/chmacka/fwbackups-1.43.3rc2'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/chmacka/fwbackups-1.43.3rc2'
make[1]: Leaving directory `/home/chmacka/fwbackups-1.43.3rc2'
** chmacka@chmacka-desktop:~/fwbackups-1.43.3rc2$ fwbackups**
Traceback (most recent call last):
  File "/usr/local/share/fwbackups/fwbackups-runapp.pyw", line 59, in <module>
    from fwbackups import backend
ImportError: cannot import name backend
chmacka@chmacka-desktop:~/fwbackups-1.43.3rc2$ 

```

---

### Post by firewing1 on 2009-07-28
The glib error was concerning the DocBook documentation in the help/ directory, so it doesn't matter if that's not built (fwbackups will use online documentation instead).

It could be that the first installation of fwbackups you made wasn't uninstalled. Do both /usr/share/fwbackups and /usr/local/share/fwbackups exist? If so that is the problem and I can show you how to remove the copy in /usr/local.

---

### Post by chmacka on 2009-07-29
Yes, they both exist.

---

### Post by firewing1 on 2009-07-29
Aha, so that's the problem. The following command will clean out the unwanted installation in /usr/local:```

sudo rm -rf /usr/local/share/fwbackups
sudo rm -rf /usr/local/share/gnome/help/fwbackups
sudo rm -f /usr/local/bin/*fwbackups*
sudo rm -f /usr/local/share/applications/fwbackups.desktop
sudo rm -f /usr/local/share/pixmaps/fwbackups.svg

```
After a login + logout, things should be back to normal.

---

### Post by chmacka on 2009-08-02
> **firewing1 said:**
> Aha, so that's the problem. The following command will clean out the unwanted installation in /usr/local:```

sudo rm -rf /usr/local/share/fwbackups
sudo rm -rf /usr/local/share/gnome/help/fwbackups
sudo rm -f /usr/local/bin/*fwbackups*
sudo rm -f /usr/local/share/applications/fwbackups.desktop
sudo rm -f /usr/local/share/pixmaps/fwbackups.svg

```After a login + logout, things should be back to normal.
I did that and now when I run fwbackups in terminal I get this:

```
bash: fwbackups: command not found
```I tried reinstalling but I still get the same "command not found" error.

```
chmacka@chmacka-desktop:~/Desktop/Downloads/fwbackups/fwbackups-1.43.2-1.fc9.src/fwbackups-1.43.2$ sudo apt-get install intltool gnome-doc-utils python-paramiko python-notify python-gtk2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
intltool is already the newest version.
gnome-doc-utils is already the newest version.
python-paramiko is already the newest version.
python-notify is already the newest version.
python-gtk2 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
chmacka@chmacka-desktop:~/Desktop/Downloads/fwbackups/fwbackups-1.43.2-1.fc9.src/fwbackups-1.43.2$ sudo wget http://downloads.diffingo.com/fwbackups/fwbackups-1.43.3rc2.tar.bz2
--2009-08-02 14:25:12--  http://downloads.diffingo.com/fwbackups/fwbackups-1.43.3rc2.tar.bz2
Resolving downloads.diffingo.com... 174.142.119.200
Connecting to downloads.diffingo.com|174.142.119.200|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 412234 (403K) [application/x-bzip2]
Saving to: `fwbackups-1.43.3rc2.tar.bz2'

100%[======================================>] 412,234      114K/s   in 3.6s    

2009-08-02 14:25:16 (111 KB/s) - `fwbackups-1.43.3rc2.tar.bz2' saved [412234/412234]

chmacka@chmacka-desktop:~/Desktop/Downloads/fwbackups/fwbackups-1.43.2-1.fc9.src/fwbackups-1.43.2$ sudo tar xfj fwbackups-1.43.3rc2.tar.bz2
chmacka@chmacka-desktop:~/Desktop/Downloads/fwbackups/fwbackups-1.43.2-1.fc9.src/fwbackups-1.43.2$ cd fwbackups-1.43.3rc2
chmacka@chmacka-desktop:~/Desktop/Downloads/fwbackups/fwbackups-1.43.2-1.fc9.src/fwbackups-1.43.2/fwbackups-1.43.3rc2$ sudo ./configure --prefix=/usr --datadir=/usr/share
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for a Python interpreter with version >= 2.4... python
checking for python... /usr/bin/python
checking for python version... 2.6
checking for python platform... linux2
checking for python script directory... ${prefix}/lib/python2.6/site-packages
checking for python extension module directory... ${exec_prefix}/lib/python2.6/site-packages
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... none
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking locale.h usability... yes
checking locale.h presence... yes
checking for locale.h... yes
checking for LC_MESSAGES... yes
checking libintl.h usability... yes
checking libintl.h presence... yes
checking for libintl.h... yes
checking for ngettext in libc... yes
checking for dgettext in libc... yes
checking for bind_textdomain_codeset... yes
checking for msgfmt... /usr/bin/msgfmt
checking for dcgettext... yes
checking if msgfmt accepts -c... yes
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
checking whether NLS is requested... yes
checking for intltool-update... /usr/bin/intltool-update
checking for intltool-merge... /usr/bin/intltool-merge
checking for intltool-extract... /usr/bin/intltool-extract
checking for xgettext... (cached) /usr/bin/xgettext
checking for msgmerge... /usr/bin/msgmerge
checking for msgfmt... (cached) /usr/bin/msgfmt
checking for gmsgfmt... (cached) /usr/bin/msgfmt
checking for perl... /usr/bin/perl
checking for XML::Parser... ok
configure: creating ./config.status
config.status: creating bin/Makefile
config.status: creating bin/fwbackups
config.status: creating help/Makefile
config.status: creating pixmaps/Makefile
config.status: creating po/Makefile.in
config.status: creating src/Makefile
config.status: creating src/fwbackups/Makefile
config.status: creating src/fwbackups/operations/Makefile
config.status: creating src/fwbackups/__init__.py
config.status: creating Makefile
config.status: creating fwbackups.spec
config.status: executing depfiles commands
config.status: executing default-1 commands
config.status: executing po/stamp-it commands
# INTLTOOL_MAKEFILE
chmacka@chmacka-desktop:~/Desktop/Downloads/fwbackups/fwbackups-1.43.2-1.fc9.src/fwbackups-1.43.2/fwbackups-1.43.3rc2$ sudo make
cd . && /bin/bash /home/chmacka/Desktop/Downloads/fwbackups/fwbackups-1.43.2-1.fc9.src/fwbackups-1.43.2/fwbackups-1.43.3rc2/missing --run aclocal-1.10 
configure.ac:18: warning: macro `AM_GLIB_GNU_GETTEXT' not found in library
 cd . && /bin/bash /home/chmacka/Desktop/Downloads/fwbackups/fwbackups-1.43.2-1.fc9.src/fwbackups-1.43.2/fwbackups-1.43.3rc2/missing --run automake-1.10 --gnu 
gnome-doc-utils.make:74: if $(DOC_H_FILE: non-POSIX variable name
gnome-doc-utils.make:74: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:77: if $(DOC_H_FILE: non-POSIX variable name
gnome-doc-utils.make:77: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:110: if $(DOC_USER_FORMATS: non-POSIX variable name
gnome-doc-utils.make:110: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:115: if $(filter environment,$(origin LINGUAS: non-POSIX variable name
gnome-doc-utils.make:115: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:115: filter $(LINGUAS: non-POSIX variable name
gnome-doc-utils.make:115: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:144: shell xmllint --format $(2: non-POSIX variable name
gnome-doc-utils.make:144: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:144: notdir $(patsubst %/$(notdir $(2: non-POSIX variable name
gnome-doc-utils.make:144: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:144: if $(_ENABLE_SK: non-POSIX variable name
gnome-doc-utils.make:144: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:160: if $(DOC_MODULE: non-POSIX variable name
gnome-doc-utils.make:160: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:160: wildcard $(_DOC_ABS_SRCDIR: non-POSIX variable name
gnome-doc-utils.make:160: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:164: if $(_DOC_OMF_IN: non-POSIX variable name
gnome-doc-utils.make:164: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:164: foreach lc,C $(_DOC_REAL_LINGUAS: non-POSIX variable name
gnome-doc-utils.make:164: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:173: call db2omf_args,$@,$<,'docbook': non-POSIX variable name
gnome-doc-utils.make:173: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:177: if $(_DOC_OMF_IN: non-POSIX variable name
gnome-doc-utils.make:177: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:177: foreach lc,C $(_DOC_REAL_LINGUAS: non-POSIX variable name
gnome-doc-utils.make:177: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:188: call db2omf_args,$@,$<,'xhtml': non-POSIX variable name
gnome-doc-utils.make:188: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:193: if $(filter docbook,$(_DOC_REAL_FORMATS: non-POSIX variable name
gnome-doc-utils.make:193: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:193: if $(filter html HTML,$(_DOC_REAL_FORMATS: non-POSIX variable name
gnome-doc-utils.make:193: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:206: if $(DOC_MODULE: non-POSIX variable name
gnome-doc-utils.make:206: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:210: foreach ent,$(DOC_ENTITIES: non-POSIX variable name
gnome-doc-utils.make:210: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:214: foreach inc,$(DOC_INCLUDES: non-POSIX variable name
gnome-doc-utils.make:214: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:230: if $(DOC_FIGURES: non-POSIX variable name
gnome-doc-utils.make:230: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:230: foreach fig,$(DOC_FIGURES: non-POSIX variable name
gnome-doc-utils.make:230: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:230: patsubst $(srcdir: non-POSIX variable name
gnome-doc-utils.make:230: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:230: wildcard $(srcdir: non-POSIX variable name
gnome-doc-utils.make:230: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:237: foreach f,                        \
gnome-doc-utils.make:237:     $(shell xsltproc --xinclude             \
gnome-doc-utils.make:237:       --stringparam db.chunk.basename "$(DOC_MODULE: non-POSIX variable name
gnome-doc-utils.make:237: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:248: if $(DOC_MODULE: non-POSIX variable name
gnome-doc-utils.make:248: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:248: foreach lc,$(_DOC_REAL_LINGUAS: non-POSIX variable name
gnome-doc-utils.make:248: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:256: if $(DOC_MODULE: non-POSIX variable name
gnome-doc-utils.make:256: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:256: foreach lc,$(_DOC_REAL_LINGUAS: non-POSIX variable name
gnome-doc-utils.make:256: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:261: foreach lc,$(_DOC_REAL_LINGUAS: non-POSIX variable name
gnome-doc-utils.make:261: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:261: foreach inc,$(_DOC_C_INCLUDES: non-POSIX variable name
gnome-doc-utils.make:261: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:261: notdir $(inc: non-POSIX variable name
gnome-doc-utils.make:261: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:268: foreach lc,$(_DOC_REAL_LINGUAS: non-POSIX variable name
gnome-doc-utils.make:268: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:268: foreach doc,$(_DOC_C_HTML: non-POSIX variable name
gnome-doc-utils.make:268: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:268: notdir $(doc: non-POSIX variable name
gnome-doc-utils.make:268: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:274: if $(filter html HTML,$(_DOC_REAL_FORMATS: non-POSIX variable name
gnome-doc-utils.make:274: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:280: foreach lc,$(_DOC_REAL_LINGUAS: non-POSIX variable name
gnome-doc-utils.make:280: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:280: patsubst C/%,$(lc: non-POSIX variable name
gnome-doc-utils.make:280: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:283: foreach fig,$(_DOC_C_FIGURES: non-POSIX variable name
gnome-doc-utils.make:283: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:283: foreach lc,C $(_DOC_REAL_LINGUAS: non-POSIX variable name
gnome-doc-utils.make:283: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:283: wildcard $(srcdir: non-POSIX variable name
gnome-doc-utils.make:283: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:283: patsubst C/%,%,$(fig: non-POSIX variable name
gnome-doc-utils.make:283: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:288: dir $@: non-POSIX variable name
gnome-doc-utils.make:288: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:318: dir $@: non-POSIX variable name
gnome-doc-utils.make:318: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:319: notdir $@: non-POSIX variable name
gnome-doc-utils.make:319: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:328: if $(DOC_MODULE: non-POSIX variable name
gnome-doc-utils.make:328: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:340: if $(filter html HTML,$(_DOC_REAL_FORMATS: non-POSIX variable name
gnome-doc-utils.make:340: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:343: foreach lc,C $(_DOC_REAL_LINGUAS: non-POSIX variable name
gnome-doc-utils.make:343: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:346: patsubst %.xhtml,%.xml,$@: non-POSIX variable name
gnome-doc-utils.make:346: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:385: if $(_DOC_OMF_IN: non-POSIX variable name
gnome-doc-utils.make:385: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:386: if $(_DOC_DSK_IN: non-POSIX variable name
gnome-doc-utils.make:386: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:387: if $(_DOC_REAL_LINGUAS: non-POSIX variable name
gnome-doc-utils.make:387: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:388: if $(DOC_MODULE: non-POSIX variable name
gnome-doc-utils.make:388: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
gnome-doc-utils.make:505: patsubst C/%,%,$(_DOC_C_FIGURES: non-POSIX variable name
gnome-doc-utils.make:505: (probably a GNU make extension)
help/Makefile.am:1:   `gnome-doc-utils.make' included from here
cd . && /bin/bash /home/chmacka/Desktop/Downloads/fwbackups/fwbackups-1.43.2-1.fc9.src/fwbackups-1.43.2/fwbackups-1.43.3rc2/missing --run autoconf
configure.ac:18: error: possibly undefined macro: AM_GLIB_GNU_GETTEXT
      If this token and others are legitimate, please use m4_pattern_allow.
      See the Autoconf documentation.
make: *** [configure] Error 1
chmacka@chmacka-desktop:~/Desktop/Downloads/fwbackups/fwbackups-1.43.2-1.fc9.src/fwbackups-1.43.2/fwbackups-1.43.3rc2$ sudo make install
/bin/bash ./config.status --recheck
running CONFIG_SHELL=/bin/bash /bin/bash ./configure --prefix=/usr --datadir=/usr/share --no-create --no-recursion
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for a Python interpreter with version >= 2.4... python
checking for python... /usr/bin/python
checking for python version... 2.6
checking for python platform... linux2
checking for python script directory... /usr/lib/python2.6/dist-packages
checking for python extension module directory... /usr/lib/python2.6/dist-packages
checking whether ln -s works... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
./configure: line 2759: AM_GLIB_GNU_GETTEXT: command not found
checking whether NLS is requested... yes
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... none
checking for intltool-update... /usr/bin/intltool-update
checking for intltool-merge... /usr/bin/intltool-merge
checking for intltool-extract... /usr/bin/intltool-extract
checking for xgettext... /usr/bin/xgettext
checking for msgmerge... /usr/bin/msgmerge
checking for msgfmt... /usr/bin/msgfmt
checking for gmsgfmt... /usr/bin/msgfmt
checking for perl... /usr/bin/perl
checking for perl >= 5.8.1... 5.10.0
checking for XML::Parser... ok
configure: creating ./config.status
 /bin/bash ./config.status
config.status: creating bin/Makefile
config.status: creating bin/fwbackups
config.status: creating help/Makefile
config.status: creating pixmaps/Makefile
config.status: creating po/Makefile.in
config.status: creating src/Makefile
config.status: creating src/fwbackups/Makefile
config.status: creating src/fwbackups/operations/Makefile
config.status: creating src/fwbackups/__init__.py
config.status: creating Makefile
config.status: creating fwbackups.spec
config.status: executing depfiles commands
config.status: executing po/stamp-it commands
Making install in bin
make[1]: Entering directory `/home/chmacka/Desktop/Downloads/fwbackups/fwbackups-1.43.2-1.fc9.src/fwbackups-1.43.2/fwbackups-1.43.3rc2/bin'
make[2]: Entering directory `/home/chmacka/Desktop/Downloads/fwbackups/fwbackups-1.43.2-1.fc9.src/fwbackups-1.43.2/fwbackups-1.43.3rc2/bin'
make[2]: Nothing to be done for `install-exec-am'.
/bin/bash /home/chmacka/Desktop/Downloads/fwbackups/fwbackups-1.43.2-1.fc9.src/fwbackups-1.43.2/fwbackups-1.43.3rc2/install-sh -d /usr/bin
/usr/bin/install -c -m 755 fwbackups /usr/bin/fwbackups
/usr/bin/install -c -m 755 fwbackups-run.py /usr/bin/fwbackups-run
/usr/bin/install -c -m 755 fwbackups-runonce.py /usr/bin/fwbackups-runonce
make[2]: Leaving directory `/home/chmacka/Desktop/Downloads/fwbackups/fwbackups-1.43.2-1.fc9.src/fwbackups-1.43.2/fwbackups-1.43.3rc2/bin'
make[1]: Leaving directory `/home/chmacka/Desktop/Downloads/fwbackups/fwbackups-1.43.2-1.fc9.src/fwbackups-1.43.2/fwbackups-1.43.3rc2/bin'
Making install in help
make[1]: Entering directory `/home/chmacka/Desktop/Downloads/fwbackups/fwbackups-1.43.2-1.fc9.src/fwbackups-1.43.2/fwbackups-1.43.3rc2/help'
make[2]: Entering directory `/home/chmacka/Desktop/Downloads/fwbackups/fwbackups-1.43.2-1.fc9.src/fwbackups-1.43.2/fwbackups-1.43.3rc2/help'
make[2]: Nothing to be done for `install-exec-am'.
/bin/bash /home/chmacka/Desktop/Downloads/fwbackups/fwbackups-1.43.2-1.fc9.src/fwbackups-1.43.2/fwbackups-1.43.3rc2/install-sh -d /usr/share/gnome/help/fwbackups/C
/usr/bin/install -c -m 644 C/fdl.xml /usr/share/gnome/help/fwbackups/C/fdl.xml
/usr/bin/install -c -m 644 C/gpl.xml /usr/share/gnome/help/fwbackups/C/gpl.xml
/usr/bin/install -c -m 644 C/fwbackups.xml /usr/share/gnome/help/fwbackups/C/fwbackups.xml
/usr/bin/install -c -m 644 C/figures/backup_sets_page.png /usr/share/gnome/help/fwbackups/C/figures/backup_sets_page.png
/usr/bin/install -c -m 644 C/figures/configure_backup_remote.png /usr/share/gnome/help/fwbackups/C/figures/configure_backup_remote.png
/usr/bin/install -c -m 644 C/figures/onetime_configuration.png /usr/share/gnome/help/fwbackups/C/figures/onetime_configuration.png
/usr/bin/install -c -m 644 C/figures/prefs_refresh.png /usr/share/gnome/help/fwbackups/C/figures/prefs_refresh.png
/usr/bin/install -c -m 644 C/figures/restore.png /usr/share/gnome/help/fwbackups/C/figures/restore.png
/usr/bin/install -c -m 644 C/figures/notification.png /usr/share/gnome/help/fwbackups/C/figures/notification.png
/bin/bash /home/chmacka/Desktop/Downloads/fwbackups/fwbackups-1.43.2-1.fc9.src/fwbackups-1.43.2/fwbackups-1.43.3rc2/install-sh -d /usr/share/omf/fwbackups
/usr/bin/install -c -m 644 fwbackups-C.omf /usr/share/omf/fwbackups/fwbackups-C.omf
/usr/bin/install: cannot stat `fwbackups-C.omf': No such file or directory
make[2]: *** [install-doc-omf] Error 1
make[2]: Leaving directory `/home/chmacka/Desktop/Downloads/fwbackups/fwbackups-1.43.2-1.fc9.src/fwbackups-1.43.2/fwbackups-1.43.3rc2/help'
make[1]: *** [install-am] Error 2
make[1]: Leaving directory `/home/chmacka/Desktop/Downloads/fwbackups/fwbackups-1.43.2-1.fc9.src/fwbackups-1.43.2/fwbackups-1.43.3rc2/help'
make: *** [install-recursive] Error 1
chmacka@chmacka-desktop:~/Desktop/Downloads/fwbackups/fwbackups-1.43.2-1.fc9.src/fwbackups-1.43.2/fwbackups-1.43.3rc2$ fwbackups
bash: fwbackups: command not found
chmacka@chmacka-desktop:~/Desktop/Downloads/fwbackups/fwbackups-1.43.2-1.fc9.src/fwbackups-1.43.2/fwbackups-1.43.3rc2$ 

```

---

### Post by firewing1 on 2009-08-02
Hrm, I'm not sure what's going on now. It's very odd that your system could compile it the first time but not now. I'm going to release 1.43.3rc3 (fully tested on Ubuntu) very soon, if you want I'll let you know when it comes out.

---

### Post by chmacka on 2009-08-02
O. K. then. Let me now when it's released, if it's not a problem. Thank you very much!

---

### Post by firewing1 on 2009-08-05
> **chmacka said:**
> O. K. then. Let me now when it's released, if it's not a problem. Thank you very much!
Hi chmacka,

Just wanted to let you know 1.43.3rc3 is out - you can download it [here](http://downloads.diffingo.com/fwbackups/fwbackups-1.43.3rc3.tar.bz2). You'll need the following packages to have it fully working:
[list][*]python (comes with all installations of Ubuntu, no worries)
[*]python-paramiko
[*]python-notify
[*]intltool
[*]gettext
[/list]
Just use this to build fwbackups:```

./configure --prefix=/usr
make && sudo make install
```

---

### Post by chmacka on 2009-08-05
O. K. Thanks!

---

### Post by chmacka on 2009-08-07
I downloaded it and installed it. Everything works great. The only problem is that it is installed not in /usr/bin but in fwbackups folder in /usr/bin (so to open it from terminal I have to do cd /usr/bin/fwbackups and then ./fwbackups and to open it from System > Preferences I have to modify the shortcut from fwbackups to /usr/bin/fwbackups/fwbackups).

But the important thing is - it's working!

---

### Post by martinbaselier on 2009-08-07
That's easily solved. 

**sudo ln -s /usr/bin/fwbackups/fwbackups /bin/fwbackups**

this will create a symbolic link in /bin/, so it's available in your path.

It can't be done in /usr/bin/, since the directory is already named fwbackups.

---

### Post by firewing1 on 2009-08-08
> **chmacka said:**
> I downloaded it and installed it. Everything works great. The only problem is that it is installed not in /usr/bin but in fwbackups folder in /usr/bin (so to open it from terminal I have to do cd /usr/bin/fwbackups and then ./fwbackups and to open it from System > Preferences I have to modify the shortcut from fwbackups to /usr/bin/fwbackups/fwbackups).

But the important thing is - it's working!
Excellent, good to hear it's working. Thanks for letting me know about the sub-directory problem as well, I'll fix that for the final release.

---

### Post by SilverWave on 2009-08-22
Hmm when trying to download I get a Server Not Found Error:
Firefox can't find the server at 
downloads.diffingo.com.

I saw an article on the Top Ten Backup Solutions and fwbackups was top so I thought I would have a look...

Here is my present solution:

[RLB (Rsync Local Backup). An easy way to backup your system RLB This script is the result of wanting a simple backup solution. For this I needed an efficient way of running rsync for local backups.](http://ubuntuforums.org/showthread.php?t=912460)

---

### Post by DBBC on 2011-06-26
I am not sure anybody offered an explanation of Snorbens' question:

> **snorbens said:**
> ...

I did type the name of the program fwbackups in the terminal and it came up with this.

```
mervyn@mervyn-laptop:~$ fwbackups
Traceback (most recent call last):
  File "/usr/share/fwbackups/fwbackups-runapp.pyw", line 34, in <module>
    from fwbackups.const import *
ImportError: No module named fwbackups.const
mervyn@mervyn-laptop:~$ 
```

I have tried both installing from from the downloaded .deb and compiling/installing the tar, both from [http://www.diffingo.com/](http://www.diffingo.com/). 
I did include this:

```
PYTHONVER=$(python -c 'import sys;print "%s.%s" % (sys.version_info[0], sys.version_info[1])')
sudo ln -s ../site-packages/fwbackups /usr/lib/python${PYTHONVER}/dist-packages/fwbackups
```

But whatever I do, I get the same problem as Snorbens did. Any suggestions? I am running Lubuntu 11.04.

At the end of the make/install I got this, could it be a problem?:

```
test -z "/usr/lib/python2.7/dist-packages/fwbackups/operations" || /bin/mkdir -p "/usr/lib/python2.7/dist-packages/fwbackups/operations"
/bin/mkdir: cannot create directory `/usr/lib/python2.7/dist-packages/fwbackups': File exists
make[2]: *** [install-pyPYTHON] Error 1
make[2]: Leaving directory `/home/david12/Downloads/fwbackups-1.43.4/src/fwbackups/operations'
make[1]: *** [install-am] Error 2
make[1]: Leaving directory `/home/david12/Downloads/fwbackups-1.43.4/src/fwbackups/operations'
make: *** [install-recursive] Error 1
```

Any advice will be much appreciated.

---

### Post by davenir on 2011-11-30
I've been using fwbackups for years and love it. Hovever afterupgrading ubuntu last week it's stopped running. I removed it and reinstalled every way I know including following instructions here: [http://www.diffingo.com/oss/fwbackups/documentation/installation#windows](http://www.diffingo.com/oss/fwbackups/documentation/installation#windows)
..but I'm getting exactly the same coompile errors.

I really want to continue using fwbackups but I'm completely stumped!

[HTML]make[1]: Entering directory `/root/fwbackups-1.43.4/pixmaps'
make[2]: Entering directory `/root/fwbackups-1.43.4/pixmaps'
make[2]: Nothing to be done for `install-exec-am'.
/bin/bash /root/fwbackups-1.43.4/install-sh -d /usr/share/pixmaps/
/bin/bash /root/fwbackups-1.43.4/install-sh -d /usr/share/fwbackups/
/usr/bin/install -c -m 644 fwbackups.svg /usr/share/pixmaps/fwbackups.svg
/usr/bin/install -c -m 644 fwbackups-32.png /usr/share/fwbackups/fwbackups.png
make[2]: Leaving directory `/root/fwbackups-1.43.4/pixmaps'
make[1]: Leaving directory `/root/fwbackups-1.43.4/pixmaps'
Making install in src
make[1]: Entering directory `/root/fwbackups-1.43.4/src'
make[2]: Entering directory `/root/fwbackups-1.43.4/src'
make[2]: Nothing to be done for `install-exec-am'.
/bin/bash /root/fwbackups-1.43.4/install-sh -d /usr/share/applications
/usr/bin/install -c -m 644 fwbackups.desktop /usr/share/applications/fwbackups.desktop
test -z "/usr/share/fwbackups" || /bin/mkdir -p "/usr/share/fwbackups"
 /usr/bin/install -c -m 644 BugReport.glade cronwriter.py fwbackups.glade fwbackups-autostart.desktop fwbackups-runapp.pyw '/usr/share/fwbackups'
make[2]: Leaving directory `/root/fwbackups-1.43.4/src'
make[1]: Leaving directory `/root/fwbackups-1.43.4/src'
Making install in src/fwbackups/operations
make[1]: Entering directory `/root/fwbackups-1.43.4/src/fwbackups/operations'
make[2]: Entering directory `/root/fwbackups-1.43.4/src/fwbackups/operations'
make[2]: Nothing to be done for `install-exec-am'.
test -z "/usr/lib/python2.7/dist-packages/fwbackups/operations" || /bin/mkdir -p "/usr/lib/python2.7/dist-packages/fwbackups/operations"
/bin/mkdir: cannot create directory `/usr/lib/python2.7/dist-packages/fwbackups': File exists
make[2]: *** [install-pyPYTHON] Error 1
make[2]: Leaving directory `/root/fwbackups-1.43.4/src/fwbackups/operations'
make[1]: *** [install-am] Error 2
make[1]: Leaving directory `/root/fwbackups-1.43.4/src/fwbackups/operations'
make: *** [install-recursive] Error 1
root@ave1:~/fwbackups-1.43.4# PYTHONVER=$(python -c 'import sys;print "%s.%s" % (sys.version_info[0], sys.version_info[1])')
root@ave1:~/fwbackups-1.43.4# ln -s ../site-packages/fwbackups /usr/lib/python${PYTHONVER}/dist-packages/fwbackups
ln: creating symbolic link `/usr/lib/python2.7/dist-packages/fwbackups': File exists[/HTML]

---

