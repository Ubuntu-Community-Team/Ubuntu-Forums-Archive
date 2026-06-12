---
title: "Need help with Gnome-Mud."
date: 2008-03-27
forum: Gaming &amp; Leisure
---

### Post by Grimhound on 2008-03-27
I'm trying to install Gnome-Mud, but I'm completely inept still when it comes to installing programs and such under Linux. Attempting to work around it, and trying ti ./configure, it says I'm lacking something called GTK+. Can anyone help me?

Question #2:I just tried to install Tinyfugue using sudo apt-get tf. What do I do now?

---

### Post by Perfect Storm on 2008-03-28
You need to install the right -devs/headers to compile it. In this case it needs libgtk2 -dev installed. Then you search synaptic for it and install it. Keep a close eye of the output of the configure.

> Question #2:I just tried to install Tinyfugue using sudo apt-get tf. What do I do now?

try with **tf** in the terminal.

---

### Post by Grimhound on 2008-03-28
It's saying:

[B]configure: error: Package requirements (libgnome-2.0 >= 2.0.0
                                          libgnomeui-2.0 >= 2.0.0
                                          vte >= 0.10.26
                                          libglade-2.0 >= 2.0.1) were not met.
Consider adjusting the PKG_CONFIG_PATH environment variable if you installed software with a non-standard prefix.

Alternatively you may set the GMUD_CFLAGS and GMUD_LIBS environment variables to avoid the need to call pkg-config. See the pkg-config man page for more details.
[/B]
(No typos, it literally says man page.)

So, what should I do?

---

### Post by lswest on 2008-03-28
```
man pkg-config
```
man=manuals page, and is a command you can use to view documentation.

apart from that, not much i can help you with, i'm not entirely sure what you're trying to do, AI can probably help you out more than i could.

---

### Post by Perfect Storm on 2008-03-28
> It's saying:

[B]configure: error: Package requirements (libgnome-2.0 >= 2.0.0
                                         

libgnome-dev


 > libgnomeui-2.0 >= 2.0.0
libgnomeui-dev
> 
                                          vte >= 0.10.26

libvte-dev

 > libglade-2.0 >= 2.0.1) were not met.

libglade2-dev



Note, as you can see it needs the -dev packages.

---

### Post by Grimhound on 2008-03-28
> **lswest said:**
> ```
man pkg-config
```
man=manuals page, and is a command you can use to view documentation.

apart from that, not much i can help you with, i'm not entirely sure what you're trying to do, AI can probably help you out more than i could.

In the long term, I'm trying to find a MUD client that works like one from Windows with its own program window and the black background/white text and trigger settings available.

In the short term, I'm trying to figure out how to install those I can find, as each one seems particularly difficult to figure out.

I'd like to try Trebuchet, found here:
[http://www.belfry.com/fuzzball/trebuchet/#WhereGetIt](http://www.belfry.com/fuzzball/trebuchet/#WhereGetIt)

But I can't figure out which file I need to download, and how to install it, being a novice to Linux.

Until I figure it out, I'm installing all MUD clients I can find in the hopes of eventually figuring out before the next version of Ubuntu comes out so I can do a clean wipe.

Currently, I'm trying to get GNOME-MUD working.

---

### Post by Grimhound on 2008-03-28
Annnd... now I'm completely lost.

God, isn't there any program that doesn't kill itself in Linux?

---

### Post by Perfect Storm on 2008-03-28
Just install the packages I posted.

---

### Post by lswest on 2008-03-28
what the error messages were telling you was that there were packages missing that are required for the program to run, and it suggested you look at a man page for more info on how to tweak something.  By installing the packages AI listed will solve the problem of being missing packages, and then the man page might give you some insight into tweaking whatever it is that isn't quite working.  However, after installing the packages you probably won't have to bother read the man page.

---

### Post by Grimhound on 2008-03-28
> **Artificial Intelligence said:**
> Just install the packages I posted.

I did, and I continued with the compiler thing.

./configure
make
make check
make install

And now I'm lost. Nothing shows up, and the directions swerve off into the sunset of Tripoli.

---

### Post by Perfect Storm on 2008-03-28
Post or attach the output.

---

### Post by Grimhound on 2008-03-28
I'll attach the instructions first, as the output appears as just 600 lines of error messages to me.

I'm about to give up on this. I'm trying to learn how Linux works, but installing a simple text-based program shouldn't be a task. @_@

---

### Post by Perfect Storm on 2008-03-28
It's because you aren't familiar with it ;) ...you'll be in time just hang in :KS

