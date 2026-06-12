---
title: "How do I undo a set of updates?  Half my media players don't work now."
date: 2009-05-24
forum: General Help
---

### Post by Mashuteichou on 2009-05-24
Basically, I installed a couple repositories from the 

[http://ubuntuforums.org/showthread.php?t=617900&highlight=avast+terminal](http://ubuntuforums.org/showthread.php?t=617900&highlight=avast+terminal)

forum, and I updated half the stuff down the list, but had trouble with some of it.  Then today, my update manager had a list of updates, but it said "partial update" because some things weren't supported or something.  

Heres what happens when I hit check in the update manager, it goes through 131 things,, then comes up with this error.  

W: GPG error: [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263

Since I already updated, its up-to-date and I can't post exactly what it said.  

I remember it had alot of random codecs or something in the updates.  Some were marked, some werent.  

When it downloaded, it said something like, 15 to be deleted, 5 to be installed, 6 to be updated.  I figured, ok, and hit install.  Afterwards, a few things happened.

VLC was deleted and won't install now.  Even under Synaptic Package Manager.  I click on the VLC part, and here is what comes up, 

vlc:
 Depends: vlc-nox but it is not going to be installed

So I click on the VLC-Nox part.  Here is what comes up:

vlc-nox:
 Depends: libavcodec52 but it is not going to be installed or
 	libavcodec-unstripped-52 but it is not going to be installed
 Depends: libavformat52 but it is not going to be installed or
 	libavformat-unstripped-52 but it is not going to be installed

Then it just goes back to the package manager with nothing done. 

I loaded Amarok, it doesn't play anything now.  It just sits in the playlist and does nothing.  When I double click, a small error message appears in the left bottom corner, "Too many errors encountered in the playlist.  Playback stopped."  

Music still plays in the other players, like MPlayer and stuff.  

So how do I fix things?  It worked better prior to the update.  Also, it looked like when I updated from 8.10 to 9.04 as far as the update window.  It started in the update manager, but went to the external window like it was updating the whole system.  But I still have 9.04.  

Thanks for any help.

---

### Post by Super TWiT on 2009-05-24
Try disabling the repositories you added.  After that, I think it will update the players to the old version.  Also, I think you could force version install on the programs, but you would have to keep reinstalling these as every time a new update came out from the other repositories, it would try to install itself.

---

### Post by Mashuteichou on 2009-05-24
It didn't work in the Update manager or add/remove, but it appears the Synaptic Manager is working correctly.  Its removing things this time instead of just trying to install.  I will let you know if it worked.

---

### Post by Mashuteichou on 2009-05-24
Ok, that fixed VLC, but Amarok is really messed up now.  I first tried opening a song, same problem as before.  I tried opening a song in the library part, and it had a fatal error and closed.  

Here is that error message:

Application: Amarok (amarok), signal SIGABRT
[Current thread is 0 (LWP 14543)]

Thread 14 (Thread 0xb0ca7b90 (LWP 14544)):
#0  0xb7ee2430 in __kernel_vsyscall ()
#1  0xb775b412 in pthread_cond_timedwait@@GLIBC_2.3.2 () from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb0e13ae3 in ?? () from /usr/lib/libxine.so.1

Thread 13 (Thread 0xb0422b90 (LWP 14545)):
#0  0xb42fb0ac in clock_gettime () from /lib/tls/i686/cmov/librt.so.1
#1  0xb699d06b in ?? () from /usr/lib/libQtCore.so.4
#2  0xb699d241 in ?? () from /usr/lib/libQtCore.so.4
#3  0xb699b553 in ?? () from /usr/lib/libQtCore.so.4
#4  0xb43976f6 in g_main_context_check () from /usr/lib/libglib-2.0.so.0
#5  0xb4397fdd in ?? () from /usr/lib/libglib-2.0.so.0
#6  0xb4398268 in g_main_context_iteration () from /usr/lib/libglib-2.0.so.0
#7  0xb699b457 in QEventDispatcherGlib::processEvents () from /usr/lib/libQtCore.so.4
#8  0xb696e06a in QEventLoop::processEvents () from /usr/lib/libQtCore.so.4
#9  0xb696e4aa in QEventLoop::exec () from /usr/lib/libQtCore.so.4
#10 0xb6878639 in QThread::exec () from /usr/lib/libQtCore.so.4
#11 0xb0e6120a in ?? () from /usr/lib/kde4/plugins/phonon_backend/phonon_xine.so
#12 0xb687b96e in ?? () from /usr/lib/libQtCore.so.4
#13 0xb77574ff in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#14 0xb668149e in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 12 (Thread 0xabc20b90 (LWP 14553)):
#0  0xb7ee2430 in __kernel_vsyscall ()
#1  0xb66797b1 in select () from /lib/tls/i686/cmov/libc.so.6
#2  0xb694d380 in ?? () from /usr/lib/libQtCore.so.4
#3  0xb687b96e in ?? () from /usr/lib/libQtCore.so.4
#4  0xb77574ff in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#5  0xb668149e in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 11 (Thread 0xafc1bb90 (LWP 14555)):
#0  0xb7ee2430 in __kernel_vsyscall ()
#1  0xb775b0e5 in pthread_cond_wait@@GLIBC_2.3.2 () from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb687c9b2 in QWaitCondition::wait () from /usr/lib/libQtCore.so.4
#3  0xb5cdc148 in ?? () from /usr/lib/libthreadweaver.so.4
#4  0xb5cdeeec in ?? () from /usr/lib/libthreadweaver.so.4
#5  0xb5cdad2b in ?? () from /usr/lib/libthreadweaver.so.4
#6  0xb5cdefea in ?? () from /usr/lib/libthreadweaver.so.4
#7  0xb5cdc6d3 in ?? () from /usr/lib/libthreadweaver.so.4
#8  0xb5cdf009 in ?? () from /usr/lib/libthreadweaver.so.4
#9  0xb5cdc6d3 in ?? () from /usr/lib/libthreadweaver.so.4
#10 0xb5cdf009 in ?? () from /usr/lib/libthreadweaver.so.4
#11 0xb5cdc6d3 in ?? () from /usr/lib/libthreadweaver.so.4
#12 0xb5cdcfbe in ?? () from /usr/lib/libthreadweaver.so.4
#13 0xb5cdd5fb in ThreadWeaver::Thread::run () from /usr/lib/libthreadweaver.so.4
#14 0xb687b96e in ?? () from /usr/lib/libQtCore.so.4
#15 0xb77574ff in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#16 0xb668149e in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 10 (Thread 0xaf2ffb90 (LWP 14556)):
#0  0xb7ee2430 in __kernel_vsyscall ()
#1  0xb6676ae7 in poll () from /lib/tls/i686/cmov/libc.so.6
#2  0xb0453912 in ?? () from /usr/lib/libpulse.so.0
#3  0xb04433c0 in pa_mainloop_poll () from /usr/lib/libpulse.so.0
#4  0xb0444d43 in pa_mainloop_iterate () from /usr/lib/libpulse.so.0
#5  0xb0444e14 in pa_mainloop_run () from /usr/lib/libpulse.so.0
#6  0xb04536c3 in ?? () from /usr/lib/libpulse.so.0
#7  0xb047def2 in ?? () from /usr/lib/libpulse.so.0
#8  0xb77574ff in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#9  0xb668149e in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 9 (Thread 0xad7f8b90 (LWP 14557)):
#0  0xb7ee2430 in __kernel_vsyscall ()
#1  0xb775b0e5 in pthread_cond_wait@@GLIBC_2.3.2 () from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb0e24d8e in ?? () from /usr/lib/libxine.so.1
Backtrace stopped: previous frame inner to this frame (corrupt stack?)

Thread 8 (Thread 0xa741eb90 (LWP 14559)):
#0  0xb7ee2430 in __kernel_vsyscall ()
#1  0xb66797b1 in select () from /lib/tls/i686/cmov/libc.so.6
#2  0xb0e3d7d6 in xine_usec_sleep () from /usr/lib/libxine.so.1
#3  0x00000000 in ?? ()

Thread 7 (Thread 0xa4184b90 (LWP 14567)):
#0  0xb7ee2430 in __kernel_vsyscall ()
#1  0xb775b0e5 in pthread_cond_wait@@GLIBC_2.3.2 () from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb687c9b2 in QWaitCondition::wait () from /usr/lib/libQtCore.so.4
#3  0xb5cdc148 in ?? () from /usr/lib/libthreadweaver.so.4
#4  0xb5cdeeec in ?? () from /usr/lib/libthreadweaver.so.4
#5  0xb5cdad2b in ?? () from /usr/lib/libthreadweaver.so.4
#6  0xb5cdefea in ?? () from /usr/lib/libthreadweaver.so.4
#7  0xb5cdc6d3 in ?? () from /usr/lib/libthreadweaver.so.4
#8  0xb5cdf009 in ?? () from /usr/lib/libthreadweaver.so.4
#9  0xb5cdc6d3 in ?? () from /usr/lib/libthreadweaver.so.4
#10 0xb5cdcfbe in ?? () from /usr/lib/libthreadweaver.so.4
#11 0xb5cdd5fb in ThreadWeaver::Thread::run () from /usr/lib/libthreadweaver.so.4
#12 0xb687b96e in ?? () from /usr/lib/libQtCore.so.4
#13 0xb77574ff in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#14 0xb668149e in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 6 (Thread 0xa3983b90 (LWP 14568)):
#0  0xb7ee2430 in __kernel_vsyscall ()
#1  0xb775b0e5 in pthread_cond_wait@@GLIBC_2.3.2 () from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb687c9b2 in QWaitCondition::wait () from /usr/lib/libQtCore.so.4
#3  0xb5cdc148 in ?? () from /usr/lib/libthreadweaver.so.4
#4  0xb5cdeeec in ?? () from /usr/lib/libthreadweaver.so.4
#5  0xb5cdad2b in ?? () from /usr/lib/libthreadweaver.so.4
#6  0xb5cdefea in ?? () from /usr/lib/libthreadweaver.so.4
#7  0xb5cdc6d3 in ?? () from /usr/lib/libthreadweaver.so.4
#8  0xb5cdf009 in ?? () from /usr/lib/libthreadweaver.so.4
#9  0xb5cdc6d3 in ?? () from /usr/lib/libthreadweaver.so.4
#10 0xb5cdf009 in ?? () from /usr/lib/libthreadweaver.so.4
#11 0xb5cdc6d3 in ?? () from /usr/lib/libthreadweaver.so.4
#12 0xb5cdf009 in ?? () from /usr/lib/libthreadweaver.so.4
#13 0xb5cdc6d3 in ?? () from /usr/lib/libthreadweaver.so.4
#14 0xb5cdcfbe in ?? () from /usr/lib/libthreadweaver.so.4
#15 0xb5cdd5fb in ThreadWeaver::Thread::run () from /usr/lib/libthreadweaver.so.4
#16 0xb687b96e in ?? () from /usr/lib/libQtCore.so.4
#17 0xb77574ff in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#18 0xb668149e in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 5 (Thread 0x96202b90 (LWP 14591)):
#0  0xb7ee2430 in __kernel_vsyscall ()
#1  0xb775b0e5 in pthread_cond_wait@@GLIBC_2.3.2 () from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb687c9b2 in QWaitCondition::wait () from /usr/lib/libQtCore.so.4
#3  0xb5cdc148 in ?? () from /usr/lib/libthreadweaver.so.4
#4  0xb5cdeeec in ?? () from /usr/lib/libthreadweaver.so.4
#5  0xb5cdad2b in ?? () from /usr/lib/libthreadweaver.so.4
#6  0xb5cdefea in ?? () from /usr/lib/libthreadweaver.so.4
#7  0xb5cdc6d3 in ?? () from /usr/lib/libthreadweaver.so.4
#8  0xb5cdcfbe in ?? () from /usr/lib/libthreadweaver.so.4
#9  0xb5cdd5fb in ThreadWeaver::Thread::run () from /usr/lib/libthreadweaver.so.4
#10 0xb687b96e in ?? () from /usr/lib/libQtCore.so.4
#11 0xb77574ff in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#12 0xb668149e in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 4 (Thread 0xa6834b90 (LWP 14624)):
#0  0xb7ee2430 in __kernel_vsyscall ()
#1  0xb775b0e5 in pthread_cond_wait@@GLIBC_2.3.2 () from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb0e17246 in ?? () from /usr/lib/libxine.so.1
#3  0x00000000 in ?? ()

Thread 3 (Thread 0xa5e66b90 (LWP 14625)):
#0  0xb7ee2430 in __kernel_vsyscall ()
#1  0xb775b0e5 in pthread_cond_wait@@GLIBC_2.3.2 () from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb0e17246 in ?? () from /usr/lib/libxine.so.1
#3  0x00000000 in ?? ()

Thread 2 (Thread 0xa5665b90 (LWP 14626)):
#0  0xb7ee2430 in __kernel_vsyscall ()
#1  0xb775b0e5 in pthread_cond_wait@@GLIBC_2.3.2 () from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb0e27bd2 in ?? () from /usr/lib/libxine.so.1
#3  0x00000000 in ?? ()

Thread 1 (Thread 0xb2ef9950 (LWP 14543)):
[KCrash Handler]
#6  0xb7ee2430 in __kernel_vsyscall ()
#7  0xb65c86d0 in raise () from /lib/tls/i686/cmov/libc.so.6
#8  0xb65ca098 in abort () from /lib/tls/i686/cmov/libc.so.6
#9  0xb6873595 in qt_message_output () from /usr/lib/libQtCore.so.4
#10 0xb6873681 in qFatal () from /usr/lib/libQtCore.so.4
#11 0xb6873775 in qt_assert () from /usr/lib/libQtCore.so.4
#12 0xb7a0ba40 in EngineController::slotAboutToFinish () from /usr/lib/libamaroklib.so.1
#13 0xb7a0f8ff in EngineController::qt_metacall () from /usr/lib/libamaroklib.so.1
#14 0xb6985ca8 in QMetaObject::activate () from /usr/lib/libQtCore.so.4
#15 0xb6986932 in QMetaObject::activate () from /usr/lib/libQtCore.so.4
#16 0xb5c4b667 in Phonon::MediaObject::aboutToFinish () from /usr/lib/libphonon.so.4
#17 0xb5c4d523 in ?? () from /usr/lib/libphonon.so.4
#18 0xb5c4e19f in Phonon::MediaObject::qt_metacall () from /usr/lib/libphonon.so.4
#19 0xb6985ca8 in QMetaObject::activate () from /usr/lib/libQtCore.so.4
#20 0xb6986932 in QMetaObject::activate () from /usr/lib/libQtCore.so.4
#21 0xb0e7ad07 in ?? () from /usr/lib/kde4/plugins/phonon_backend/phonon_xine.so
#22 0xb0e7c440 in ?? () from /usr/lib/kde4/plugins/phonon_backend/phonon_xine.so
#23 0xb0e7ef29 in ?? () from /usr/lib/kde4/plugins/phonon_backend/phonon_xine.so
#24 0xb697e8fb in QMetaCallEvent::placeMetaCall () from /usr/lib/libQtCore.so.4
#25 0xb69803a0 in QObject::event () from /usr/lib/libQtCore.so.4
#26 0xb6e40e9c in QApplicationPrivate::notify_helper () from /usr/lib/libQtGui.so.4
#27 0xb6e4919e in QApplication::notify () from /usr/lib/libQtGui.so.4
#28 0xb7d2f94d in KApplication::notify () from /usr/lib/libkdeui.so.5
#29 0xb696fa3b in QCoreApplication::notifyInternal () from /usr/lib/libQtCore.so.4
#30 0xb6970695 in QCoreApplicationPrivate::sendPostedEvents () from /usr/lib/libQtCore.so.4
#31 0xb697088d in QCoreApplication::sendPostedEvents () from /usr/lib/libQtCore.so.4
#32 0xb699b7ef in ?? () from /usr/lib/libQtCore.so.4
#33 0xb4394b88 in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
#34 0xb43980eb in ?? () from /usr/lib/libglib-2.0.so.0
#35 0xb4398268 in g_main_context_iteration () from /usr/lib/libglib-2.0.so.0
#36 0xb699b438 in QEventDispatcherGlib::processEvents () from /usr/lib/libQtCore.so.4
#37 0xb6ee2365 in ?? () from /usr/lib/libQtGui.so.4
#38 0xb696e06a in QEventLoop::processEvents () from /usr/lib/libQtCore.so.4
#39 0xb696e4aa in QEventLoop::exec () from /usr/lib/libQtCore.so.4
#40 0xb6970959 in QCoreApplication::exec () from /usr/lib/libQtCore.so.4
#41 0xb6e40d17 in QApplication::exec () from /usr/lib/libQtGui.so.4
#42 0x0814c4b2 in _start ()

---

### Post by Super TWiT on 2009-05-24
Try deleting the amorak preferences file.  If that doesn't work, try reinstalling amorak.  If it still doesn't work, try reinstalling some of its key dependencies.

---

