---
title: "GNUCash 2.2.0"
date: 2007-07-19
forum: Desktop Environments
---

### Post by Banter on 2007-07-19
GNUCash 2.2.0 was released four days ago. Does anyone know when it will make it to the repositories?

Thanks!

---

### Post by Reodge on 2007-07-19
It probably wont make it into the official repository for a release until Gutsy+1, so it will be a while ...

I've been searching around for any 3rd party repositories that have packaged it at all and haven't found anything, so I ended up making my own ones, my first attempt at a proper build :P

You could just try compiling it yourself, otherwise there might be some places that will package it in time ... it is definitely a worthy upgrade, you can move the tabs around! :D

---

### Post by Brentley_11 on 2007-07-21
Has anyone come across a repository yet?  If not, anyone want to maybe help a noob compile it? :D

---

### Post by podfish on 2007-07-24
I have gnucash, gnucash-common, libaqbanking and its friends; these are packages that I just put together over the weekend, including hbci/ofx support.  They're completely untested, but should work.  I managed to import some files, put in some transactions, and whatnot.  Haven't tried anything fancy yet.

u want?

---

### Post by harty83 on 2007-07-29
podfish,

I wouldn't mind them!  Could I snag them from you?

Alan

---

### Post by dholbert on 2007-07-30
To build GnuCash 2.2 on Feisty (it's pretty easy), see the instructions I posted on the GnuCash wiki:

[http://wiki.gnucash.org/wiki/Building#Feisty](http://wiki.gnucash.org/wiki/Building#Feisty)

---

### Post by Banter on 2007-07-31
Thanks everyone for your help! 

really appreciate it

- banter

---

### Post by wedge2k on 2007-08-02
I've ben having a heluva time compiling.   Keeps failing here:

```
checking for SLIB support... configure: error:

   Cannot find SLIB.  Are you sure you have it installed?
   See http://bugzilla.gnome.org/show_bug.cgi?id=347922

```

But its installed, and i even added a simlink to help it along.  Every forum post, bug thread i've looked and tried has come up dry.  Anyone else have this problem?

```
$ aptitude show slib
Package: slib
State: installed
Automatically installed: no
Version: 3a4-4
Priority: optional
Section: universe/devel
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Uncompressed Size: 4047k
Conflicts: libguile9 (<= 1:1.4-26), guile-1.6-libs (<= 1.6.7-1.1), scm (< 5e3)
Description: Portable Scheme library
 SLIB is a portable scheme library meant to provide compatibility and utility functions for all standard scheme implementations.  SLIB includes initialization files
 for Chez, ELK 2.1, GAMBIT, MacScheme, MITScheme, scheme->C, Scheme48, T3.1, and VSCM.  SCM also supports SLIB.

```

```
$ whereis slib
slib: /usr/bin/slib /usr/X11R6/bin/slib /usr/bin/X11/slib /usr/share/slib
```

here's the simlink i made: 
```
/usr/share/guile/site$ ls -la | grep slib
lrwxrwxrwx  1 root root     16 2007-07-18 20:52 slib -> /usr/share/slib/
```

---

### Post by ceelight on 2007-08-03
Yes, I do have exactly the same problem. Any hints how to solve this?
My "dev feisty" - running in QEMU on Feisty ;)

Thanks!

---

### Post by ceelight on 2007-08-03
I've found the solution :)

Install the Package *guile-1.6-slib* and ./configure works.

---

### Post by rbmorse on 2007-08-03
You also need guile-1.6-slib if I remember correctly. 

I could not get Gnucash to build with Guile 1.8 installed.   Works fine with Guile 1.6, though..

---

### Post by helpdeskdan on 2007-08-05
I get: 
make[2]: Entering directory `/home/dan/gnucash-2.2.0/po'
file=`echo ca | sed 's,.*/,,'`.gmo \
          && rm -f $file &&  -o $file ca.po
/bin/sh: -o: not found
make[2]: *** [ca.gmo] Error 127
make[2]: Leaving directory `/home/dan/gnucash-2.2.0/po'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/dan/gnucash-2.2.0'
make: *** [install] Error 2

****  Installation failed. Aborting package creation.

Cleaning up...OK

Bye.


Any ideas much appreciated, thanks.

---

### Post by rbmorse on 2007-08-06
You're missing the gettext utils.

---

### Post by podfish on 2007-08-07
> **harty83 said:**
> podfish,

I wouldn't mind them!  Could I snag them from you?

Alan

I'm very sorry, but I had a hard drive crash event that destroyed that build.  I'll try to rebuild it on my laptop and post it somewhere on the web; i'll link to it here.

I'm submitting it to getdeb.org, too.

---

### Post by helpdeskdan on 2007-08-07
Thank you for the reply, but I am afraid I do have gettext installed and I still get the error. 

Thanks, 
-Dan

---

### Post by rbmorse on 2007-08-07
How odd.

At this point I'd consider posting the problem on the gnucash-users mail list. They're pretty responsive, and pointed me to gettext when I had the identical error. 

[http://wiki.gnucash.org/wiki/Mailing_Lists](http://wiki.gnucash.org/wiki/Mailing_Lists)

---

### Post by atze76 on 2007-08-09
@dholbert, it is a nice step by step tutorial how to install gnucash on ubuntu feisty, but your suggestion to force overwrite of existing files is dangerous. 
After installing the created gnucash .deb package and forcing file overwrite, it messed up my whole environment. Even part of the gcc files were overwritten and I had to reinstall my system.
I think the procedure how to compile and create the .deb package should be reworked....

---

### Post by wedge2k on 2007-08-10
> **ceelight said:**
> I've found the solution :)

Install the Package *guile-1.6-slib* and ./configure works.

I have that package installed, no luck. Althought it was able to compile on another machine, so I'm wondering what's wrong w/ my machine that keeps giving the error.  I've tried reinstalling guile as well, still doesn't help any.

---

### Post by DCToblerone on 2007-08-15
I reinstalled the gettext package, then re-ran ./configure and was able to get it to compile. Now, I am getting this:

dpkg: error processing gnucash_2.2.0-1_i386.deb (--install): trying to overwrite `/usr/lib/libgconf2-4/2/libgconfbackend-xml.so', which is also in package libgconf2-4

I am afraid to use the suggested --force-overwrite option. Has anyone had success with this damaging things?

Dave

---

### Post by helpdeskdan on 2007-08-17
Hum.... thanks for the suggestion, I tried a make clean and did it again and it seems to have worked.  Also, the docs are nice, but they are easy to build.  

Hearing it trashed somebodies system, I'll try it on another; this system is much too important to accidentally trash. This .deb should work on other computers

---

### Post by mazdaracer on 2007-08-17
Per CEELITE's suggestion, I checked that and re-installed but also am still having that same SLIB error trying to install GNUCash 2.2.0. Also tried the wiki: [http://wiki.gnucash.org/wiki/Building#Feisty](http://wiki.gnucash.org/wiki/Building#Feisty) but still get that error. Do I need to uninstall and run it again?

I had built 2.0.5 on my laptop w/o problems. Both systems (lap and desk) were initially 6.0.4 Ubuntu configurations and upgraded online to 7.0.4 with current patches:
root@rotor:/opt/gnucash-2.2.0# uname -a
Linux rotor 2.6.20-16-generic #2 SMP Thu Jun 7 20:19:32 UTC 2007 i686 GNU/Linux

Really would like to have it up on the desktop, since the laptop is the company's that I dual boot.

---

### Post by helpdeskdan on 2007-08-22
The wiki did not work for me.  This line here:

sudo apt-get install build-essential checkinstall guile-1.6-dev guile-1.6-slib libgoffice-0-dev libgtkhtml3.14-dev texinfo

should have gettext

sudo apt-get install build-essential checkinstall guile-1.6-dev guile-1.6-slib libgoffice-0-dev libgtkhtml3.14-dev texinfo gettext

The instructions work great for Edgy.  They produce a bad package that wants to replace stuff.  Instead, just do:
make
sudo make install

This doesn't create a nice package that can be tracked and removed.  However, it works.   Also, when you are finished installing, download compile and install the documents.  (tar -xzf (filename), cd (filename), ./configure, make, sudo make install)  The documents are very useful.

---

### Post by bdoetsch on 2007-10-03
GnuCash 2.2.1 is now in Gutsy and the description in the gnucash wiki works for compiling with enabled hbci. If you need my already compiled binary packages for gutsy, let me know.

---

### Post by LaneLester on 2007-10-13
> **bdoetsch said:**
> GnuCash 2.2.1 is now in Gutsy and the description in the gnucash wiki works for compiling with enabled hbci. If you need my already compiled binary packages for gutsy, let me know.
I've been running Feisty on one partition, and I just installed Gutsy on a different one. I copied my .gnucash folder from the old home folder to the new one, but the newer version of Gnucash did not open with my accounts and transactions.

I tried exporting to a file from the older Gnucash, but the new one did not recognize the file as a .qif.

Ideas?

Lane

---

### Post by bdoetsch on 2007-10-13
Hey Lane,

on my computer the accounts data is not stored in .gnucash - in fact it is in a file which name and path you got to choose explicitly. Did you try opening that file manually out of gnucash? Could it be that your gutsy doesn't have access to this file?

If manually opening the file doesn't work, it might be due to a change in the file-format, although I think I read, that the newer versions can read the old format - but not vice-versa.

Regards,
B

---

### Post by LaneLester on 2007-10-13
Yes, I see that you are right: the transactions are not in .gnucash, although it seems that the "books" with the account information is. I found where the transaction files are stored (I'm in Feisty now), and I'll boot to Gutsy and see if I can get Gnucash to find them.

I would think that the location would have to be stored in .gnucash. I don't think the path to the location is different in Feisty and Gutsy, but I'll check.

Thanks for the help. I may be back. :)

Later: Yep, I was able to go to the transactions folder and open a master file that got me going again. Whew!

Lane

---

### Post by jozsef on 2008-06-14
In order to get slib working you should remove from your computer any other version of guile (e.g. guile-1.8), you should have only one guile (e.g. guil-1.6) with the dev and you can configure Gnucash.

---