You attached the readme file, I need the in/output of the terminal.

---

### Post by Grimhound on 2008-03-28
> **Artificial Intelligence said:**
> It's because you aren't familiar with it ;) ...you'll be in time just hang in :KS

You attached the readme file, I need the in/output of the terminal.

Alright. Attached.

The results of:
./configure
make
make check
make install

---

### Post by Perfect Storm on 2008-03-28
> checking for Python version >= 2.x... yes, Python 2.5
checking for Python compile flags... Can't find Python.h

```
sudo aptitude install python2.5-dev
```

cd into the gnome-mud-0.10.7, then;
```
make clean
```

Then do it the compiling again, when you come to the **make install** you need to put **sudo** infront 
```
sudo make install
```

sudo means superuser do. It's needed to make changes/editing the system.
The system is like the "core" where each user(s) are "attached" with their own home. (simplfied explaination)

---

### Post by Grimhound on 2008-03-28
It just got to:
wyrmkin@hoard-02:~/gnome-mud-0.10.7$ sudo make install
Making install in doc
make[1]: Entering directory `/home/wyrmkin/gnome-mud-0.10.7/doc'
Making install in gnome-mud-manual
make[2]: Entering directory `/home/wyrmkin/gnome-mud-0.10.7/doc/gnome-mud-manual'
Making install in C
make[3]: Entering directory `/home/wyrmkin/gnome-mud-0.10.7/doc/gnome-mud-manual/C'
make[4]: Entering directory `/home/wyrmkin/gnome-mud-0.10.7/doc/gnome-mud-manual/C'
make[4]: Nothing to be done for `install-exec-am'.
for file in gnome-mud-manual-C.omf; do \
          scrollkeeper-preinstall /usr/local/share/gnome/help/gnome-mud/C/`awk 'BEGIN {RS = ">" } /identifier/ {print $0}' ${file} | awk 'BEGIN {FS="\""} /url/ {print $2}'` ${file} ../../../doc/omf-install/${file}; \
        done
touch omf_timestamp
/bin/bash ../../../mkinstalldirs /usr/local/share/gnome/help/gnome-mud/C/figures
mkdir -p -- /usr/local/share/gnome/help/gnome-mud/C/figures
cp ./ gnome-mud-manual.xml /usr/local/share/gnome/help/gnome-mud/C
cp: omitting directory `./'
make[4]: [install-data-am] Error 1 (ignored)
for file in ./figures/*.png; do \
          basefile=`echo $file | sed -e  's,^.*/,,'`; \
          /usr/bin/install -c -m 644 $file /usr/local/share/gnome/help/gnome-mud/C/figures/$basefile; \
        done
if [ -e ./topic.dat ]; then \
                /usr/bin/install -c -m 644 ./topic.dat /usr/local/share/gnome/help/gnome-mud/C; \
         fi
