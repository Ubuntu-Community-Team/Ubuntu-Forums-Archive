---
title: "Well, I think I broke Ubuntu [Long Post Warning]"
date: 2009-05-15
forum: General Help
---

### Post by Riktol on 2009-05-15
**Warning: This post is very long and verbose. There is a summary at the bottom**
[edit]I am running Ubuntu 9.04 on a custom built machine. I also didn't manage to get the restricted drivers working (just in case this was important)[/edit]
I have had this problem for a while now and have been trying to fix it without success.
Mostly my computer works with the exception of package management.
The problem stems from the package manager but there is nothing actually wrong with apt as far as I know.


I can't remember the exact circumstances (it was probably more than 2 weeks ago) but I tried to download and install somethings (I never seem to only find one thing in the app manager, there is always something else which catches my eye) or else I tried to download and install VLC from the package manager (it wasn't in the add/remove programs that I remember).

In this case it failed. I am fairly certain the problem was that it failed to get all the packages. This is quite common for me as I have to sit behind a proxy which hates actually doing anything other than giving you errors or 2bit/sec download speed (and I have a screenshot of that), but I digress.

I probably told it to go ahead and install what it could anyway (I am fairly sure was a mistake).
Having done that, I tried to get more/other things (at one point VLC) but have failed for various reasons and I cannot recall the order in which they happened.

