---
title: "CNR to install games"
date: 2007-10-12
forum: Gaming &amp; Leisure
---

### Post by whistlerspa on 2007-10-12
I thought I'd try this client to install a few games like Quake 2. 

Download and installed as per cnr.com instructions. Ran the client , found my software and clicked install. It downloaded the *.cnr file and ran the synchronization file and then crashed. Does this every time. 

Also the client seems to close itself all the time so I can't really configure it properly.

Can't get help on cnr forums as they won't accept my login and password (even though the main site does). 

All seems a bit bizarre really. Does this work for anyone?

---

### Post by penquin on 2007-10-12
I have the same problem.  the only solution I can come up with is to copy and paste the discription of the CNR program to snaptic search and download.[http://ubuntuforums.org/images/smilies/icon_sad.gif](http://ubuntuforums.org/images/smilies/icon_sad.gif)

---

### Post by S3Indiana on 2007-10-12
If you like to assist in troubleshooting: from the console run: ```
sudo gdb cnr
```then ```
run
``` and after the failure ```
bt
```Reply with the results. Thx. in advance...

---

### Post by whistlerspa on 2007-10-12
Sorry but I haven't a clue what you mean by this, can you explain please?

---

### Post by whistlerspa on 2007-10-12
Here's the terminal stuff 


GNU gdb 6.6-debian
Copyright (C) 2006 Free Software Foundation, Inc.
GDB is free software, covered by the GNU General Public License, and you are
welcome to change it and/or distribute copies of it under certain conditions.
Type "show copying" to see the conditions.
There is absolutely no warranty for GDB.  Type "show warranty" for details.
This GDB was configured as "i486-linux-gnu"...
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
(gdb) run
Starting program: /usr/bin/cnr 
[Thread debugging using libthread_db enabled]
[New Thread -1234356528 (LWP 9763)]
[Debug]Qt: gdb: -nograb added to command-line options.
         Use the -dograb option to enforce grabbing.
[New Thread -1238111344 (LWP 9769)]
[New Thread -1246504048 (LWP 9770)]
[Thread -1238111344 (LWP 9769) exited]
[Thread -1246504048 (LWP 9770) exited]
bt
[New Thread -1246504048 (LWP 9774)]
[Debug]Creating InstallComplete
10/13 14:05:40.904|../src/lib/actions/InitAction.cpp|438|Action|lightup completed.
snapVersion = 2

Program received signal SIGSEGV, Segmentation fault.
[Switching to Thread -1246504048 (LWP 9774)]
0x0805e762 in q_atomic_increment (ptr=0x0)
    at /usr/include/qt4/QtCore/qatomic_i386.h:70
70      /usr/include/qt4/QtCore/qatomic_i386.h: No such file or directory.
        in /usr/include/qt4/QtCore/qatomic_i386.h
(gdb) bt
#0  0x0805e762 in q_atomic_increment (ptr=0x0)
    at /usr/include/qt4/QtCore/qatomic_i386.h:70
#1  0x0805e7c9 in QBasicAtomic::ref (this=0x0)
    at /usr/include/qt4/QtCore/qatomic.h:71
#2  0x0805e9a1 in QString (this=0xb5b25a98, s=@0xb5b259b4)
    at /usr/include/qt4/QtCore/qstring.h:608
#3  0x0805ea12 in CNRClient::Package::Version::operator QString (
    this=0xb5b259b0) at ../src/lib/common/Package.hpp:70
#4  0x0805ea3a in CNRClient::Package::version (this=0xb5b259a8)
    at ../src/lib/common/Package.hpp:168
#5  0x080c106e in CNRClient::InitAction::update (this=0x81f45a8)
    at ../src/lib/actions/InitAction.cpp:685
#6  0x080c5cdf in CNRClient::InitAction::init (this=0x81f45a8, 
    userAuth=@0xb5b3cdbc) at ../src/lib/actions/InitAction.cpp:205
#7  0x080bf17b in CNRClient::ActionThread::runInitAction (this=0x81fbe70, 
    currentAction=0x81f45a8) at ../src/lib/actions/ActionThread.cpp:142
#8  0x080bfafd in CNRClient::ActionThread::run_process (this=0x81fbe70)
    at ../src/lib/actions/ActionThread.cpp:180
#9  0x080bfcf6 in CNRClient::ActionThread::qt_metacall (this=0x81fbe70, 
    _c=QMetaObject::InvokeMetaMethod, _id=6, _a=0xb5b3ce8c)
    at moc_dir/moc_ActionThread.cpp:83
#10 0xb71dbbc0 in QMetaObject::activate () from /usr/lib/libQtCore.so.4
#11 0xb71dc035 in QMetaObject::activate () from /usr/lib/libQtCore.so.4
---Type <return> to continue, or q <return> to quit---
#12 0x080bef83 in CNRClient::ActionThread::beginProcess (this=0x81fbe70)
    at moc_dir/moc_ActionThread.cpp:94
#13 0x080bf075 in CNRClient::ActionThread::run (this=0x81fbe70)
    at ../src/lib/actions/ActionThread.cpp:205
#14 0xb7114eb5 in ?? () from /usr/lib/libQtCore.so.4
#15 0x081fbe70 in ?? ()
#16 0x00000000 in ?? ()
(gdb) 

Does this mean anything to you?

---

### Post by whistlerspa on 2007-10-12
> **penquin said:**
> I have the same problem.  the only solution I can come up with is to copy and paste the discription of the CNR program to snaptic search and download.[http://ubuntuforums.org/images/smilies/icon_sad.gif](http://ubuntuforums.org/images/smilies/icon_sad.gif)

I meant what do you mean by this  - what is 'description' exactly?

---

### Post by penquin on 2007-10-13
Firefox
Internet & Networking : Web Browsers
Firefox empowers you to browse faster, more safely, and more efficiently than with any other browser.

this is an example of the blurb after the icon.  you would copy the following part "**Firefox empowers you to browse faster, more safely, and more efficiently than with any other browser**." 

this should bring up the only packages you need.  by the way quake 2 doesn't contain the rom of the game you must have the disc or at least thats what it sounds like.

---

### Post by S3Indiana on 2007-10-13
> **whistlerspa said:**
> Here's the terminal stuff 

Does this mean anything to you?Not me personally, but the developers are very appreciative (forwarded)...

---