make[4]: Leaving directory `/home/wyrmkin/gnome-mud-0.10.7/doc/gnome-mud-manual/C'
make[3]: Leaving directory `/home/wyrmkin/gnome-mud-0.10.7/doc/gnome-mud-manual/C'
make[3]: Entering directory `/home/wyrmkin/gnome-mud-0.10.7/doc/gnome-mud-manual'
make[4]: Entering directory `/home/wyrmkin/gnome-mud-0.10.7/doc/gnome-mud-manual'
make[4]: Nothing to be done for `install-exec-am'.
make[4]: Nothing to be done for `install-data-am'.
make[4]: Leaving directory `/home/wyrmkin/gnome-mud-0.10.7/doc/gnome-mud-manual'
make[3]: Leaving directory `/home/wyrmkin/gnome-mud-0.10.7/doc/gnome-mud-manual'
make[2]: Leaving directory `/home/wyrmkin/gnome-mud-0.10.7/doc/gnome-mud-manual'
Making install in gnome-mud-plugin-api
make[2]: Entering directory `/home/wyrmkin/gnome-mud-0.10.7/doc/gnome-mud-plugin-api'
Making install in C
make[3]: Entering directory `/home/wyrmkin/gnome-mud-0.10.7/doc/gnome-mud-plugin-api/C'
make[4]: Entering directory `/home/wyrmkin/gnome-mud-0.10.7/doc/gnome-mud-plugin-api/C'
make[4]: Nothing to be done for `install-exec-am'.
for file in gnome-mud-plugin-api-C.omf; do \
          scrollkeeper-preinstall /usr/local/share/gnome/help/gnome-mud/C/`awk 'BEGIN {RS = ">" } /identifier/ {print $0}' ${file} | awk 'BEGIN {FS="\""} /url/ {print $2}'` ${file} ../../../doc/omf-install/${file}; \
        done
touch omf_timestamp
/bin/bash ../../../mkinstalldirs /usr/local/share/gnome/help/gnome-mud/C/figures
cp ./monitor.py gnome-mud-plugin-api.xml /usr/local/share/gnome/help/gnome-mud/C
for file in ./figures/*.png; do \
          basefile=`echo $file | sed -e  's,^.*/,,'`; \
          /usr/bin/install -c -m 644 $file /usr/local/share/gnome/help/gnome-mud/C/figures/$basefile; \
        done
/usr/bin/install: target `/usr/local/share/gnome/help/gnome-mud/C/figures/profiles-window.png' is not a directory
make[4]: [install-data-am] Error 1 (ignored)
if [ -e ./topic.dat ]; then \
                /usr/bin/install -c -m 644 ./topic.dat /usr/local/share/gnome/help/gnome-mud/C; \
         fi
