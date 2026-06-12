---
title: "Compile libgpod from CVS?"
date: 2006-09-04
forum: Desktop Environments
---

### Post by gandalf2041 on 2006-09-04
I am attempting to compile libgpod from CVS (the photo-support branch).  According to the Amarok Main Page, it is needed to transfer videos using Amarok.  When running the autogen script, all seems to go well although I don't understand some of the m4 issues it's reporting:
```
Please add the files
  codeset.m4 gettext.m4 glibc21.m4 iconv.m4 isc-posix.m4 lcmessage.m4
  progtest.m4
from the /usr/share/aclocal directory to your autoconf macro directory
or directly to your aclocal.m4 file.
You will also need config.guess and config.sub, which you can get from
ftp://ftp.gnu.org/pub/gnu/config/.
```
I added the files via the includes at the bottom of the aclocal.m4 script in the libgpod directory, but it still says the same thing when I re-run.  Also, the files at the ftp site mentioned don't exist.  At any rate, it runs but when I try a 'make' it fails with: 
```
collect2: ld returned 1 exit status
make[2]: *** [test-init-ipod] Error 1
make[2]: Leaving directory `/home/kupdegrove/Downloads/libgpod/tests'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/kupdegrove/Downloads/libgpod'
make: *** [all] Error 2

```
has anyone had success with this compile and if so, what did you have to do?  Any help would be GREATLY appreciated.:)

---

### Post by mlind on 2006-09-05
I tried to compile CVS version (with Edgy though.. I can try later with Dapper too). Here are the packages that I installed (also **build-essential**)
```

sudo aptitude install -R autotools-dev automake1.9 autoconf libtool intltool pkg-config libglib2.0-dev libgtk2.0-dev gtk-doc-tools