For some time I was presented with messages stating that the software was unauthenticated. I didn't allow any of these downloads (even though I didn't see why it should be giving me this error) until I got the same from a update check. I allowed it to download and install (I don't recall the outcome of this but it may be important unfortunately). I suspect that I was also in error there and I should have sought help here.

I have recorded some of the error messages I have received.
I list the first few below separated where I think they are individual (I may be incorrect in this)

> E: /var/cache/apt/archives/libqtgui4_4.5.0-0ubuntu4_i386.deb: short read in buffer_copy (backend dpkg-deb during `./usr/lib/qt4/plugins/accessible/libqtaccessiblewidgets.so')

> E: /var/cache/apt/archives/libqtgui4_4.5.0-0ubuntu4_i386.deb: short read in buffer_copy (backend dpkg-deb during `./usr/lib/qt4/plugins/accessible/libqtaccessiblewidgets.so')

> E: /var/cache/apt/archives/libqtgui4_4.5.0-0ubuntu4_i386.deb: short read in buffer_copy (backend dpkg-deb during `./usr/lib/qt4/plugins/accessible/libqtaccessiblewidgets.so')
E: /var/cache/apt/archives/libqt4-webkit_4.5.0-0ubuntu4_i386.deb: short read in buffer_copy (backend dpkg-deb during `./usr/lib/libQtWebKit.so.4.5.0')
E: /var/cache/apt/archives/libqt4-xmlpatterns_4.5.0-0ubuntu4_i386.deb: short read in buffer_copy (backend dpkg-deb during `./usr/lib/libQtXmlPatterns.so.4.5.0')
E: /var/cache/apt/archives/qt4-qmake_4.5.0-0ubuntu4_i386.deb: short read in buffer_copy (backend dpkg-deb during `./usr/share/qt4/mkspecs/common/linux.conf')
E: /var/cache/apt/archives/libxrender-dev_1%3a0.9.4-2_i386.deb: corrupted filesystem tarfile - corrupted package archive
E: /var/cache/apt/archives/libqt4-dev_4.5.0-0ubuntu4_i386.deb: short read in buffer_copy (backend dpkg-deb during `./usr/bin/lrelease-qt4')

> E: /var/cache/apt/archives/libqtgui4_4.5.0-0ubuntu4_i386.deb: short read in buffer_copy (backend dpkg-deb during `./usr/lib/qt4/plugins/accessible/libqtaccessiblewidgets.so')
E: /var/cache/apt/archives/libqt4-webkit_4.5.0-0ubuntu4_i386.deb: short read in buffer_copy (backend dpkg-deb during `./usr/lib/libQtWebKit.so.4.5.0')
E: /var/cache/apt/archives/libqt4-xmlpatterns_4.5.0-0ubuntu4_i386.deb: short read in buffer_copy (backend dpkg-deb during `./usr/lib/libQtXmlPatterns.so.4.5.0')
E: /var/cache/apt/archives/qt4-qmake_4.5.0-0ubuntu4_i386.deb: short read in buffer_copy (backend dpkg-deb during `./usr/share/qt4/mkspecs/common/linux.conf')
E: /var/cache/apt/archives/libxrender-dev_1%3a0.9.4-2_i386.deb: corrupted filesystem tarfile - corrupted package archive
E: /var/cache/apt/archives/libqt4-dev_4.5.0-0ubuntu4_i386.deb: short read in buffer_copy (backend dpkg-deb during `./usr/bin/lrelease-qt4')

I am not really sure what to make of them but they indicate that something went wrong. It then (or sometime) instructed me to check the permissions on '/etc/apt/sources.list' which is owned by the root (I suspect that this is normal) and also to try and rebuild the packages using
```
sudo apt-get install build-essential checkinstall
```
which returned this:
> Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  dpkg-dev g++ g++-4.3 libstdc++6-4.3-dev patch
Suggested packages:
  gettext debian-keyring g++-multilib g++-4.3-multilib gcc-4.3-doc
  libstdc++6-4.3-dbg libstdc++6-4.3-doc diff-doc
The following NEW packages will be installed
  build-essential checkinstall dpkg-dev g++ g++-4.3 libstdc++6-4.3-dev patch
0 upgraded, 7 newly installed, 0 to remove and 0 not upgraded.
Need to get 6386kB of archives.
After this operation, 21.9MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get: 1 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/main libstdc++6-4.3-dev 4.3.3-5ubuntu4 [1356kB]
Get: 2 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/main g++-4.3 4.3.3-5ubuntu4 [4162kB]
Get: 3 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/main g++ 4:4.3.3-1ubuntu1 [1438B]
Get: 4 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/main patch 2.5.9-5 [100kB]
Get: 5 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/main dpkg-dev 1.14.24ubuntu1 [643kB]
Get: 6 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/main build-essential 11.4 [7172B]
Get: 7 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/universe checkinstall 1.6.1-8 [116kB]
Fetched 6386kB in 1s (4208kB/s)   
Selecting previously deselected package libstdc++6-4.3-dev.
(Reading database ... 122405 files and directories currently installed.)
Unpacking libstdc++6-4.3-dev (from .../libstdc++6-4.3-dev_4.3.3-5ubuntu4_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libstdc++6-4.3-dev_4.3.3-5ubuntu4_i386.deb (--unpack):
 corrupted filesystem tarfile - corrupted package archive
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Selecting previously deselected package g++-4.3.
Unpacking g++-4.3 (from .../g++-4.3_4.3.3-5ubuntu4_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/g++-4.3_4.3.3-5ubuntu4_i386.deb (--unpack):
 corrupted filesystem tarfile - corrupted package archive
Selecting previously deselected package g++.
Unpacking g++ (from .../g++_4%3a4.3.3-1ubuntu1_i386.deb) ...
Selecting previously deselected package patch.
Unpacking patch (from .../patch_2.5.9-5_i386.deb) ...
Selecting previously deselected package dpkg-dev.
Unpacking dpkg-dev (from .../dpkg-dev_1.14.24ubuntu1_all.deb) ...
Selecting previously deselected package build-essential.
Unpacking build-essential (from .../build-essential_11.4_i386.deb) ...
Selecting previously deselected package checkinstall.
Unpacking checkinstall (from .../checkinstall_1.6.1-8_i386.deb) ...
Processing triggers for man-db ...
Errors were encountered while processing:
 /var/cache/apt/archives/libstdc++6-4.3-dev_4.3.3-5ubuntu4_i386.deb
 /var/cache/apt/archives/g++-4.3_4.3.3-5ubuntu4_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

After this, the next error I recorded is
> E: /var/cache/apt/archives/libstdc++6-4.3-dev_4.3.3-5ubuntu4_i386.deb: corrupted filesystem tarfile - corrupted package archive
E: /var/cache/apt/archives/g++-4.3_4.3.3-5ubuntu4_i386.deb: corrupted filesystem tarfile - corrupted package archive
This is the essential problem as far as I can determine. I am not sure how to fix it and I don't what to file a bug report (unless PIBKAC is a valid bug  ;) )

Having received this error I was instructed by an error message to run 
```
sudo apt-get install -f
```
which returned this
> Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies...Done
The following extra packages will be installed:
  g++-4.3 libstdc++6-4.3-dev
Suggested packages:
  g++-4.3-multilib gcc-4.3-doc libstdc++6-4.3-dbg libstdc++6-4.3-doc
The following NEW packages will be installed
  g++-4.3 libstdc++6-4.3-dev
0 upgraded, 2 newly installed, 0 to remove and 30 not upgraded.
2 not fully installed or removed.
Need to get 0B/5518kB of archives.
After this operation, 19.1MB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 122639 files and directories currently installed.)
Unpacking libstdc++6-4.3-dev (from .../libstdc++6-4.3-dev_4.3.3-5ubuntu4_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libstdc++6-4.3-dev_4.3.3-5ubuntu4_i386.deb (--unpack):
 corrupted filesystem tarfile - corrupted package archive
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Unpacking g++-4.3 (from .../g++-4.3_4.3.3-5ubuntu4_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/g++-4.3_4.3.3-5ubuntu4_i386.deb (--unpack):
 corrupted filesystem tarfile - corrupted package archive
Processing triggers for man-db ...
Errors were encountered while processing:
 /var/cache/apt/archives/libstdc++6-4.3-dev_4.3.3-5ubuntu4_i386.deb
 /var/cache/apt/archives/g++-4.3_4.3.3-5ubuntu4_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

I have tried to fix the broken package (and I also am forced to install a missing dependant package which may be causing problems) when I try and fix this with apt. I also tried to use a live CD as the source for the files but I always get the same error (the one I marked as the main problem).

**In Summary**
For the most part my computer runs smoothly and well however:
I am getting the following error whenever I try and do anything package manager related
> E: /var/cache/apt/archives/libstdc++6-4.3-dev_4.3.3-5ubuntu4_i386.deb: corrupted filesystem tarfile - corrupted package archive
E: /var/cache/apt/archives/g++-4.3_4.3.3-5ubuntu4_i386.deb: corrupted filesystem tarfile - corrupted package archive
The Add/Remove Applications refuses to run and asks me to check the permissions on '/etc/apt/sources.list' and to run
```
sudo apt-get update
```
and
```
sudo apt-get install -f
```
None of this seems to help.
Any advice, constructive criticism and fix attempts are welcome.
Advice to the extent that I should return to windows is not (I have enough unexplained Kernal Errors there thanks).

---

### Post by quixote on 2009-05-17
have you already tried ```
sudo dpkg --configure -a
```
That's usually fixes broken packages, although not always.

---

### Post by Partyboi2 on 2009-05-17
Hi, try cleaning out the cache first.
```
sudo apt-get clean
sudo apt-get -f install

```

---

### Post by Riktol on 2009-05-17
I ran
```
sudo apt-get clean
```
but it didn't seem to do anything.
I then tried
```
sudo dpkg --configure -a
```
which gave
> dpkg: dependency problems prevent configuration of g++:
 g++ depends on g++-4.3 (>= 4.3.3-1); however:
  Package g++-4.3 is not installed.
dpkg: error processing g++ (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of build-essential:
 build-essential depends on g++ (>= 4:4.3.1); however:
  Package g++ is not configured yet.
dpkg: error processing build-essential (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 g++
 build-essential

I tried 'get clean' again but again it didn't seem to do anything so I moved on to
```
sudo apt-get -f install
```
Which gave
> Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies...Done
The following extra packages will be installed:
  g++-4.3 libstdc++6-4.3-dev
Suggested packages:
  g++-4.3-multilib gcc-4.3-doc libstdc++6-4.3-dbg libstdc++6-4.3-doc
The following NEW packages will be installed
  g++-4.3 libstdc++6-4.3-dev
0 upgraded, 2 newly installed, 0 to remove and 69 not upgraded.
2 not fully installed or removed.
Need to get 0B/5518kB of archives.
After this operation, 19.1MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Media Change: Please insert the disc labelled
 'Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)'
in the drive ‘/cdrom/’ and press enter

(Reading database ... 122639 files and directories currently installed.)
Unpacking libstdc++6-4.3-dev (from .../libstdc++6-4.3-dev_4.3.3-5ubuntu4_i386.deb) ...
Unpacking g++-4.3 (from .../g++-4.3_4.3.3-5ubuntu4_i386.deb) ...
Processing triggers for man-db ...
Setting up g++-4.3 (4.3.3-5ubuntu4) ...
Setting up libstdc++6-4.3-dev (4.3.3-5ubuntu4) ...
Setting up g++ (4:4.3.3-1ubuntu1) ...

Setting up build-essential (11.4) ...

After doing this it stopped and loaded the update manager (I have missed quite a few things since updates stopped working).
I am not quite sure why it wanted the files from the live cd (I did try and use it as the source for fixing things earlier this week and I noticed that it is checked in the list of software sources in synaptic)

I loaded up the Add/Remove Programs which didn't complain at all and Synaptic lists no broken or missing packages.
I can't think of anything else to try and check to make sure that everything is back to normal (or rather, not normal at all :P)

If there is nothing else, I'll get back to installing updates.
Thanks
Riktol

---

### Post by Partyboi2 on 2009-05-17
Open Software Sources and make sure that the box under "Installable from Cdrom/dvd" is un ticked, so that it does not look to the cdrom.

When you ran apt-get clean it removed all the downloaded deb packages that are stored in  /var/cache/apt/archives, the problem you were having was probably related to corrupt downloaded deb package(s).

---

### Post by quixote on 2009-05-17
Glad to hear that it sounds like you have things sorted out!

---

