---
title: "HOWTO install cvs xqf??"
date: 2006-07-20
forum: Gaming &amp; Leisure
---

### Post by nickless on 2006-07-20
Today I **tried/failed** to install xqf from cvs. Why? Simply because the games I play are until today only supported in the cvs version. So to get a nice browser for Tremulous and especially Warsow (it has only a strange java browser that really works) I went to [http://www.linuxgames.com/xqf/docs.shtml#mozTocId355848](http://www.linuxgames.com/xqf/docs.shtml#mozTocId355848) and followed what the FAQ told me to do. 

1. Installing needed packages, because the FAQ says:
> Compiling CVS snapshots requires that you have recent versions of automake (at least 1.6), autoconf, libtool and gettext installed. You also need to have both GTK1 and GTK2 development packages installed.
So I did:
```
sudo apt-get install automake libtool
```
which installed  autoconf automake1.4 autotools-dev libtool

2. Getting cvs xqf:
```

cvs -z3 -d:pserver:anonymous@xqf.cvs.sourceforge.net:/cvsroot/xqf co -P xqf
```

3. Create the 'configure' script:
```
./autogen.sh
```
but then I got this:
> Running gettextize and intltoolize...
Copying file mkinstalldirs
Copying file po/Makefile.in.in

Please add the files
  codeset.m4 gettext.m4 glibc21.m4 iconv.m4 isc-posix.m4 lcmessage.m4
  progtest.m4
from the /usr/share/aclocal directory to your autoconf macro directory
or directly to your aclocal.m4 file.
You will also need config.guess and config.sub, which you can get from
[ftp://ftp.gnu.org/pub/gnu/config/](ftp://ftp.gnu.org/pub/gnu/config/).

./autogen.sh: line 47: intltoolize: command not found


I found the files, but I have no idea where to copy them to. What is the "autoconf macro directory"? I tried it again with the files in the xqf/ folder, but that didn't seem right from the beginning...](*,) 

If somebody could help me I would update this "howto" and maybe help this way people like me to get the newest xqf running. Maybe there is a better and easier way to get it running, or maybe you want to write a script? Everything would be fine :D

---

### Post by ubuntu_demon on 2006-07-21
What version do you require ? Is there no way to add a game by hand ?

Some xqf version information :

Dapper has 1.0.4-1
Edgy has 1.0.4-2 but requires a newer version of libc6 
I just installed xqf 1.0.4-2 from Debian unstable but there were no mentions of tremulous or warshow. So I don't advice you to install it. But if you insist on installing it you can download the package here : [http://packages.debian.org/unstable/games/xqf](http://packages.debian.org/unstable/games/xqf)

---

### Post by ubuntu_demon on 2006-07-21
Are you sure that XQF from CVS will provide tremulous and warshow ?

---

### Post by nickless on 2006-07-21
I was told it does. No idea, but I don't think they tricked me :D

edit: Yes I checked it, it should be possible. Thats what I found in a NEWS file: > Changes since 1.0.4:

o new games: Warsow
o fix Quake 4 RCON
o add "Show only configured games" button again
o fix SOF2 query
o add new America's Army master server
o support copying server info values to clipboard

And after some research I also found this:
> The XQF CVS version ( [http://xqf.sourceforge.net/cvs/](http://xqf.sourceforge.net/cvs/) ) has support for
 tremulous. But, you have to patch the /etc/qstat.cfg file in order the QSTAT
 supports Tremulous.
[http://sourceforge.net/mailarchive/forum.php?thread_id=10232334&forum_id=8001](http://sourceforge.net/mailarchive/forum.php?thread_id=10232334&forum_id=8001)

I'll try the debian package you found there and give answere if it supports warsow=D>

---

### Post by nickless on 2006-07-21
Nope the .deb doesn't support warsow :(

---

### Post by ubuntu_demon on 2006-07-21
> **nickless said:**
> Nope the .deb doesn't support warsow :(
Maybe you should first patch the /etc/qstat.cfg and then try whether it works with the Dapper XQF version and/or the Debian unstable XQF version.

---

### Post by markmark on 2006-07-21
You say the FAQ states that automake > 1.6 is required, but that doing apt-get install automake only gave you 1.4?

There is individual automake packages in the repos for specific versions:
```
apt-get install automake1.4 automake1.7 automake1.8 automake1.9
```
Maybe that will help?

---

### Post by nickless on 2006-07-22
Sam error:
> Running gettextize and intltoolize...
Copying file mkinstalldirs
Copying file po/Makefile.in.in

Please add the files
  codeset.m4 gettext.m4 glibc21.m4 iconv.m4 isc-posix.m4 lcmessage.m4
  progtest.m4
from the /usr/share/aclocal directory to your autoconf macro directory
or directly to your aclocal.m4 file.
You will also need config.guess and config.sub, which you can get from
[ftp://ftp.gnu.org/pub/gnu/config/](ftp://ftp.gnu.org/pub/gnu/config/).

./autogen.sh: line 47: intltoolize: command not found


---

### Post by mlind on 2006-07-22
I suggest you to get the source package from Ubuntu or Debian, and the use **uupdate** to apply old (packaging) diffs to the new cvs version. I'll check this out later today and help you with this.

You should use automake1.9 instead of virtual package automake, which installs very old and unsupported version 1.4. You should also install autotools-dev, autoconf, libtool and probably pkg-config.

---

### Post by nickless on 2006-07-22
Cool, thx :D
So you suggest I install the old xqf through apt and then run uupdate (which seems to be a part of the devscripts package) to update the program. This sounds too easy to be true :D
Well for now I will install the packages you listed there and try the ./autogen.sh again :)

edit: packages you listed were all already installed

---

### Post by mlind on 2006-07-22
> **nickless said:**
> Cool, thx :D
So you suggest I install the old xqf through apt and then run uupdate (which seems to be a part of the devscripts package) to update the program. This sounds too easy to be true :D
Well for now I will install the packages you listed there and try the ./autogen.sh again :)

edit: packages you listed were all already installed

Okay, I got this to build with some adjustments.. This is very brief howto and probably contains some errors


[LIST=1]
[*]Add new repository to **/etc/apt/sources.list**
```

deb-src http://ftp.uk.debian.org/debian unstable main contrib non-free

```

[*]Create build directory and get source from debian unstable
```

mkdir -p ~/packages/xqf
cd ~/packages/xqf
**sudo aptitude update**
apt-get source xqf

```

[*]Checkout cvs module
```

cvs -z3 -d:pserver:anonymous@xqf.cvs.sourceforge.net:/cvsroot/xqf co -P xqf

```

[*]Prepare for uupdate
```

mv xqf xqf-1.0.4.1+cvs20060722
#cvs snapshot seems to contain debian package information, but we'll remove it
rm -rf xqf-1.0.4.1+cvs20060722/debian

tar czvf xqf-1.0.4.1+cvs20060722.tar.gz xqf-1.0.4.1+cvs20060722
rm -rf xqf-1.0.4.1+cvs20060722

```

[*]Apply old debian package information (diffs)
```

cd xqf-1.0.4/
uupdate ../xqf-1.0.4.1+cvs20060722.tar.gz **1.0.4.1+cvs20060722**
cd ../xqf-1.0.4.1+cvs20060722

```


[*]Edit **debian/rules** so that autogen.sh is executed before configure. Bold entries are new stuff
```

[B]post-patches:: debian/stamp-autogen
debian/stamp-autogen:
        NOCONFIGURE=1 ./autogen.sh
        touch $@[/B]

clean::
        rm -f config.h
        **rm -f debian/stamp-autogen**

```

[*]Edit **debian/control** and _add_ necessary packages for autogen.sh script
```

Build-Depends: **automake1.9, autoconf, intltool, libtool, libglib-dev, libgtk-dev, libgdk-pixbuf-dev**
**Build-Conflicts: automake1.4, autoconf2.13**

```


[*]Modify changelog information. You need **devscripts** package for this
```

dch -e

```

(Example changelog entry. Bolded part is important)
```

xqf (1.0.4.1+cvs20060722-**0ubuntu1**) **dapper**; urgency=low

  * New CVS snapshot

 -- Firstname Lastname <you@somemail.com>  Sat, 22 Jul 2006 19:52:09 +0300

```

[*]Build the package. I suggest using pbuilder ([HOWTO]("http://www.ubuntuforums.org/showthread.php?t=206382")) that automates the dependency install process.
```

cd ..
#generate .dsc and diffs
dpkg-source -b xqf-1.0.4.1+cvs20060722
sudo pbuilder build xqf_1.0.4.1+cvs20060722-0ubuntu1.dsc

```

[*]**Alternatively**, you may use dpkg-buildpackage. You'll need **dpkg-dev** package for this
```

dpkg-buildpackage -rfakeroot -us -uc

```
[/LIST]

---

### Post by nickless on 2006-07-22
Wow thx! This is some heavy stuff... not shure I understood all of what you did there, so I'll just try to install the tar.gz you made there :D

---

### Post by mlind on 2006-07-22
> **nickless said:**
> Wow thx! This is some heavy stuff... not shure I understood all of what you did there, so I'll just try to install the tar.gz you made there :D

Yeah, no problem. You can probably use those instructions next time you need to upgrade xqf or install other cvs/svn package.

---

### Post by nickless on 2006-07-22
Everything is working fine, this is great! Thanks again mate! :D

---

### Post by User_Program on 2006-07-23
Thank You mlind!  

I did run into some problems with installing the deb.  I was getting 

> CRITICAL **: egg_desktop_entries

It is fixed now after editing the .desktop files  

If anyone is getting these errors plz post and I will write up a fix for it.

Thanks again!

BTW I'm having an issue with UT master server showing up.  I get LAN but no master server.  In game I get the list but in XQF I don't.  All other games, DOOM3,Quake4,UT2004,Tremulous are fine.  Does anyone know what is wrong?  also this was in issue for me with other versions of xqf not mlind debs.

---

### Post by User_Program on 2006-07-24
Anyone?  

> I'm having an issue with UT master server showing up. I get LAN but no master server. In game I get the list but in XQF I don't. All other games, DOOM3,Quake4,UT2004,Tremulous are fine. Does anyone know what is wrong? also this was in issue for me with other versions of xqf not mlind debs.

---

### Post by User_Program on 2006-07-27
I hate doing this :P  

Does anyone have any ideas?

---

### Post by mlind on 2006-07-27
> **User_Program said:**
> I hate doing this :P  

Does anyone have any ideas?

Where does qstat fetch UT2004 master server list?

---