```

Then run ./autogen.sh. 

Does this work for you?

---

### Post by gandalf2041 on 2006-09-05
Thanks!  I'll give it a shot when I get home.  I have dependency issues with libgtk2.0-dev ](*,)   I don't specifically remember what they were but I discovered them when I tried to compile easytag with aac support.  I guess I'll have to sort through that first.

---

### Post by mlind on 2006-09-05
> **gandalf2041 said:**
> Thanks!  I'll give it a shot when I get home.  I have dependency issues with libgtk2.0-dev ](*,)   I don't specifically remember what they were but I discovered them when I tried to compile easytag with aac support.  I guess I'll have to sort through that first.

I guess this is one of the compiz/libcairo2 issues where -dev package is missing for libcairo2 (in unofficial repository) and this breaks the dependency chain .. Post back the error message when you try to install libgtk2.0-dev.

---

### Post by gandalf2041 on 2006-09-06
I didn't get a chance to work on the issue last night but, now that you mention it, it was an issue with libcairo.  I'll post the aptitude output from your install chain tonight.  Is there a fix for the issue?

---

### Post by mlind on 2006-09-06
> **gandalf2041 said:**
> I didn't get a chance to work on the issue last night but, now that you mention it, it was an issue with libcairo.  I'll post the aptitude output from your install chain tonight.  Is there a fix for the issue?

The problem is that the 3rd party repository you installed libcairo2 package from, doesn't provide libcairo2-**dev** (that matches to version of installed libcairo2).
You can solve this issue by downgrading libcairo2 temporarily by doing **aptitude remove libcairo2** and accepting downgrade solution.

You can also build package on a clean chroot, this way the packages that you've installed on your system don't interfiere. One way to accomplish this is to use [pbuilder]("http://www.ubuntuforums.org/showthread.php?t=206382").

---

### Post by gandalf2041 on 2006-09-06
Thanks mlind!  I like the idea of a clean environment to build my own packages but, I must admit, at this point it's a little over my head :???:   I'm still kind of new to Linux in general and Debian specifically (I started with Red Hat/Fedora).  I will do my best to digest the pbuilder "how-to" you referenced but it's obvious I have a LOT of reading to do.  First though, let me ensure I understand the premise...

By using pbuilder, I can essentially build a package with all the requisite dependencies WITHOUT making changes to my installed base?  (I wish I had know that before I started building several packages from the lastest source/CVS from the net ](*,)) I'm 1 for 3 so far...I've successfully compiled the lastest mpeg4ip and failed with libgpod CVS and easytag with aac support. (Edit: Oh yeah and I somehow stumbled my way through compiling ffmpeg successfully - a programmer I'm not but, I guess with a big enough hammer, you can eventually conquer anything! LOL)

At this point...I've got to wonder how badly I've screwed up my installed system :rolleyes:

---

### Post by mlind on 2006-09-06
> **gandalf2041 said:**
> Thanks mlind!  I like the idea of a clean environment to build my own packages but, I must admit, at this point it's a little over my head :???:   I'm still kind of new to Linux in general and Debian specifically (I started with Red Hat/Fedora).  I will do my best to digest the pbuilder "how-to" you referenced but it's obvious I have a LOT of reading to do.  First though, let me ensure I understand the premise...


Building on a clean room environment has it benefits, but also downsides.. It may be a bit pain to setup and understand at first sight, but it's worth it. The problem is that pbuilder is supposed to be used with Debian **source** packages. This means that if you plan to automatically build a package using pbuilder, it must be "debianized" first..

But pbuilder can be used alternatives ways too. It offers you to setup a test environment (see *pbuilder login* from pbuilder manual) and you can mess around without doing any damage/changes to your normal environment.

I tested to build CVS snapshot using "pbuilder login" method.

> **gandalf2041 said:**
> 
By using pbuilder, I can essentially build a package with all the requisite dependencies WITHOUT making changes to my installed base?  (I wish I had know that before I started building several packages from the lastest source/CVS from the net ](*,)) I'm 1 for 3 so far...I've successfully compiled the lastest mpeg4ip and failed with libgpod CVS and easytag with aac support.


Yes. pbuilder manual page explains how this all works in greater detail (man pbuilder).

The problem here is that you're not doing a .deb package out of libgpod CVS snapshot and probably need to install all build dependencies on your system to get it build and installed.

Does dapper contain any version of libgpod package? It's possible to use existing packaging information and build a .deb file of libgpod CVS version. (It would be somewhat important to use source package for dapper because python policy changes between edgy and debian sid compared to dapper.)

---

### Post by gandalf2041 on 2006-09-06
Yes. Dapper contains a libgpod package.  I don't know about source.  Is there an aptitude equivalent to apt-get source?  I couldn't figure out how to download source using aptitude...there doesn't appear to be an option.  

I did see in your how-to about merging a CVS version into a "debianized" source.  I'll spend the next couple of days reading up on this and see how far I can get.  I'll post back with questions if you don't mind helping out a sorta kinda but not quite Newbie :)

---

### Post by mlind on 2006-09-06
> **gandalf2041 said:**
> Yes. Dapper contains a libgpod package.  I don't know about source.  Is there an aptitude equivalent to apt-get source?  I couldn't figure out how to download source using aptitude...there doesn't appear to be an option.  

I did see in your how-to about merging a CVS version into a "debianized" source.  I'll spend the next couple of days reading up on this and see how far I can get.  I'll post back with questions if you don't mind helping out a sorta kinda but not quite Newbie :)

I'll check that Dapper package out tomorrow. You need to have deb-src equivalents for binary repositories on your /etc/apt/sources.list
```

deb-src http://archive.ubuntu.com/ubuntu dapper main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse

```

Then update package lists and download the source. (There's no aptitude equivalent for *apt-get source* though.)
```

sudo aptitude update
*cd /path/to/source_folder*
apt-get source *package*

```

Don't hesitate to ask any questions you may have regarding this task. I consider myself a newbie too, but I can probably assist you on this matter.

---

### Post by gandalf2041 on 2006-09-28
I'm finally getting around to trying the pbuilder how-to.  When I get to the ```
[18:49:23]-rand:~(0)>> sudo pbuilder update --override-config

```

I get the following output:
```
Upgrading for distribution dapper
Building the build Environment
 -> extracting base tarball [/var/cache/pbuilder/base.tgz]
 -> creating local configuration
 -> copying local configuration
 -> mounting /proc filesystem
