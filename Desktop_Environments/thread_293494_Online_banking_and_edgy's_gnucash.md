---
title: "Online banking and edgy's gnucash"
date: 2006-11-05
forum: Desktop Environments
---

### Post by engywook on 2006-11-05
Is the gnucash 2.0.1 package in the edgy repositories compiled with online banking enabled?  I installed gnucash, and then I went back and installed all the aqbanking and ofx libraries (including -dev) that came up in synaptic, but still no online banking option in the gnucash menu.  Is there a way to get gnucash with online banking support through the repositories?  If so, where did I go wrong?

Thanks!

---

### Post by engywook on 2006-11-07
Just to clarify:  by online banking, I mean OFX direct connect.

---

### Post by onesojourner on 2006-11-07
I also need to know how to set up online banking with gnucash google and these forums have been little help.

---

### Post by sirmrmatt on 2006-11-08
I am having the same issue. Need to solve this, would be a very useful feature for many, many people out there to adopt Ubuntu.

I am eager to use the automatic banking feature with gnucash, but cannot without this feature (and I certainly don't want to have to manually import each time).

- Matt
[http://www.thecastleclothing.com](http://www.thecastleclothing.com)
[email]info@thecastleclothing.com[/email]

---

### Post by engywook on 2006-11-08
I found some information that might explain why OFX Direct Connect is unavailable in the Ubuntu GnuCash binary.  From the [GnuCash Wiki]("http://wiki.gnucash.org/wiki/Setting_up_OFXDirectConnect_in_GnuCash_2"):
> GnuCash must be configured using --enable-hbci and --enable-ofx in order for OFXDirectConnect to be available.

The following [post](http://ubuntuforums.org/showthread.php?p=1242167&highlight=hbci+license#post1242167) is referring to Debian's GnuCash packages, but I suspect Ubuntu may have the same licensing issue. > HBCI support is not enabled in the official Debian packages because of licensing issues with openssl, which aqbanking, the library providing this functionality indirectly uses. So we won't be seeing an HBCI enabled GnuCash in Debian unless openssl changes its license or aqbanking starts using gnutls as a replacement for openssl, for example. Neither of these two situations are very likely to happen in the near future, AFAIK. So people who are using HBCI will always have to resort to adding --enable-hbci to debian/rules and rebuilding the package from the Debian sources. HBCI is widely used in Germany by most banking institutions.


The above thread also has instructions [here](http://ubuntuforums.org/showpost.php?p=1242466&postcount=29) for building from source, if you are interested.  I have built it from source and online banking works great, but I would still like to see this available without having to build it.

Merely enabling HBCI support in GnuCash does not cause aqbanking to be a mandatory dependency, but it would allow users to add aqbanking and thus have OFX Direct Connect support later without having to build GnuCash from source.  So, how do I go about requesting an "official" Ubuntu GnuCash package configured/built with --enable-hbci added?
Thanks again!

---

### Post by sirmrmatt on 2006-11-09
"engywook":

I tried building from source. I had to have the ofxlib and that other one (not-terribly-technical, sorry), but I got to a point where I needed to get ssl and could not get it. 

I really know that automated personal finance is a killer app for many "ordinary" people, a very worthwhile pursuit. 

Any ideas on fixing my dependency ssl issues?

- Mat

---

### Post by sirmrmatt on 2006-11-10
I get this after installing libofx 0.8:

checking whether to use OFX... yes -- failure is fatal
checking for libofx version >= 0.7.0... ./configure: line 28924: ofxdump: command not found
configure: error: found ; Libofx 0.7.0 or newer needed for ofx support

Any ideas?
](*,) 

- Matt

---

### Post by yzwkzfn on 2006-12-12
> **sirmrmatt said:**
> I get this after installing libofx 0.8:

checking whether to use OFX... yes -- failure is fatal
checking for libofx version >= 0.7.0... ./configure: line 28924: ofxdump: command not found
configure: error: found ; Libofx 0.7.0 or newer needed for ofx support

Any ideas?
](*,) 

- Matt

You might want to add the flag: --with-ofx-prefix=/usr/local (working 
from memory here on the --with-ofx).  If you built libofx 0.8 verify the
prefix that it used.

Kevin

---

### Post by wuzzeb on 2006-12-18
I just expanded and cleaned up the build instructions for HBCI on the gnucash wiki.  There are build instructions located at [http://wiki.gnucash.org/wiki/Debian](http://wiki.gnucash.org/wiki/Debian)   I was able to successfully build the packages on edgy.

---

### Post by rparker on 2006-12-31
> **wuzzeb said:**
> I just expanded and cleaned up the build instructions for HBCI on the gnucash wiki.  There are build instructions located at [http://wiki.gnucash.org/wiki/Debian](http://wiki.gnucash.org/wiki/Debian)   I was able to successfully build the packages on edgy.


Working in Edgy; prior to following your instructions I installed the aqbanking tool and associated files through Synaptic Package Manager.

I attempted to build the package and ran into two issues:

1) While installing aqbanking16-qt-wizard I received an error that reported conflicts with libaqbanking16. So I proceeded the build w/o the wizard. Is this a problem?

2) the build started and then stopped with the following lines just preceeding the stop:

configure: exit 1
touch configure-stamp
dh_testdir
# dh_testroot
dh_clean -k
dh_installdirs
make
make[1]: Entering directory '/home/[user]/gnucash/gnucash-2.0.1'
make[1]: *** No targets specified and no makefile found. Stop.
make[1]: leaving directory '/home/[user]/gnucash/gnucash-2.0.1'
make: *** [build-stamp] Error 2

I would appreciate any suggestions on how to proceed.

---

### Post by astabeno on 2007-01-05
Apt-get could not find packet aqbanking16-qt-wizard.  I searched for it online and found it listed only under feisty universe repository.  So I downloaded it from the debian packages site.  I tried for a while to install it from there but got tired of installing packet after packet of dependencies.  Is there an easier way to do this?  Is there a repository I can add to sources.list to install this through apt-get?

---

### Post by rparker on 2007-01-05
I'm not sure if this is helpful as I am a newbie but I first installed the aqbanking tool and associated files through Synaptic Package Manager.

My conflict with installing aqbanking16-qt-wizard came from trying to install libaqbanking16 but I think I should have installed libaqbanking16-dev. I have not had a chance to re-try the steps.

---

### Post by the79bomb on 2007-01-08
Having trouble compiling gnucash with online banking enabled.  Found the link to the article in the Wiki posted earlier:

There are build instructions located at [http://wiki.gnucash.org/wiki/Debian](http://wiki.gnucash.org/wiki/Debian) I was able to successfully build the packages on edgy.

but I cannot find the debian/rules file which should be in the gnucash-2.0... folder.  Does anyone know where to progress from here?  Maybe I downloaded something other than the source code for gnucash but there is a src folder present and it appears to be the right thing.  

I installed the libaqbanking16-dev using the package installer tool in edgy (search for libaqbanking)  

how can I verify if I did indeed install the source files on my system and also where do I find this rules file?  all files seem to have some extension to them and there is not file named rules in the directory.

Any help would be appreciated.  Thanks, Tim

---

### Post by rparker on 2007-01-09
If you followed the wiki you created a folder called gnucash and then a sub folder gnucash-2.*. Within this folder is another folder called Debian and the 'rules' file is there. (gnucash/gnucash-2.0.1/debian/rules).

I have yet to be successful in compiling the on-line banking. Maybe I need to download the gnucash source again.

---

### Post by bobpaul on 2007-02-20
I'm told I have unmet dependencies when attempting to build the package

```
bobpaul@bobpaul:~/gnucash-build/gnucash-2.0.1$ dpkg-buildpackage -b -us -uc -rfakeroot
dpkg-buildpackage: source package is gnucash
dpkg-buildpackage: source version is 2.0.1-3ubuntu3.1
dpkg-buildpackage: source changed by bobpaul <bobpaul@bobpaul>
dpkg-buildpackage: host architecture i386
dpkg-buildpackage: source version without epoch 2.0.1-3ubuntu3.1
dpkg-checkbuilddeps: Unmet build dependencies: libltdl3-dev ofx (>= 1:0.8.0-8) libdb3-dev libjpeg62-dev liborbit-dev libungif4-dev libglib2.0-dev (>= 2.4.7) libxml2-dev (>= 2.4.16) libbonobo2-dev (>= 2.0.0) libgnomevfs2-dev (>= 2.2.0) libgtk2.0-dev (>= 2.4.13) libglade2-dev (>= 2.3.6) libgnomeprint2.2-dev (>= 2.8.0) libart-2.0-dev (>= 2.3.11) libgconf2-dev libgnomeui-dev (>= 2.0.0) libgsf-gnome-1-dev (>= 1.12.2) libpango1.0-dev (>= 1.6.0) libgtkhtml3.8-dev libgoffice-0-dev libgsf-gnome-1-dev
dpkg-buildpackage: Build dependencies/conflicts unsatisfied; aborting.
dpkg-buildpackage: (Use -d flag to override.)
```

---

### Post by karmayogi on 2007-07-08
bobpaul,

I had the same error. Here is what I did to resolve this

[FONT="Courier New"]$ sudo apt-get install libltdl3-dev gettext libdb3-dev debhelper zlib1g-dev libjpeg62-dev liborbit-dev libungif4-dev libglib2.0-dev libxml2-dev libbonobo2-dev  libgnomevfs2-dev libgtk2.0-dev libglade2-dev libgnomeprint2.2-dev libart-2.0-dev libgconf2-dev libgnomeui-dev libgsf-gnome-1-dev libpango1.0-dev libgtkhtml3.8-dev libgoffice-0-dev libgsf-gnome-1-dev imagemagick[/FONT]

---

### Post by dennis1200 on 2007-07-16
Would there be any possibility of someone sticking a HBCl-enabled GnuCash deb in Multiverse? Or even, possibly, in the not-at-all utilized 'commercial' repos where I think there are just 4 things: Arkeia, Opera, and two packages for VMWare. I'm a huge fan of open source, but when licensing things like this come up, shouldn't there be an alternative or at least a choice on the part of the user (and unfortunately, forcing someone to learn the intricacies of compilation and -dev packages is not really providing a choice to most users).

---

