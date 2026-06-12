---
title: "ngspice installation help"
date: 2007-10-30
forum: Education &amp; Science
---

### Post by nuir on 2007-10-30
Hi. I've been using oregano for some simple circuit simulations with gnucap (I really don't need anything more complex right now), and I wanted to try ngspice as the simulation engine.

I checked the ngspice home page first, and they pointed to the ubuntu repository, but I couldn't find any ngspice package in any of the ubuntu repositories (I'm using ubuntu v7.10). So I tried the .deb packages from the ngspice project home page.

I downloaded two files: ngspice[...].deb and xspice[...].deb, but whenever I try to install either of them, I get a "dependency is not satisfiable" error pointing to the exact other package.

I tried to install them through the terminal with the exact same result. Is there something I'm doing wrong? Do I have to use a particular option to install two mutually dependent packages? Or maybe they are in some repository I don't know of...?

I'm not sure how to compile the .tar packages, and I couldn't find any more info in the home page...  maybe that's the only option I'm left with. So if somebody could please tell me how to compile a package, maybe a link to a tutorial or something like that, it'd be really helpful (especially 'cause it seems I'll be compiling many other things in the future)

---

### Post by DarkW0lf on 2007-11-11
I have hit the same problem.

They were listed in 7.04 but I can't find them in 7.10 repos. :(
gEDA docs seem to indicate that ngspice is included in the packages but I haven't been able to verify that.

I am trying to get started in Electronics Design in Linux, so I hope to get the circuit simulation working.

---

### Post by Twister594 on 2008-02-05
I managed to get the two debs to install by installing them using the command line.

For example:

```
sudo dpkg -i xspice_17.0.0-1_i386.deb
sudo dpkg -i ngspice_17.0.0-1_i386.deb
```

That should work, if not, I tried install both with only one dpkg -i command and had to go back and take care of ngspice.

I hope this helps.

---

### Post by Twister594 on 2008-02-11
Hi everyone, I created an installer script that will install the packages for you.

You can get it here:
[NG SPICE INSTALLER ZIP]("http://filer.case.edu/car44/ngspice/NGSPICEINSTALL.zip")

In this package is also a test file.

After double clicking and executing the .sh file and entering your password, it will install xspice and ngspice for you.

To test if your installation was successful, I've included a test file - amplifier0.cir

To run this, enter into a terminal:

```
ngspice "LOCATION OF THE TEST FILE"
```

You could just type ngspice into a terminal followed by a space and then drag the file in, this will fill in the location and name of the test file for you.

I'm sorry that the test bit isn't very clear, but the installer will work fine.

---

### Post by abrie on 2008-02-12
what worked for me is the following:

Get the ngspice and xspice .deb files (they're contained in NG SPICE INSTALLER ZIP posted by Twister594.)

Then type in your console:

dpkg -i 'path to ngspice file' --force-all
dpkg -i 'path to xspice file' --force-all


The reason this worked for me is that it wouldn't install because the two packages were mutually dependent, and the one wouldn't install without the other one already being installed, so if you just force it to install regardless of the dependencies it works! You can then try the test file in Twister594's script. [Thanks for the script man!]

---

### Post by DarkW0lf on 2008-02-29
So xsoice and ngspice are still available just removed from the repos ?
Did you download those from packages.ubuntu.com (puc) ?

What is up with the repos ?
gspiceui is listed at puc but I can't find it in Synaptic.

---

### Post by Twister594 on 2008-02-29
I tracked down the deb files from source forge.

[SourceForge]("http://sourceforge.net/project/showfiles.php?group_id=38962&package_id=31152")

These files are under 17.binary.32bit

I used ngspice....deb and xspice....deb

---

### Post by carlosalvatore on 2008-03-27
> **abrie said:**
> what worked for me is the following:

Get the ngspice and xspice .deb files (they're contained in NG SPICE INSTALLER ZIP posted by Twister594.)

Then type in your console:

dpkg -i 'path to ngspice file' --force-all
dpkg -i 'path to xspice file' --force-all


The reason this worked for me is that it wouldn't install because the two packages were mutually dependent, and the one wouldn't install without the other one already being installed, so if you just force it to install regardless of the dependencies it works! You can then try the test file in Twister594's script. [Thanks for the script man!]


Sorry but i think the way to get it works is this one... at least it works for me...
```
sudo dpkg --force-all -i xspice_17.0.0-1_i386.deb
sudo dpkg --force-all -i ngspice_17.0.0-1_i386.deb

```
Greetings!

---

### Post by mafifk on 2008-05-13
Sorry, typing error (See below)

---

### Post by mafifk on 2008-05-14
Hello,
You can compile it by yourself.
First download the source at:
[HTML]http://sourceforge.net/project/showfiles.php?group_id=38962&package_id=31152[/HTML]
Download the: ng-spice-rework-17.tar.gz  or the latest.
Download from Synaptic:
libgtk2.0-dev(with all the component highlight)
libxaw7-dev(with all the component highlight)
libxaw7-header(with all the component highlight)
Go to the directory of ngspice.
```
$ aclocal
```
```
$ ./autogen.sh
```
```
$ ./configure --enable-xgraph
```
```
$ make
```
```
$ sudo make install
```
Walla...
It will work...
Please PM me if it don't work.:KS

---

### Post by reinderien on 2008-07-08
> **Twister594 said:**
> ```
sudo dpkg -i xspice_17.0.0-1_i386.deb
sudo dpkg -i ngspice_17.0.0-1_i386.deb
```
Even when I tried that I get a circular dependency. The only way I got it to work was to do it all at once, to the tune of
```
sudo dpkg -i *.deb
```
(assuming xspice and ngspice are the only debs in the directory.)

---

### Post by Gndrix on 2008-07-11
> **reinderien said:**
> Even when I tried that I get a circular dependency. The only way I got it to work was to do it all at once, to the tune of
```
sudo dpkg -i *.deb
```
(assuming xspice and ngspice are the only debs in the directory.)

Thanks reinderien, this just worked for me.

---

### Post by Stbhan on 2008-10-11
> **carlosalvatore said:**
> Sorry but i think the way to get it works is this one... at least it works for me...
```
sudo dpkg --force-all -i xspice_17.0.0-1_i386.deb
sudo dpkg --force-all -i ngspice_17.0.0-1_i386.deb

```
Greetings!

Thanks to you all.

I've tried this two senteces and worked fine. I checked with the example provided (good job!) and it worked.

Again, thanks.

---

### Post by bdemers on 2008-10-17
I used this thread to help me install ngspice on my amd64 system.  Downloading the correct set of 'deb files did what I needed.  Just curious, though, where the heck are the installed files?  I searched on both xspice and ngspice without any luck. Yet when I run the test file, it works! so I know they are in there someplace. Sure will be nice when I become a bit more familiar with Linux.

---

### Post by dzaia-bs on 2008-12-23
thanks a lot for your guide,
even though I could not find libgtk2.0-dev and libxaw7-header from synaptic... but it still working :D

> **mafifk said:**
> Hello,
You can compile it by yourself.
First download the source at:
[HTML]http://sourceforge.net/project/showfiles.php?group_id=38962&package_id=31152[/HTML]
Download the: ng-spice-rework-17.tar.gz  or the latest.
Download from Synaptic:
libgtk2.0-dev(with all the component highlight)
libxaw7-dev(with all the component highlight)
libxaw7-header(with all the component highlight)
Go to the directory of ngspice.
```
$ aclocal
```
```
$ ./autogen.sh
```
```
$ ./configure --enable-xgraph
```
```
$ make
```
```
$ sudo make install
```
Walla...
It will work...
Please PM me if it don't work.:KS

---

### Post by a80 on 2009-04-28
Please help the xgraph doesnt work at 9.04. I fount at web that there is a bug.

Is there another program to see plots exept xgraph ?

---

### Post by nuir on 2009-04-29
great posts, thank you very much!

---

### Post by jurusu on 2010-02-26
still unable to install properly in karmic. followed all the instructions given.


******
** ngspice-20 : Circuit level simulation program
** The U. C. Berkeley CAD Group
** Copyright 1985-1994, Regents of the University of California.
** Please submit bug-reports to: [email]ngspice-bugs@lists.sourceforge.net[/email]
** Creation Date: Fri Feb 26 22:38:32 PHT 2010
******
external error:  no graphics interface; please check compiling instructions
ngspice 1 ->

has anyone properly installed this on karmic? 
<sigh>

---