ln: creating symbolic link `/var/cache/pbuilder/build//25859/etc/mtab' to `../pr oc/mounts': File exists
 -> mounting /dev/pts filesystem
-> Mounting /home/kupdegrove/pbuilder/result
mount: special device /home/kupdegrove/pbuilder/result does not exist
```

Do I need to specifically create the special device ~/pbuilder/result?

---

### Post by mlind on 2006-09-28
No, you probably missed some step or there's an error in guide. $BUILDRESULT folder which you define on .pbuilderrc file must be created manually, but it's just a directory.

That step is missing ](*,)  Sorry about that. I'll add it asap.
```

mkdir -p ~/pbuilder/result

```

---

### Post by gandalf2041 on 2006-09-28
Wow! Thanks for the quick reply! :p  It seems I'm out of space on my /var partition.  I believe if I comment the /etc/fstab entry out and reboot, it will automatically mount under /.  Is this correct? :-k

Edit: What the heck am I thinking? ](*,) Of course it won't.  Looks like a little gparted work is in order.  Wish me luck!

---

### Post by mlind on 2006-09-28
> **gandalf2041 said:**
> Wow! Thanks for the quick reply! :p  It seems I'm out of space on my /var partition.  I believe if I comment the /etc/fstab entry out and reboot, it will automatically mount under /.  Is this correct? :-k

I was just around the neighborhood ;)

Yes, /var/cache/pbuilder directory is used as default for downloaded packages and build chroots. You can change this if you wish though. See **man pbuilder**.

You can override BASETGZ (tar of the minimal distribution) and BUILDPLACE (where temporary build chroots are created) settings in your .pbuilderrc
```

BASETGZ=${HOME}/path/to/base.tgz
BUILDPLACE=/mnt/share/builds

```
or something similar.

---

### Post by gandalf2041 on 2006-09-28
That was a much simpler solution :rolleyes: Thanks!  I'll keep the manual handy ;)

---

### Post by digitalramble on 2006-10-01
I compiled the latest version of libgpod yesterday with no real issues, except this:

libgpod 0.3.2-1 is what is supported/compiled into dapper AND edgy and;

i want libgpod 0.4.0 (the whole reason for compiling from source in the first place)

but this leaves me with two library files one for each.  This means that when I run a gtkpod built with 0.4.0, it fails because I have two library versions for it.  But, if I look at uninstalling libgpod 0.3.2-1, there's way too many other things that depend on it.  Maybe I can live without amarok, but gnome desktop?

Is there, generally, a way for multiple libraries to coexist?  I'm bugging the folks at gtkpod as well, but having trouble getting thru the mailing list, so I'm trying a couple of possible places.

Also, any notion when the ubuntu distro will update its libgpod?  Is it worth asking the edgy folks to consider it or are there Issues with it as of yet?  I was hoping that perhaps edgy had the newer version and I could just wait a few weeks to resolve this, but...

](*,)

---

### Post by mlind on 2006-10-01
digitalramble, how did you exactly compile it?

---

### Post by gandalf2041 on 2006-10-01
Another quick question: I'm trying to add the latest libgpod (libgpod-0.4.0) per your instructions [here]("http://www.ubuntuforums.org/showthread.php?t=206382") in response #6.  I successfully built libgpod (libgpod-0.3.0) from the repos and then used uupdate after d/l the newest tarball.  The output says it updated OK but, I'm not sure what now?  I tried doing the pbuilder build again on the old version because there is no updated .dsc file```
sudo pbuilder build libgpod_0.3.2-0ubuntu1.dsc
``` Does the resulting .deb contain the changes even though it still says 0.3.2? If so, how do I know what is actually installed?

---

### Post by mlind on 2006-10-01
> **gandalf2041 said:**
> Another quick question: I'm trying to add the latest libgpod (libgpod-0.4.0) per your instructions [here]("http://www.ubuntuforums.org/showthread.php?t=206382") in response #6.  I successfully built libgpod (libgpod-0.3.0) from the repos and then used uupdate after d/l the newest tarball.  The output says it updated OK but, I'm not sure what now?  I tried doing the pbuilder build again on the old version because there is no updated .dsc file```
sudo pbuilder build libgpod_0.3.2-0ubuntu1.dsc
``` Does the resulting .deb contain the changes even though it still says 0.3.2? If so, how do I know what is actually installed?

You must generate .diff.gz and .dsc file using
```

