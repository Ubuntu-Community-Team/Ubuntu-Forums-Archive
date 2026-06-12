---
title: "Just installed KDE"
date: 2009-10-04
forum: Desktop Environments
---

### Post by kfitzenreiter on 2009-10-04
Well, I took the plunge and installed KDE just for kicks.  Now it appears I can choose my window manager on login.

Are there any pitfalls to doing this?  KDE seems a bit slower, but that could be because it is just learning the computer or something.

Any thoughts???

---

### Post by kfitzenreiter on 2009-10-04
Uh-Oh!!! It begins...

Error message is as follows....

The application Plasma Workspace (plasma) crashed and caused the signal 11 (SIGSEGV).
Please help us improve the software you use by filing a report at [http://bugs.kde.org](http://bugs.kde.org). Useful details include how to reproduce the error, documents that were loaded, etc.
Application: Plasma Workspace (plasma), signal SIGSEGV
[Current thread is 0 (LWP 16866)]

Thread 3 (Thread 0xa9574b90 (LWP 16993)):
#0  0xb7ff0430 in __kernel_vsyscall ()
#1  0xb51880e5 in pthread_cond_wait@@GLIBC_2.3.2 () from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb63402ed in pthread_cond_wait () from /lib/tls/i686/cmov/libc.so.6
#3  0xb652c9b2 in QWaitCondition::wait () from /usr/lib/libQtCore.so.4
#4  0xa98c7b9a in ?? () from /usr/lib/kde4/plasma_wallpaper_image.so
#5  0xb652b96e in ?? () from /usr/lib/libQtCore.so.4
#6  0xb51844ff in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#7  0xb633149e in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 2 (Thread 0xa8cc3b90 (LWP 17055)):
#0  0xb7ff0430 in __kernel_vsyscall ()
#1  0xb51880e5 in pthread_cond_wait@@GLIBC_2.3.2 () from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb63402ed in pthread_cond_wait () from /lib/tls/i686/cmov/libc.so.6
#3  0xb652c9b2 in QWaitCondition::wait () from /usr/lib/libQtCore.so.4
#4  0xb79ad152 in ?? () from /usr/lib/libQtNetwork.so.4
#5  0xb652b96e in ?? () from /usr/lib/libQtCore.so.4
#6  0xb51844ff in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#7  0xb633149e in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 1 (Thread 0xb4c75710 (LWP 16866)):
[KCrash Handler]
#6  0xa96b9be2 in TaskManager::GroupManager::add () from /usr/lib/libtaskmanager.so.4
#7  0xa96bbc7f in TaskManager::GroupManager::qt_metacall () from /usr/lib/libtaskmanager.so.4
#8  0xb6635ca8 in QMetaObject::activate () from /usr/lib/libQtCore.so.4
#9  0xb6636932 in QMetaObject::activate () from /usr/lib/libQtCore.so.4
#10 0xa96d44d3 in TaskManager::TaskManager::taskAdded () from /usr/lib/libtaskmanager.so.4
#11 0xa96d6786 in TaskManager::TaskManager::windowAdded () from /usr/lib/libtaskmanager.so.4
#12 0xa96d785c in TaskManager::TaskManager::qt_metacall () from /usr/lib/libtaskmanager.so.4
#13 0xb6635ca8 in QMetaObject::activate () from /usr/lib/libQtCore.so.4
#14 0xb6636932 in QMetaObject::activate () from /usr/lib/libQtCore.so.4
#15 0xb786e4c3 in KWindowSystem::windowAdded () from /usr/lib/libkdeui.so.5
#16 0xb7870b79 in ?? () from /usr/lib/libkdeui.so.5
#17 0xb7880207 in NETRootInfo::update () from /usr/lib/libkdeui.so.5
#18 0xb78805bf in NETRootInfo::event () from /usr/lib/libkdeui.so.5
#19 0xb7870f8d in ?? () from /usr/lib/libkdeui.so.5
#20 0xb7723c69 in KApplication::x11EventFilter () from /usr/lib/libkdeui.so.5
#21 0xb7fad4d7 in ?? () from /usr/lib/libkdeinit4_plasma.so
#22 0xb692ff3e in ?? () from /usr/lib/libQtGui.so.4
#23 0xb69426a8 in QApplication::x11ProcessEvent () from /usr/lib/libQtGui.so.4
#24 0xb696ec6a in ?? () from /usr/lib/libQtGui.so.4
#25 0xb4f82b88 in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
#26 0xb4f860eb in ?? () from /usr/lib/libglib-2.0.so.0
#27 0xb4f86268 in g_main_context_iteration () from /usr/lib/libglib-2.0.so.0
#28 0xb664b438 in QEventDispatcherGlib::processEvents () from /usr/lib/libQtCore.so.4
#29 0xb696e365 in ?? () from /usr/lib/libQtGui.so.4
#30 0xb661e06a in QEventLoop::processEvents () from /usr/lib/libQtCore.so.4
#31 0xb661e4aa in QEventLoop::exec () from /usr/lib/libQtCore.so.4
#32 0xb6620959 in QCoreApplication::exec () from /usr/lib/libQtCore.so.4
#33 0xb68ccd17 in QApplication::exec () from /usr/lib/libQtGui.so.4
#34 0xb7f9ab56 in kdemain () from /usr/lib/libkdeinit4_plasma.so
#35 0x08048712 in _start ()

---

### Post by RichardLinx on 2009-10-04
> **kfitzenreiter said:**
> Well, I took the plunge and installed KDE just for kicks.  Now it appears I can choose my window manager on login.

Are there any pitfalls to doing this?  KDE seems a bit slower, but that could be because it is just learning the computer or something.

Any thoughts???

Congratulations. It could be slower because now your computer has to load up both KDE and GNOME applications on login, instead of just GNOME apps.

Thoughts? Don't give up and get frustrated with it too early. Give it a fair chance and you might just find that you like it... K/Ubuntu doesn't do KDE justice..

---

### Post by fela on 2009-10-04
+1 to RichardLinx.

Actually I'm having a much better time with KDE on its own with Debian, than I ever did with KDE installed alongside Ubuntu. Probably it was loading loads of Gnome stuff and got really slow.

---

### Post by kfitzenreiter on 2009-10-04
I select from the two on startup, so does it still load up both "X" managers?

---

### Post by RichardLinx on 2009-10-05
> **kfitzenreiter said:**
> I select from the two on startup, so does it still load up both "X" managers?

No. But it loads up all the GNOME applications and the GTK+ libs.

---

### Post by ad_267 on 2009-10-05
Kubuntu Karmic looks to be much improved from Jaunty, from the testing I've done. And I find everything works better installing plain Kubuntu, rather than kubuntu-desktop alongside Ubuntu.

---

### Post by kfitzenreiter on 2009-10-05
Well, it's official.  I'm in over my head...
 
KDE and Gnome don't like each other very much.  Windows on the KDE desktop are crashing.  It now says KUBUNTU at startup which I didn't think would happen.  Gnome is missing the power button in the top right corner...
 
 In short, it is time to bid farewell to this installation of Ubuntu.....
 
I have four partitions on that hard disk, one of which is XP.  I may boot up with my Gatesian CD and fixmbr and fixboot, etc, to bring back XP and then reinstall Ubuntu over the top of it.  I'm debating whether or not I should download the beta of Karmic or stick with Jackalope.
 
Any thoughts from someone wiser than myself before I drive a stake through this Jackalope???

---

### Post by RichardLinx on 2009-10-05
> **kfitzenreiter said:**
> Well, it's official.  I'm in over my head...
 
KDE and Gnome don't like each other very much.  Windows on the KDE desktop are crashing.  It now says KUBUNTU at startup which I didn't think would happen.  Gnome is missing the power button in the top right corner...
 
 In short, it is time to bid farewell to this installation of Ubuntu.....
 
I have four partitions on that hard disk, one of which is XP.  I may boot up with my Gatesian CD and fixmbr and fixboot, etc, to bring back XP and then reinstall Ubuntu over the top of it.  I'm debating whether or not I should download the beta of Karmic or stick with Jackalope.
 
Any thoughts from someone wiser than myself before I drive a stake through this Jackalope???

It might just be easier to remove KDE instead of completely removing and reinstalling Ubuntu. If for some reason you feel like going through the entire installation + update process then don't forget to back up your data!

To remove KDE + Apps: [http://www.psychocats.net/ubuntu/puregnome.php](http://www.psychocats.net/ubuntu/puregnome.php)

---

### Post by kfitzenreiter on 2009-10-05
Thanks for your reply.
 
I think I'll try your link to remove KDE, etc, just to see how it goes...
 
I guess the reason I am ready to reinstall so quickly is that the machine I'm testing Ubuntu on is not really a pc I use for anything important.  As I've mentioned in a few other posts, I sort of collect friends, coworkers old pcs and coupled with a kvm device allows me to load and trash OS's left and right so to speak.  I can reformat and partition the entire drive without fear of losing any important data, which is always a good feeling.

---

