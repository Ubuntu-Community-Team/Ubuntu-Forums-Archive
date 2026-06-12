---
title: "no KDE headers installed."
date: 2010-03-18
forum: Desktop Environments
---

### Post by Fitch on 2010-03-18
I'm trying to get kmsgmodem installed, as I have an external message modem.
It requires KDE, so I've attempted to install that in Karmic.

I've come across exactly the same problems as:
[http://ubuntuforums.org/showthread.php?t=75143](http://ubuntuforums.org/showthread.php?t=75143)

but using that thread, have muddled my way through until I get :

E: /var/cache/apt/archives/kdelibs-data_4%3a3.5.10.dfsg.1-3_all.deb: trying to overwrite '/usr/share/doc/kde/HTML/en/common/mainheader.html', which is also in package kdelibs5-data 4
E: /var/cache/apt/archives/kdelibs4-dev_4%3a3.5.10.dfsg.1-3_i386.deb: trying to overwrite '/usr/bin/ksvgtopng', which is also in package kdebase-runtime 4

The Synaptic manager "details" are in the attachment
The last few lines of "configure" are below:

checking for KDE... configure: error:
in the prefix, you've chosen, are no KDE headers installed. This will fail.
So, check this please and use another prefix!


[IMG]file:///tmp/moz-screenshot-2.png[/IMG]
[IMG]file:///tmp/moz-screenshot.png[/IMG][IMG]file:///tmp/moz-screenshot-1.png[/IMG]

---

### Post by Fitch on 2010-03-20
bump

---

### Post by xifer on 2010-03-20
> **Fitch said:**
>  I get :
E: /var/cache/apt/archives/kdelibs-data_4%3a3.5.10.dfsg.1-3_all.deb: trying to overwrite '/usr/share/doc/kde/HTML/en/common/mainheader.html', which is also in package kdelibs5-data 4
E: /var/cache/apt/archives/kdelibs4-dev_4%3a3.5.10.dfsg.1-3_i386.deb: trying to overwrite '/usr/bin/ksvgtopng', which is also in package kdebase-runtime 4

The Synaptic manager "details" are in the attachment
The last few lines of "configure" are below:

checking for KDE... configure: error:
in the prefix, you've chosen, are no KDE headers installed. This will fail.
So, check this please and use another prefix!


cLEraly something is messed up.  Have you tried uninstalling everything K related - clean your catalogue, for good measure use a terminal session to hunt around for any leftover files - especially the ones being griped about and delete with wild abandon.


then check your sources list - here's a good place to do that

[http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/)


then try to install the full KDE packages kdelibs4-dev, kdebase, kdeworkspace-dev, kubuntu-desktop and hope the problem has gone away

---

### Post by Fitch on 2010-03-20
When you say "clean your catalogue", how does one go about that exactly?
Julie's got a catalogue, I think it it's Freemans...

---

### Post by xifer on 2010-03-20
i mean the packages and lists index that is stored on your machine by the package installer.  
after you have uninstalled eveything  use this command  - run it  as root or use sudo

apt-get -autoremove

apt-get -autoclean



then delete any leftover files/directories with K stuff in them.

---

### Post by Fitch on 2010-03-21
Thanks for that.

I did try to delete everything, unfortunately, I have kbarcode and openoffice which would both be removed if I continued, so I can't go on.

I'll have to give up on kmsgmodem.

I've now got a nice clean computer though!

Thanks for your help.

The operation was a success, but the patient died.

---

### Post by xifer on 2010-03-21
> **Fitch said:**
> Thanks for that.

I did try to delete everything, unfortunately, I have kbarcode and openoffice which would both be removed if I continued, so I can't go on.

I'll have to give up on kmsgmodem.

I've now got a nice clean computer though!

Thanks for your help.

The operation was a success, but the patient died.

any reason they can't be removed and reinstalled later? there's  no need to lose any personal data/config just make sure it's all backed up elsewhere.  Good chance that the kbarcode install is the real problem - I'm guessing it's from an earlier version of KDE.

---

### Post by Fitch on 2010-03-23
Brilliant program though!
Need it for the PAT testing
Guess what.  It's gone anyway!
Hard drive dying. 
Got a new hard drive and waiting to see if everything is cured.
(Will have to put the barcode reader back on though!

---

### Post by macogw on 2010-03-26
Headers means you need to have the -dev packages installed, not just the plain packages (which only contain the binaries).

---

### Post by Fitch on 2010-03-27
I seem to have gotten further after a new hard drive:
The last bit from ./configure is:

checking for perl... /usr/bin/perl
checking for Qt... configure: error: Qt (>= Qt 3.0) (headers and libraries) not found. Please check your installation!
For more details about this problem, look at the end of config.log.

The end of config log is:

define VERSION "$"
#define ksize_t socklen_t
#endif
#ifdef __cplusplus
extern "C" void exit (int) throw ();

configure: exit 1

---

### Post by Fitch on 2010-03-29
Forgot to mention that I've installed every dev file I can lay my hands on


Installed the following packages:
akonadi-server (1.2.1-0ubuntu4)
automoc (1.0~version-0.9.88-2)
cervisia (4:4.3.5-0ubuntu1~karmic1)
cmake (2.8.0-5ubuntu1~karmic1)
cmake-data (2.8.0-5ubuntu1~karmic1)
cvsservice (4:4.3.5-0ubuntu1~karmic1)
emacsen-common (1.4.19ubuntu1)
gawk (1:3.1.6.dfsg-0ubuntu2)
graphviz (2.20.2-3ubuntu5)
kapptemplate (4:4.3.5-0ubuntu1~karmic1)
kate (4:4.3.5-0ubuntu1~karmic1)
kbugbuster (4:4.3.5-0ubuntu1~karmic1)
kcachegrind (4:4.3.5-0ubuntu1~karmic1)
kde-devel (5:50ubuntu2)
kde-minimal (5:50ubuntu2)
kde-window-manager (4:4.3.5-0ubuntu1~karmic1)
kdebase-workspace (4:4.3.5-0ubuntu1~karmic1)
kdebase-workspace-bin (4:4.3.5-0ubuntu1~karmic1)
kdebase-workspace-data (4:4.3.5-0ubuntu1~karmic1)
kdebase-workspace-dev (4:4.3.5-0ubuntu1~karmic1)
kdebase-workspace-kgreet-plugins (4:4.3.5-0ubuntu1~karmic1)
kdelibs5-dev (4:4.3.5-0ubuntu1~karmic1)
kdepim-runtime (4:4.3.5-0ubuntu1~karmic1)
kdepim-runtime-data (4:4.3.5-0ubuntu1~karmic1)
kdepim-runtime-libs4 (4:4.3.5-0ubuntu1~karmic1)
kdepimlibs-data (4:4.3.5-0ubuntu1~karmic1)
kdepimlibs5 (4:4.3.5-0ubuntu1~karmic1)
kdesdk (4:4.3.5-0ubuntu1~karmic1)
kdesdk-kio-plugins (4:4.3.5-0ubuntu1~karmic1)
kdesdk-misc (4:4.3.5-0ubuntu1~karmic1)
kdesdk-scripts (4:4.3.5-0ubuntu1~karmic1)
kdesdk-strigi-plugins (4:4.3.5-0ubuntu1~karmic1)
kdm (4:4.3.5-0ubuntu1~karmic1)
klipper (4:4.3.5-0ubuntu1~karmic1)
kompare (4:4.3.5-0ubuntu1~karmic1)
kpartloader (4:4.3.5-0ubuntu1~karmic1)
ksysguard (4:4.3.5-0ubuntu1~karmic1)
ksysguardd (4:4.3.5-0ubuntu1~karmic1)
kuiviewer (4:4.3.5-0ubuntu1~karmic1)
libakonadiprivate1 (1.2.1-0ubuntu4)
libapr1 (1.3.8-1)
libaprutil1 (1.3.9+dfsg-1ubuntu1)
libboost-program-options1.38.0 (1.38.0-6ubuntu6)
libc6-dbg (2.10.1-0ubuntu16)
libkdecorations4 (4:4.3.5-0ubuntu1~karmic1)
libkonq5-dev (4:4.3.5-0ubuntu1~karmic1)
libkrosspython0 (4:4.3.5-0ubuntu1~karmic1)
libkwineffects1 (4:4.3.5-0ubuntu1~karmic1)
libpolkit-qt0 (0.9.2+svn966498-0ubuntu1)
libqimageblitz4 (1:0.0.4-4)
libqt4-phonon-dev (4.5.3really4.5.2-0ubuntu1)
libqt4-sql-sqlite (4.5.3really4.5.2-0ubuntu1)
libsoprano-dev (2.3.1+dfsg.1-1)
libstrigiqtdbusclient0 (0.7.0-1)
libsvn1 (1.6.5dfsg-1ubuntu1)
libtidy-0.99-0 (20081224cvs-1)
lokalize (4:4.3.5-0ubuntu1~karmic1)
mysql-server-core-5.1 (5.1.37-1ubuntu5.1)
pkg-kde-tools (0.4.11ubuntu7)
plasma-dataengines-workspace (4:4.3.5-0ubuntu1~karmic1)
plasma-widgets-workspace (4:4.3.5-0ubuntu1~karmic1)
poxml (4:4.3.5-0ubuntu1~karmic1)
python-dateutil (1.4.1-3)
python-enchant (1.5.3-1)
python-kde4 (4:4.3.5-0ubuntu1~karmic1)
python-levenshtein (0.10.1-1ubuntu1)
python-lxml (2.1.5-1ubuntu2)
python-utidylib (0.2-3.2ubuntu1)
python-vobject (0.6.0-1)
subversion (1.6.5dfsg-1ubuntu1)
systemsettings (4:4.3.5-0ubuntu1~karmic1)
translate-toolkit (1.3.0-6ubuntu1)
ttf-liberation (1.05.1.20090721-0ubuntu1)
umbrello (4:4.3.5-0ubuntu1~karmic1)
valgrind (1:3.5.0-2ubuntu2)

nstalled the following packages:
comerr-dev (2.1-1.41.9-1ubuntu3)
libaudio-dev (1.9.2-1)
libgl1-mesa-dev (7.6.0-1ubuntu4)
libglib2.0-dev (2.22.3-0ubuntu1)
libglu1-mesa-dev (7.6.0-1ubuntu4)
libglu1-xorg-dev (1:7.4+3ubuntu10)
libgssrpc4 (1.7dfsg~beta3-1ubuntu0.5)
libkadm5clnt6 (1.7dfsg~beta3-1ubuntu0.5)
libkadm5srv6 (1.7dfsg~beta3-1ubuntu0.5)
libkdb5-4 (1.7dfsg~beta3-1ubuntu0.5)
libkrb5-dev (1.7dfsg~beta3-1ubuntu0.5)
liblcms1-dev (1.18.dfsg-1ubuntu1)
libmng-dev (1.0.9-1build1)
libpng12-dev (1.2.37-1ubuntu0.1)
libpq-dev (8.4.2-0ubuntu9.10)
libqt4-dev (4.5.3really4.5.2-0ubuntu1)
libqt4-opengl-dev (4.5.3really4.5.2-0ubuntu1)
libsqlite0-dev (2.8.17-6build1)
libssl-dev (0.9.8g-16ubuntu3.1)
mesa-common-dev (7.6.0-1ubuntu4)
qt4-qmake (4.5.3really4.5.2-0ubuntu1)
xlibmesa-gl-dev (1:7.4+3ubuntu10)


Installed the following packages:
libjpeg62-dev (6b-14build1)

nstalled the following packages:
f2c (20061008-3)
fort77 (1.15-8)
libcnf-dev (4.0-2)
libf2c2 (20061008-4.1)
libf2c2-dev (20061008-4.1)


Installed the following packages:
libpthread-stubs0 (0.1-2)
libpthread-stubs0-dev (0.1-2)
libx11-dev (2:1.2.2-1ubuntu1)
libxau-dev (1:1.0.4-2)
libxcb1-dev (1.4-1)
libxdmcp-dev (1:1.0.2-3)
libxext-dev (2:1.0.99.1-0ubuntu4)
libxp-dev (1:1.0.0.xsf1-2)
x11proto-input-dev (1.5.0-2ubuntu1)
x11proto-kb-dev (1.0.3-3ubuntu1)
x11proto-print-dev (1.0.3.xsf1-1)
x11proto-xext-dev (7.0.4-2)
xtrans-dev (1.2.4-1)


Installed the following packages:
libuu0 (0.5.20-3.2)
x-dev (7.0.15-1)
x11proto-core-dev (7.0.15-1)
xutils-dev (1:7.4+5ubuntu1)


Installed the following packages:
dolphin (4:4.3.5-0ubuntu1~karmic1)
kappfinder (4:4.3.5-0ubuntu1~karmic1)
kdebase (4:4.3.5-0ubuntu1~karmic1)
kdebase-bin (4:4.3.5-0ubuntu1~karmic1)
kdebase-data (4:4.3.5-0ubuntu1~karmic1)
kdebase-workspace-libs4+5 (4:4.3.5-0ubuntu1~karmic1)
kdepasswd (4:4.3.5-0ubuntu1~karmic1)
kfind (4:4.3.5-0ubuntu1~karmic1)
konqueror (4:4.3.5-0ubuntu1~karmic1)
konqueror-nsplugins (4:4.3.5-0ubuntu1~karmic1)
konsole (4:4.3.5-0ubuntu1~karmic1)
kwrite (4:4.3.5-0ubuntu1~karmic1)
libkonq5 (4:4.3.5-0ubuntu1~karmic1)
libkonq5-templates (4:4.3.5-0ubuntu1~karmic1)
libkonqsidebarplugin4 (4:4.3.5-0ubuntu1~karmic1)
plasma-widget-folderview (4:4.3.5-0ubuntu1~karmic1)


Installed the following packages:
alien (8.78)
bsd-mailx (8.1.2-0.20081101cvs-2ubuntu1)
build-essential (11.4)
cl-asdf (1.111-1)
cl-plus (1.0-3)
common-lisp-controller (6.18)
cvs (1:1.12.13-12ubuntu1)
debhelper (7.3.15ubuntu3)
dpkg-dev (1.15.4ubuntu2.1)
g++ (4:4.4.1-1ubuntu2)
g++-4.4 (4.4.1-4ubuntu9)
gettext (0.17-8ubuntu2)
gpp (2.24-1)
html2text (1.3.2a-14)
intltool-debian (0.35.0+20060710.1)
kcc (2.3-12)
libmail-sendmail-perl (0.79.16-1)
librpm0 (4.7.0-9)
librpmbuild0 (4.7.0-9)
librpmio0 (4.7.0-9)
libstdc++6-4.4-dev (4.4.1-4ubuntu9)
libsys-hostname-long-perl (1.4-2)
lsb-core (4.0-0ubuntu5)
lsb-cxx (4.0-0ubuntu5)
mailx (1:20081101-2ubuntu1)
ncurses-term (5.7+20090803-2ubuntu2)
pax (1:20090728-1)
po-debconf (1.0.16)
realpath (1.15)
rpm (4.7.0-9)
sbcl (1:1.0.29.11-1)

---

### Post by Fitch on 2010-03-30
Managed to find all the dev files and missing dependancies needed.
kmsgmodem configures nicely now..

Make ends with:

 from main.cpp:24:
/usr/share/qt3/include/qevent.h: In constructor &#8216;QContextMenuEvent::QContextMenuEvent(QContextMenuEvent::Reason, const QPoint&, const QPoint&, int)&#8217;:
/usr/share/qt3/include/qevent.h:432: warning: conversion to &#8216;unsigned char&#8217; from &#8216;uint&#8217; may alter its value
/usr/share/qt3/include/qevent.h: In member function &#8216;void QDropEvent::setAction(QDropEvent::Action)&#8217;:
/usr/share/qt3/include/qevent.h:523: warning: conversion to &#8216;unsigned char&#8217; from &#8216;uint&#8217; may alter its value
In file included from main.cpp:24:
kmsgmodem.h: At global scope:
kmsgmodem.h:104: error: &#8216;KArtsDispatcher&#8217; does not name a type
kmsgmodem.h:105: error: &#8216;KArtsServer&#8217; does not name a type
kmsgmodem.h:106: error: ISO C++ forbids declaration of &#8216;PlayObject&#8217; with no type
kmsgmodem.h:106: error: invalid use of &#8216;::&#8217;
kmsgmodem.h:106: error: expected &#8216;;&#8217; before &#8216;*&#8217; token
In file included from /usr/include/kde/kaboutdata.h:24,
                 from main.cpp:26:
/usr/share/qt3/include/qimage.h: In member function &#8216;bool QImageTextKeyLang::operator<(const QImageTextKeyLang&) const&#8217;:
/usr/share/qt3/include/qimage.h:61: warning: suggest parentheses around &#8216;&&&#8217; within &#8216;||&#8217;
make[2]: *** [main.o] Error 1
make[2]: Leaving directory `/home/brafferton/kmsgmodem/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/brafferton/kmsgmodem'
make: *** [all] Error 2

Has ANYBODY any ideas?

I've had two faxes sitting on the modem memory for over a week now.

And how do you disable smilies?

---

### Post by xifer on 2010-03-30
My only idea is to take this to the kmsgmodem developers

---

### Post by Fitch on 2010-03-30
There are'nt any

---

### Post by xifer on 2010-03-30
Fancy teaching yourself c++ ?

a quick look tells me KArtsDispatcher should be int and KArtSServer void but i'm not sure if that helps...

---

### Post by Fitch on 2010-03-30
52 years old and trying to run a guest house for a living,  C++ is a little too much for me.

What's Int and Void?

---

### Post by xifer on 2010-03-30
You need to talk to a c++ person which I'm not - although I have some exposure.

those error messages you had related to declarations of objects in the header files.

The declarations appear to malformed - missing the TYPE of the object.


Some common types are int (integer) uint (unsigned integer) and unsigned char (which your log refers to but which doesn't make much sense to me).  void means there is no type but it it required to specify that.  You may care to try and edit the offending .h files and see if you can tidy this up.  Or ask for help on a c++ dev forum - try the kde team if all else fails.

---

### Post by Fitch on 2010-03-30
Thanks for the info.

However, Karmic just did an upgrade, so all the KDE headers that I painstakingly installed in the last week have gone.

./configure now dumps out after about 5 lines.

Not going through all that again.

Cheers anyway.

---

### Post by xifer on 2010-03-30
> **Fitch said:**
> Thanks for the info.

However, Karmic just did an upgrade, so all the KDE headers that I painstakingly installed in the last week have gone.

./configure now dumps out after about 5 lines.

Not going through all that again.

Cheers anyway.

bummer.  It is possible to ''pin'' packages in your catalogue to prevent this occurring again.

see this link for more info

[https://help.ubuntu.com/community/PinningHowto](https://help.ubuntu.com/community/PinningHowto)

---

### Post by Fitch on 2010-03-30
As I had previously decided that kmsgmodem was never going to work, no matter what (there are too many obsolete packages - and support for the application stopped in 2004) I threw in the towel and wiped all 114 installations that got ./configure working.

Support for tkvoice stopped in 2006 I think, so the faxes will never be retrieved.  Shame really, I switch the computers off at night to reduce fire risk (and electricity bills), so the stand alone modem was ideal, as a normal fax machine (which I have) prints everything, 90% of which is spam (yes fax machines get it as well), and is therefore costly on the consumables.

Only Microsoft Widows has the answer for this one I'm afraid (and no, wine doesn't work with the windows applications - I've tried).

Never mind, Linux was a good idea, pity it didn't catch on...

---

### Post by xifer on 2010-03-30
> **Fitch said:**
> As I had previously decided that kmsgmodem was never going to work, no matter what (there are too many obsolete packages - and support for the application stopped in 2004) I threw in the towel and wiped all 114 installations that got ./configure working.

Support for tkvoice stopped in 2006 I think, so the faxes will never be retrieved.  Shame really, I switch the computers off at night to reduce fire risk (and electricity bills), so the stand alone modem was ideal, as a normal fax machine (which I have) prints everything, 90% of which is spam (yes fax machines get it as well), and is therefore costly on the consumables.

Only Microsoft Widows has the answer for this one I'm afraid (and no, wine doesn't work with the windows applications - I've tried).

Never mind, Linux was a good idea, pity it didn't catch on...

That's a bit harsh.  Just cos you have some unsupported hardware?  Would it be bad of me to ask why the fsck you need to use faxes anyway?  Sorry, could you not persuade people to use email instead?  e.g. banks & estate agents etc requiring faxed signatures for authorisation - wtf - they better do not do that on my account!

Sorry you haven't got it sorted. In this case the windows support is easily available so yeah - use it.  But it could have been made to work with the right technical assistance.

---

### Post by Fitch on 2010-03-31
Every now and then, after a few weeks of going round in circles (happens a lot) I do tend to take it out on the keyboard.  Sorry about that.

We get a lot of deaf and dumb people staying here, due to their HQ being across the road.
Their preference is to fax through bookings as most of them are a bit too old and reluctant to learn computers.

Many companies still send their remittance advices by fax, and yes, even the bank did till very recently..

We spent several thousands on a telephone system - which will take another 2 years to pay off, but it does have a night service - at 11 pm both lines switch to the modem so we can actually get to sleep at night.
The message modem is ideal for that.

I'm going to get drunk tonight and chill before I dust off any XP disks.

I'll think about it in the morning.

---

### Post by Fitch on 2010-04-01
Tried tkusr.  managed to get the gui up after a fight.

Started another thread just to see if anyone is clever enough to figure out why the g3 output is scrambled.

This thread is no more - unsolvable. again.

---