dpkg-source -b *directory*

```
where the directory is the extracted source (with debian folder). If you make any changes to any of the files, dpkg-source -b must be used to generate .diff.gz (in case on non-native package, which most are).

Make sure the original source is archived as
*package_version.orig.tar.gz*.

---

### Post by gandalf2041 on 2006-10-01
OK, that seemed to work.  I now have a LOT of stuff in ~/packages/libgpod:
```
[17:01:38]-rand:~/packages/libgpod(0)>> ls
libgpod-0.3.2                   libgpod_0.4.0-1.diff.gz
libgpod_0.3.2-0ubuntu1.diff.gz  libgpod_0.4.0-1.dsc
libgpod_0.3.2-0ubuntu1.dsc      libgpod_0.4.0.orig.tar.gz
libgpod_0.3.2.orig.tar.gz       libgpod-0.4.0.tar.gz
libgpod-0.4.0
``` and ~/pbuilder/result:
```
[17:02:50]-rand:~/pbuilder/result(0)>> ls
libgpod0_0.3.2-0ubuntu1_i386.deb     libgpod_0.4.0-1_i386.changes
libgpod0_0.4.0-1_i386.deb            libgpod_0.4.0.orig.tar.gz
libgpod_0.3.2-0ubuntu1.diff.gz       libgpod-common_0.3.2-0ubuntu1_all.deb
libgpod_0.3.2-0ubuntu1.dsc           libgpod-common_0.4.0-1_all.deb
libgpod_0.3.2-0ubuntu1_i386.changes  libgpod-dev_0.3.2-0ubuntu1_i386.deb
libgpod_0.3.2.orig.tar.gz            libgpod-dev_0.4.0-1_i386.deb
libgpod_0.4.0-1.diff.gz              Packages
libgpod_0.4.0-1.dsc
```

How much of this stuff do I actually need? (I'm afraid to delete anything :( ).  

Also, how do I confirm that I have the new libgpod installed? :confused: 

I apologize for all the questions.  Debian is pretty new to me.  I'm a Fedora convert (although I'm still somewhat of a general Linux newbie ;) as well)

---

### Post by digitalramble on 2006-10-01
I got the tarballs from here
[http://sourceforge.net/project/showfiles.php?group_id=67873](http://sourceforge.net/project/showfiles.php?group_id=67873)

ran ./configure and make install

I updated a number of things prior to this, from my notes:

d'ld the [gtkpod] .99.8 tarball...
needs gtk+-2.0 -> spm libgtk2.0-dev
libgpod -> spm 
libglade -> spm
flex -> spm
id3tag .15 only -> spm -dev version
libmp4v2-dev, should have the -lmp4v2 for compile?
okay, also mpeg4ip stuff from spm good god
!!! libgpod is too old, get tar.gz & compile..OK

and now...
dr@nemesis:~/Desktop/gtkpod-0.99.8$ gtkpod &
[2] 19033
dr@nemesis:~/Desktop/gtkpod-0.99.8$
** (gtkpod:19033): CRITICAL **: file misc_conversion.c: line 214 (ST_to_T): should not be reached
gtkpod: symbol lookup error: gtkpod: undefined symbol: itdb_get_mountpoint
found this [http://article.gmane.org/gmane.comp.ipod.gtkpod/1179/](http://article.gmane.org/gmane.comp.ipod.gtkpod/1179/)
which seems to relate to the error, but the suggested fix (ldconfig) didn't work

So basically, i set about recompiling gtkpod so as to include the acc support, wound up needing libgpod (latest version) when I found the spm(synaptic package manager) only had the old version and finally got it compiled only to run into the multiple library problem.

I had no particular problems compiling, it's just that when something's missing, the config.log tells you what is wrong, and you can hunt it down.  That's all I did.

---

### Post by mlind on 2006-10-02
> **gandalf2041 said:**
> OK, that seemed to work.  I now have a LOT of stuff in ~/packages/libgpod:
```
[17:01:38]-rand:~/packages/libgpod(0)>> ls
libgpod-0.3.2                   libgpod_0.4.0-1.diff.gz
libgpod_0.3.2-0ubuntu1.diff.gz  libgpod_0.4.0-1.dsc
libgpod_0.3.2-0ubuntu1.dsc      libgpod_0.4.0.orig.tar.gz
libgpod_0.3.2.orig.tar.gz       libgpod-0.4.0.tar.gz
libgpod-0.4.0
``` and ~/pbuilder/result:
```
[17:02:50]-rand:~/pbuilder/result(0)>> ls
libgpod0_0.3.2-0ubuntu1_i386.deb     libgpod_0.4.0-1_i386.changes
libgpod0_0.4.0-1_i386.deb            libgpod_0.4.0.orig.tar.gz
libgpod_0.3.2-0ubuntu1.diff.gz       libgpod-common_0.3.2-0ubuntu1_all.deb
libgpod_0.3.2-0ubuntu1.dsc           libgpod-common_0.4.0-1_all.deb
libgpod_0.3.2-0ubuntu1_i386.changes  libgpod-dev_0.3.2-0ubuntu1_i386.deb
libgpod_0.3.2.orig.tar.gz            libgpod-dev_0.4.0-1_i386.deb
libgpod_0.4.0-1.diff.gz              Packages
libgpod_0.4.0-1.dsc
```

How much of this stuff do I actually need? (I'm afraid to delete anything :( ).  



You'll just need the .deb package(s). diff.gz, .dsc, .changes and .orig.tar.gz form the source package. .deb is the binary you need.

-dev package is development headers, you don't need to install those unless you're compiling something that requires libgpod headers. You can safely remove *0.3.2*, it's probably the older version.

```