make[4]: Leaving directory `/home/wyrmkin/gnome-mud-0.10.7/doc/gnome-mud-plugin-api/C'
make[3]: Leaving directory `/home/wyrmkin/gnome-mud-0.10.7/doc/gnome-mud-plugin-api/C'
make[3]: Entering directory `/home/wyrmkin/gnome-mud-0.10.7/doc/gnome-mud-plugin-api'
make[4]: Entering directory `/home/wyrmkin/gnome-mud-0.10.7/doc/gnome-mud-plugin-api'
make[4]: Nothing to be done for `install-exec-am'.
make[4]: Nothing to be done for `install-data-am'.
make[4]: Leaving directory `/home/wyrmkin/gnome-mud-0.10.7/doc/gnome-mud-plugin-api'
make[3]: Leaving directory `/home/wyrmkin/gnome-mud-0.10.7/doc/gnome-mud-plugin-api'
make[2]: Leaving directory `/home/wyrmkin/gnome-mud-0.10.7/doc/gnome-mud-plugin-api'
Making install in omf-install
make[2]: Entering directory `/home/wyrmkin/gnome-mud-0.10.7/doc/omf-install'
make[3]: Entering directory `/home/wyrmkin/gnome-mud-0.10.7/doc/omf-install'
make[3]: Nothing to be done for `install-exec-am'.
/bin/bash ../../mkinstalldirs /usr/local/share/omf/gnome-mud
mkdir -p -- /usr/local/share/omf/gnome-mud
for file in ./*.omf; do \
                /usr/bin/install -c -m 644 ./$file /usr/local/share/omf/gnome-mud; \
        done
scrollkeeper-update -p /usr/local/var/scrollkeeper 
scrollkeeper-update: warning: /usr/share/omf/workspace-switcher/workspace-switcher-de.omf overrides /usr/share/omf/gnome-panel/workspace-switcher-de.omf
scrollkeeper-update: warning: /usr/share/omf/gnome-panel/window-list-de.omf overrides /usr/share/omf/window-list/window-list-de.omf

And then froze...

---

### Post by Perfect Storm on 2008-03-28
give it some time, it may be thinking (I dunno how fast your computer is).

---

### Post by Grimhound on 2008-03-28
> **Artificial Intelligence said:**
> Post or attach the output.

Alright. It finished up, and the program icon appears, but it says:

Could not launch menu item
Failed to execute child process "gnome-mud" (No such file or directory)

---

### Post by Perfect Storm on 2008-03-28
first try with 
```
gnome-mud
```

if it doesn't work;

do a:
```
whereis gnome-mud
locate gnome-mud
```

---

### Post by Grimhound on 2008-03-28
Alright. Got that one working.

Thanks for all your help.

Would you happen to know which of these files I'd need to test the next one out?
[http://www.belfry.com/fuzzball/trebuchet/#WhereGetIt](http://www.belfry.com/fuzzball/trebuchet/#WhereGetIt)

---

### Post by Perfect Storm on 2008-03-28
trebuchet-1.067.tar.gz

---

### Post by Grimhound on 2008-03-28
> **Artificial Intelligence said:**
> trebuchet-1.067.tar.gz

Alright. Downloaded that. Tried things, didn't work.

[B]Install instructions:
UNIX/LINUX INSTALLATION:



    This assumes that you already have TCL/Tk (AKA 'wish') already installed

    on your unix/linux system, and that the 'wish' program is in your $PATH.

    If you don't have wish installed, you will want to either get the TCL/Tk

    packages from your OS vendor (RedHat, Debian, etc.) or you may fetch the

    sources from [www.scriptics.com](www.scriptics.com).  You need TCL/Tk version 8.0.5 or later.



    Un-gzip the tarfile:

        gunzip TrebTk10aXX.tar.gz



    Untar the tarfile:

        tar xf TrebTk10aXX.tar



    Move the directory structure that you unpacked to someplace convenient:

        mv TrebTk10aXX /usr/local/trebtk



    Make a softlink from a convenient directory that is in your $PATH, linking

    to the Trebuchet.tcl file:

        cd /usr/local/bin

        ln -s /usr/local/trebtk/Trebuchet.tcl treb



    Then when you want to run Trebuchet, just invoke the 'treb' softlink.

    NOTE:  The Trebuchet.tcl file MUST be located in the same directory as

    the 'lib' and 'docs' directories.  Otherwise it won't be able to find

    the libraries it needs to run.  This is why you make a softlink to the

    Trebuchet.tcl file, instead of moving it.[/B]

Any idea how to make it work? Does Ubuntu already have the TCL/Tk thing?

---

### Post by Perfect Storm on 2008-03-29
No, you need to install them.
```
sudo aptitude install tk8.4
```
(It is dependend on tlc, so it will automatically grab it)

unpack the package, and cd into the unpack folder.
then (from what I read):

```
mv TrebTk10aXX /usr/local/trebtk
 cd /usr/local/bin
ln -s /usr/local/trebtk/Trebuchet.tcl treb
cd && treb
```

---

### Post by ComeAlive on 2008-12-06
Hello.
I don't have Ubuntu. I have Fedora, but... I came across this thread and I'm in a similar situation as the person that started the thread.

I ran ./configure. At the end of the output, it says:

> checking for GMUD... configure: error: Package requirements (gtk+-2.0 >= 2.10.0 vte >= 0.11.00 libglade-2.0 >= 2.0.1 libpcre >= 6.0.0 gmodule-2.0 >= 2.0.0 gnet-2.0 >= 0.22 gconf-2.0 >= 0.20) were not met:

No package 'libpcre' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GMUD_CFLAGS
and GMUD_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.


I assume that I need newer versions of gtk+-2.0, vte, libglade-2.0, libpcre, gmodule-2.0, gnet-2.0 and gconf-2.0 BUT, I can't find these things in my package manager.

Any suggestions? From a linux newbie (but one who embraces the philosphy),
thanks.

---

### Post by ComeAlive on 2008-12-06
Is this what is called "dependency hell?"

---

### Post by Grishka on 2008-12-06
> **ComeAlive said:**
> Is this what is called "dependency hell?"

nope. the error message lists all dependencies, not just the ones missing. it looks like you're only missing libpcre development package.

---

### Post by Vadi on 2008-12-06
install libpcre3-dev package (at least its called so in ubuntu, dont know about fedora)

---

