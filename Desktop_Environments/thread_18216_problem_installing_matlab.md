---
title: "problem installing matlab"
date: 2005-03-05
forum: Desktop Environments
---

### Post by lorap on 2005-03-05
when i try to run "install" script this way:
sudo /media/cdrom0/install
i automaticly get an error message : "Permission denied".
what'd i do to solve this problem?
thanks
pavel

---

### Post by bored2k on 2005-03-05
[QUOTE=lorap]when i try to run "install" script this way:
sudo /media/cdrom0/install
i automaticly get an error message : "Permission denied".
what'd i do to solve this problem?
thanks
pavel[/QUOTE]


ur cdrom is most likely being mounted as if u were on root
proly if u nautilus /mount/cdrom0 as root ud be able to install


not sure but maybe JUST maybe
>  $ sudo mount /dev/hda1 /media/disk -t -o umask=000 
MIGHT work ]that disk dir is made up[


hav u tried mathematica 5 for nix ? it does charms here

---

### Post by paul cooke on 2005-03-05
[QUOTE=lorap]when i try to run "install" script this way:
sudo /media/cdrom0/install
i automaticly get an error message : "Permission denied".
what'd i do to solve this problem?
thanks
pavel[/QUOTE]

have you tried actually cd'ing to that directory and running the program from it instead?

ie 

cd /media/cdrom0
sudo ./install

---

### Post by lorap on 2005-03-05
yup, i've already done that.
the same thing: "permission denied".
thanks friend for the attention.
pavel

---

### Post by GilGalad on 2005-03-05
What about?

sudo sh /media/cdrom0/install

---

### Post by bored2k on 2005-03-05
[QUOTE=GilGalad]What about?

sudo sh /media/cdrom0/install[/QUOTE]

that should work , but then again he would install as root

u can mount the cdrom for rw access to everyone, but to make things easier, u can copy the app to a dir. then change its permissions to "lorap" .

---

### Post by lorap on 2005-03-05
that was also possible, i've checked that.
thank you friend.
pavel

---

### Post by GilGalad on 2005-03-05
[QUOTE=bored2k]that should work , but then again he would install as root

u can mount the cdrom for rw access to everyone, but to make things easier, u can copy the app to a dir. then change its permissions to "lorap" .[/QUOTE]

Hi,

What is the problem with installing it as root? In fact I've done that and I see no problem...

---

### Post by bored2k on 2005-03-05
[QUOTE=GilGalad]Hi,

What is the problem with installing it as root? In fact I've done that and I see no problem...[/QUOTE]


Why would he want to install a non-system-configuration-utility application in a root environment ? 

There's actually no problem, but per say a "desktop icon" or whatever would need the gksudo command, wich requires a passwd right ? [unless u have the Oh so unsafe straight to root]

I say cut the middle man and the tedious passwd input _ _ _


There's no beef with installing as root still , but par example in my case, my $HOME and / are in separate partitions, and i like skipping steps so ...

By the time u read this u couldve already chmod chgroup the dir lol


*edit : sorry if my english/french/spanish mixture ever gets confusing*

---

### Post by GilGalad on 2005-03-05
Sorry, I don't see your point just yet. Then each user should install e.g. firefox in her own home? (my very basic matlab install is 700Mb). You do not neet to be root to run matlab or to create launchers pointing to it (it's like firefox and the other apps in the system). 

It is true though that you want to keep these "manual installed" applications separated from the others (eg, in case you want to reinstall the whole system) and that is what a separated /usr/local partition is for (yeah some day I'll understand why linux distributions advice to create only one big root partition now)

---

### Post by lorap on 2005-03-05
i've it installed but get this error on loading it:

Warning: latest version of matlab app-defaults file not found.
Contact your system administrator to have this file installed.
Warning: Unable to load Java Runtime Environment: libjvm.so: cannot open shared object file: No such file or directory.
Warning: Disabling Java support.
Warning: Could not access OpenGL library

< M A T L A B >
Copyright 1984-2004 The MathWorks, Inc.
Version 7.0.0.19901 (R14)
May 06, 2004

??? Undefined function or variable 'matlabrc'.

pavel

---

### Post by bored2k on 2005-03-05
different POVs . im 2 lazy r`now to start typing.

---

### Post by GilGalad on 2005-03-05
Do you have the files (change /usr/local for your matlab install dir)

/usr/local/matlab7/X11/app-defaults/Matlab
/usr/local/matlab7/sys/java/jre/glnx86/jre1.4.2/lib/i386/client/libjvm.so
/usr/local/matlab7/bin/matlab

and are they user (yours) readable?

---

### Post by acorrigan on 2005-03-11
jre1.4.2/

What JRE is that, an official Sun one?  Or is it blackdown?

I had the exact same problem as the person two posts above.

---

### Post by bored2k on 2005-03-11
[QUOTE=acorrigan]jre1.4.2/

What JRE is that, an official Sun one?  Or is it blackdown?

I had the exact same problem as the person two posts above.[/QUOTE]
 j2re1.5 Is out people, its even apt-gettable [at least for warty].

---

### Post by lorap on 2005-03-12
hi friends!
thank for being trying to help me.
the error message i get once i run install is this:

/media/usb-cdrom/install: line 1: /lib/libc.so.6: Permission denied
/tmp/16415tmwinstall/install: line 1: /lib/libc.so.6: Permission denied

but i did complete installation althou nothing worked cause matlab was unable to write to the /lib directory library files needed.
maybe you know how to solve this problem?
when i break an installation i get this message:

/tmp/6537tmwinstall/install: /media/usb-cdrom/install: /bin/sh: bad interpreter: Permission denied
/tmp/6537tmwinstall/install: line 300: /media/usb-cdrom/install: Success

so if somebody can help you'd make me very happy.
thanks again!
pavel

---