cd ~/pbuilder/result
sud dpkg -i libgpod-common_0.4.0-1_all.deb libgpod0_0.4.0-1_i386.deb

```

> **gandalf2041 said:**
> 
Also, how do I confirm that I have the new libgpod installed? :confused: 

I apologize for all the questions.  Debian is pretty new to me.  I'm a Fedora convert (although I'm still somewhat of a general Linux newbie ;) as well)

You can use synaptic, aptitude/apt-get or dpkg to verify this
```

dpkg -l | grep gpod
dpkg -p libgpod
apt-cache madison libgpod
apt-cache show libgpod

```

---

### Post by mlind on 2006-10-02
> **digitalramble said:**
> I got the tarballs from here
[http://sourceforge.net/project/showfiles.php?group_id=67873](http://sourceforge.net/project/showfiles.php?group_id=67873)

ran ./configure and make install

I updated a number of things prior to this, from my notes:

d'ld the [gtkpod] .99.8 tarball...
needs gtk+-2.0 -> spm libgtk2.0-dev
libgpod -> spm 
libglade -> spm
flex -> spm
id3tag .15 only -> spm -dev version
libmp4v2-dev, should have the -lmp4v2 for compile?
okay, also mpeg4ip stuff from spm good god
!!! libgpod is too old, get tar.gz & compile..OK

and now...
dr@nemesis:~/Desktop/gtkpod-0.99.8$ gtkpod &
[2] 19033
dr@nemesis:~/Desktop/gtkpod-0.99.8$
** (gtkpod:19033): CRITICAL **: file misc_conversion.c: line 214 (ST_to_T): should not be reached
gtkpod: symbol lookup error: gtkpod: undefined symbol: itdb_get_mountpoint
found this [http://article.gmane.org/gmane.comp.ipod.gtkpod/1179/](http://article.gmane.org/gmane.comp.ipod.gtkpod/1179/)
which seems to relate to the error, but the suggested fix (ldconfig) didn't work

So basically, i set about recompiling gtkpod so as to include the acc support, wound up needing libgpod (latest version) when I found the spm(synaptic package manager) only had the old version and finally got it compiled only to run into the multiple library problem.

I had no particular problems compiling, it's just that when something's missing, the config.log tells you what is wrong, and you can hunt it down.  That's all I did.


I advice you to compile .deb package from CVS snaphost, that's what gandalf2041 is doing.

---

### Post by digitalramble on 2006-10-02
> **mlind said:**
> I advice you to compile .deb package from CVS snaphost, that's what gandalf2041 is doing.

OK...I don't think I'm having the same problem as gandalf.  I finally threw my hands up and went to gtkpod 0.88.4 which uses libgpod 3.2 and everything compiled like a charm and things seem to be doing okay, except that I've since been informed by someone at gtkpod that the newer generation ipods need libgpod 4.0 or they start crashing.  This would, btw, be true for Amarok and anything else trying to use the libgpod to write to these ipods.  (I'm *really* *really* disappointed edgy didn't go up to this version.)

So here's my very specific question.  I would like to  have *both* libgpod 3.2 and 4.0 installed on my system because I do not want to recompile half of ubuntu that depends on 3.2.  Is there some way to create a particular compile of some object to use a particular version of a library?

For example, if I could rename the 4.0 libgpod library slightly, and then somehow tell the gtkpod compile to use that instead?  I can't find anything obvious in the src/makefiles, though.  I'm not sure how they're linked.

And yes, I'm asking over at the gtkpod mailing list as well, but it's having issues with gmail accounts at the moment ](*,) 

Thanks!
--Cindy

---

### Post by gandalf2041 on 2006-10-09
I hope I didn't miss an obvious answer somewhere in the man page but, how do I pass configuration parameters to pbuilder? :-k  For example...let's say I want to run ```
./configure --enable-gpl --enable-pp --enable-zlib --enable-vorbis \
	--enable-libogg --enable-theora --enable-a52 --enable-dts \
	--enable-dc1394 --enable-libgsm --disable-debug --enable-mp3lame \
	--enable-faad --enable-faac --enable-xvid
