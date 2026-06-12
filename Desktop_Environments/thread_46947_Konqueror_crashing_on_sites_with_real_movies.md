---
title: "Konqueror crashing on sites with real movies"
date: 2005-07-06
forum: Desktop Environments
---

### Post by André on 2005-07-06
Hi everybody,

when i visit a site, that wants to play a real player movie konqueror just crashes.

I don't really have the need to play these files and i will follow any suggestion for completely turning them off, but the crashes from time to time are pretty disturbing.

Any ideas how to completely turn displaying real player movies off or how to get rid of the crashes??

Any help is so appreciated. Right now i am using firefox to avoid the crashes but there are some features in konqueror which make me prefer this browser and i really want to use it.

Greetings
André

---

### Post by André on 2005-07-06
Here is my backtracing output:

Backtracing i get the following output:

(no debugging symbols found)
Using host libthread_db library "/lib/libthread_db.so.1".
(no debugging symbols found)
`system-supplied DSO at 0xffffe000' has disappeared; keeping its symbols.
(no debugging symbols found)
... /* for sake of readibility i killed some of these messages */
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread 16384 (LWP 7633)]
[New Thread 32769 (LWP 8748)]
[New Thread 16386 (LWP 8749)]
[New Thread 32771 (LWP 8750)]
[New Thread 49156 (LWP 8751)]
[New Thread 65541 (LWP 8752)]
[New Thread 81926 (LWP 8753)]
[New Thread 98311 (LWP 8754)]
[New Thread 114696 (LWP 8755)]
(no debugging symbols found)
...
(no debugging symbols found)
[KCrash handler]
#6  0xb62be346 in QMemArray<QPoint>::detach () from /usr/lib/libkhtml.so.4
#7  0xb61efa39 in KHTMLPart::processObjectRequest ()
   from /usr/lib/libkhtml.so.4
#8  0xb61eedbc in KHTMLPart::requestObject () from /usr/lib/libkhtml.so.4
#9  0xb61ee546 in KHTMLPart::requestObject () from /usr/lib/libkhtml.so.4
#10 0xb62bf350 in QMemArray<QPoint>::detach () from /usr/lib/libkhtml.so.4
#11 0xb62c02f2 in QMemArray<QPoint>::detach () from /usr/lib/libkhtml.so.4
#12 0xb6225d43 in QPtrDict<QWidget>::deleteItem () from /usr/lib/libkhtml.so.4
#13 0xb6225d12 in QPtrDict<QWidget>::deleteItem () from /usr/lib/libkhtml.so.4
#14 0xb622bf9f in QPtrDict<QWidget>::deleteItem () from /usr/lib/libkhtml.so.4
#15 0xb6241e6e in KStaticDeleter<QPtrList<DOM::DocumentImpl> >::~KStaticDeleter () from /usr/lib/libkhtml.so.4
#16 0xb6241e10 in KStaticDeleter<QPtrList<DOM::DocumentImpl> >::~KStaticDeleter () from /usr/lib/libkhtml.so.4
#17 0xb6241c93 in KStaticDeleter<QPtrList<DOM::DocumentImpl> >::~KStaticDeleter () from /usr/lib/libkhtml.so.4
#18 0xb623fdbc in KStaticDeleter<QPtrList<DOM::DocumentImpl> >::~KStaticDeleter () from /usr/lib/libkhtml.so.4
#19 0xb6248990 in KStaticDeleter<QPtrList<DOM::DocumentImpl> >::~KStaticDeleter () from /usr/lib/libkhtml.so.4
#20 0xb62468db in KStaticDeleter<QPtrList<DOM::DocumentImpl> >::~KStaticDeleter () from /usr/lib/libkhtml.so.4
#21 0xb6247dae in KStaticDeleter<QPtrList<DOM::DocumentImpl> >::~KStaticDeleter () from /usr/lib/libkhtml.so.4
#22 0xb621da70 in QPtrDict<QWidget>::deleteItem () from /usr/lib/libkhtml.so.4
#23 0xb621d98b in QPtrDict<QWidget>::deleteItem () from /usr/lib/libkhtml.so.4
#24 0xb63a5197 in DOM::HTMLDocument::write () from /usr/lib/libkhtml.so.4
#25 0xb6323dec in EmbedLiveConnect::toString () from /usr/lib/libkhtml.so.4
#26 0xb63102fe in QPtrDict<khtml::CachedObjectClient>::deleteItem ()
   from /usr/lib/libkhtml.so.4
#27 0xb60df7d0 in KJS::Object::call () from /usr/lib/libkjs.so.1
#28 0xb60ad903 in KJS::timeClip () from /usr/lib/libkjs.so.1
#29 0xb60b1f5a in KJS::timeClip () from /usr/lib/libkjs.so.1
#30 0xb60b8956 in KJS::timeClip () from /usr/lib/libkjs.so.1
#31 0xb60b1d6f in KJS::timeClip () from /usr/lib/libkjs.so.1
#32 0xb60b7e73 in KJS::timeClip () from /usr/lib/libkjs.so.1
#33 0xb60dae8c in KJS::DeclaredFunctionImp::execute ()
   from /usr/lib/libkjs.so.1
#34 0xb60da240 in KJS::FunctionImp::call () from /usr/lib/libkjs.so.1
#35 0xb60df7d0 in KJS::Object::call () from /usr/lib/libkjs.so.1
#36 0xb60ad903 in KJS::timeClip () from /usr/lib/libkjs.so.1
#37 0xb60b1f5a in KJS::timeClip () from /usr/lib/libkjs.so.1
#38 0xb60b8956 in KJS::timeClip () from /usr/lib/libkjs.so.1
#39 0xb60b1d6f in KJS::timeClip () from /usr/lib/libkjs.so.1
#40 0xb60b7e73 in KJS::timeClip () from /usr/lib/libkjs.so.1
#41 0xb60cf757 in KJS::SourceCode::cleanup () from /usr/lib/libkjs.so.1
#42 0xb60e176a in KJS::Interpreter::evaluate () from /usr/lib/libkjs.so.1
#43 0xb635e4bf in EmbedLiveConnect::toString () from /usr/lib/libkhtml.so.4
#44 0xb61ddfed in KHTMLPart::executeScript () from /usr/lib/libkhtml.so.4
#45 0xb6244386 in KStaticDeleter<QPtrList<DOM::DocumentImpl> >::~KStaticDeleter () from /usr/lib/libkhtml.so.4
#46 0xb6243edb in KStaticDeleter<QPtrList<DOM::DocumentImpl> >::~KStaticDeleter () from /usr/lib/libkhtml.so.4
#47 0xb6243aac in KStaticDeleter<QPtrList<DOM::DocumentImpl> >::~KStaticDeleter () from /usr/lib/libkhtml.so.4
#48 0xb62469ab in KStaticDeleter<QPtrList<DOM::DocumentImpl> >::~KStaticDeleter () from /usr/lib/libkhtml.so.4
#49 0xb6247dae in KStaticDeleter<QPtrList<DOM::DocumentImpl> >::~KStaticDeleter () from /usr/lib/libkhtml.so.4
#50 0xb624957b in KStaticDeleter<QPtrList<DOM::DocumentImpl> >::~KStaticDeleter () from /usr/lib/libkhtml.so.4
#51 0xb6305e53 in QPtrList<DOM::StyleBaseImpl>::deleteItem ()
   from /usr/lib/libkhtml.so.4
#52 0xb6305da2 in QPtrList<DOM::StyleBaseImpl>::deleteItem ()
   from /usr/lib/libkhtml.so.4
#53 0xb6309e65 in QPtrList<DOM::StyleBaseImpl>::deleteItem ()
   from /usr/lib/libkhtml.so.4
#54 0xb630b39d in QPtrList<DOM::StyleBaseImpl>::deleteItem ()
   from /usr/lib/libkhtml.so.4
#55 0xb73c0067 in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#56 0xb7b84e3a in KIO::Job::result () from /usr/lib/libkio.so.4
#57 0xb7b6d12c in KIO::Job::emitResult () from /usr/lib/libkio.so.4
#58 0xb7b6e64c in KIO::SimpleJob::slotFinished () from /usr/lib/libkio.so.4
#59 0xb7b71ace in KIO::TransferJob::slotFinished () from /usr/lib/libkio.so.4
#60 0xb7b86e1d in KIO::TransferJob::qt_invoke () from /usr/lib/libkio.so.4
#61 0xb73c0067 in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#62 0xb73bfeae in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#63 0xb7b6333e in KIO::SlaveInterface::finished () from /usr/lib/libkio.so.4
#64 0xb7b61ea1 in KIO::SlaveInterface::dispatch () from /usr/lib/libkio.so.4
#65 0xb7b613a9 in KIO::SlaveInterface::dispatch () from /usr/lib/libkio.so.4
#66 0xb7b5eddb in KIO::Slave::gotInput () from /usr/lib/libkio.so.4
#67 0xb7b60af8 in KIO::Slave::qt_invoke () from /usr/lib/libkio.so.4
#68 0xb73c0067 in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#69 0xb73c01be in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#70 0xb76dbee0 in QSocketNotifier::activated () from /usr/lib/libqt-mt.so.3
#71 0xb73db036 in QSocketNotifier::event () from /usr/lib/libqt-mt.so.3
#72 0xb7368370 in QApplication::internalNotify () from /usr/lib/libqt-mt.so.3
#73 0xb73679d4 in QApplication::notify () from /usr/lib/libqt-mt.so.3
#74 0xb78b8ab5 in KApplication::notify () from /usr/lib/libkdecore.so.4
#75 0xb7358a10 in QEventLoop::activateSocketNotifiers ()
   from /usr/lib/libqt-mt.so.3
#76 0xb7314917 in QEventLoop::processEvents () from /usr/lib/libqt-mt.so.3
#77 0xb737974c in QEventLoop::enterLoop () from /usr/lib/libqt-mt.so.3
#78 0xb737960e in QEventLoop::exec () from /usr/lib/libqt-mt.so.3
#79 0xb736857b in QApplication::exec () from /usr/lib/libqt-mt.so.3
#80 0xb68df2bc in kdemain () from /usr/lib/libkdeinit_konqueror.so
#81 0xb697e776 in kdeinitmain () from /usr/lib/kde3/konqueror.so
#82 0x0804cbd2 in ?? ()
#83 0x00000004 in ?? ()
#84 0x08139e18 in ?? ()
#85 0x00000001 in ?? ()
#86 0x00000000 in ?? ()
#87 0x00000000 in ?? ()
#88 0x00000000 in ?? ()
#89 0x00000000 in ?? ()
#90 0x00000000 in ?? ()
#91 0x00000000 in ?? ()
#92 0x00000000 in ?? ()
#93 0x00000000 in ?? ()
#94 0x00000000 in ?? ()
#95 0x00000000 in ?? ()
#96 0x00000000 in ?? ()
#97 0x01000000 in ?? ()
#98 0x00000000 in ?? ()
#99 0x00000000 in ?? ()
#100 0x00000000 in ?? ()
#101 0x00000000 in ?? ()
#102 0x00000000 in ?? ()
#103 0x00000000 in ?? ()
#104 0x00000000 in ?? ()
#105 0x00000000 in ?? ()
#106 0x00000000 in ?? ()
#107 0x08139df0 in ?? ()
#108 0x00000000 in ?? ()
#109 0x00000000 in ?? ()
#110 0x00000000 in ?? ()
#111 0x00000000 in ?? ()
#112 0x00000000 in ?? ()
#113 0x00000000 in ?? ()
#114 0x00000000 in ?? ()
#115 0xb77deee0 in vtable for QGArray () from /usr/lib/libqt-mt.so.3
#116 0x00000000 in ?? ()
#117 0xb6af579f in __pthread_alt_unlock () from /lib/libpthread.so.0
#118 0x0804e0fb in ?? ()
#119 0x00000004 in ?? ()
#120 0x0813a72c in ?? ()
#121 0x0813a75b in ?? ()
#122 0x0813a75b in ?? ()
#123 0x0000001a in ?? ()
#124 0x0813ab04 in ?? ()
#125 0x00000001 in ?? ()
#126 0x00000000 in ?? ()
#127 0x00000000 in ?? ()
#128 0x0813ab08 in ?? ()
#129 0x00000000 in ?? ()
#130 0x00000000 in ?? ()
#131 0x00000000 in ?? ()
#132 0x0813ab08 in ?? ()
#133 0x00000000 in ?? ()
#134 0x00000000 in ?? ()
#135 0x0813a76b in ?? ()
#136 0x0000001a in ?? ()
#137 0x0813a75b in ?? ()
#138 0x0813a736 in ?? ()
#139 0x0813a72c in ?? ()
#140 0x00000004 in ?? ()
#141 0x0813a728 in ?? ()
#142 0x00000000 in ?? ()
#143 0x00000000 in ?? ()
#144 0x00000000 in ?? ()
#145 0x00000006 in ?? ()
#146 0x00000408 in ?? ()
#147 0x080513d8 in vtable for QCString ()
#148 0x0805a588 in ?? ()
#149 0x00000000 in ?? ()
#150 0x00000000 in ?? ()
#151 0x080513d8 in vtable for QCString ()
#152 0x0813a160 in ?? ()
#153 0xb7daad2b in ssignal () from /lib/libc.so.6
#154 0x0804e6fb in ?? ()
#155 0x00000004 in ?? ()
#156 0xbffff960 in ?? ()
#157 0xbffff8e4 in ?? ()
#158 0xbffff9d0 in ?? ()
#159 0x00000000 in ?? ()
#160 0xbffff970 in ?? ()
#161 0xbffff8d8 in ?? ()
#162 0xb7f69d13 in operator delete () from /usr/lib/libstdc++.so.5
#163 0x0804f68d in ?? ()
#164 0x00000000 in ?? ()
#165 0xbffffbce in ?? ()
#166 0x00000001 in ?? ()
#167 0x00000000 in ?? ()
#168 0x00000000 in ?? ()
#169 0x00000000 in ?? ()
#170 0x00000000 in ?? ()
#171 0x00000000 in ?? ()
#172 0x00000000 in ?? ()
#173 0x08050457 in _IO_stdin_used ()
#174 0xbffffc74 in ?? ()
#175 0xbffffba8 in ?? ()
#176 0xb7dad2a0 in __cxa_atexit () from /lib/libc.so.6
#177 0xb7d97d76 in __libc_start_main () from /lib/libc.so.6
#178 0x0804b571 in ?? ()

---

### Post by beko on 2005-07-07
I have the same problem & I reported it to kde bugzilla ,it's really annoying problem :roll:

---

### Post by André on 2005-07-07
Was there any reaction on your bugfiling til now??

Could you post a link to your post at bugzilla? Maybe i can also give some further information and help to get rid of this problem...

Greetings
André

P.S.: And yes, it's really annoying ;-)

---