```  FYI: These are the recommended options for ffmpeg from the "[HowTo: Encode Video for iPod]("http://ubuntuforums.org/showthread.php?t=114946")" thread

---

### Post by mlind on 2006-10-09
You'll define configure stuff in debian/rules.
If cdbs is being used, define additional flags using DEB_CONFIGURE_EXTRA_FLAGS
```

DEB_CONFIGURE_EXTRA_FLAGS += --with-foo --enable-bar

```

---

### Post by gandalf2041 on 2006-10-09
Thanks mlind! Sounds like a little more reading is in order :-k  Can you point me in the right direction?

---

### Post by mlind on 2006-10-10
> **gandalf2041 said:**
> Thanks mlind! Sounds like a little more reading is in order :-k  Can you point me in the right direction?

Sure thing. These should help you
[http://www.debian.org/doc/maint-guide/ch-dreq.en.html](http://www.debian.org/doc/maint-guide/ch-dreq.en.html)
[https://perso.duckcorp.org/duck/cdbs-doc/cdbs-doc.xhtml](https://perso.duckcorp.org/duck/cdbs-doc/cdbs-doc.xhtml)

You'll know if cdbs is used if debian/control contains cdbs as Build-Depens and/or debian/rules contains cdbs imports.

---

### Post by gandalf2041 on 2006-10-11
Awesome! Thanks! :D

---

### Post by starscalling on 2007-08-24
> **mlind said:**
> I tried to compile CVS version (with Edgy though.. I can try later with Dapper too). Here are the packages that I installed (also **build-essential**)
```

sudo aptitude install -R autotools-dev automake1.9 autoconf libtool intltool pkg-config libglib2.0-dev libgtk2.0-dev gtk-doc-tools

```

Then run ./autogen.sh. 

Does this work for you?

ah awesomely in feisty ty

needed libgnomecanvas2-dev to do gtkpod itself...

---

