---
title: "Azureus startup hath an infinate loop"
date: 2005-08-03
forum: Desktop Environments
---

### Post by electrosoccertux on 2005-08-03
DEBUG::Wed Aug 03 00:44:53 EDT 2005::com.aelitis.azureus.core.networkmanager.VirtualServerChannelSelector::accept_loop()::-1:
    VirtualServerChannelSelector::access$100(com.aelitis.azureus.core.networkmanager.VirtualServerChannelSelector)::-1,VirtualServerChannelSelector$1::runSupport()::-1,AEThread::run()::-1,::GC_start_routine::-1,::__clone::-1
java.lang.NullPointerException
   at com.aelitis.azureus.core.networkmanager.VirtualServerChannelSelector.accept_loop() (Unknown Source)
   at com.aelitis.azureus.core.networkmanager.VirtualServerChannelSelector.access$100(com.aelitis.azureus.core.networkmanager.VirtualServerChannelSelector) (Unknown Source)
   at com.aelitis.azureus.core.networkmanager.VirtualServerChannelSelector$1.runSupport() (Unknown Source)
   at org.gudy.azureus2.core3.util.AEThread.run() (Unknown Source)
   at .GC_start_routine (/usr/lib/libgcj.so.6.0.0)
   at .__clone (/lib/tls/i686/cmov/libc-2.3.2.so)
DEBUG::Wed Aug 03 00:44:53 EDT 2005::com.aelitis.azureus.core.networkmanager.VirtualServerChannelSelector::accept_loop()::-1:
    VirtualServerChannelSelector::access$100(com.aelitis.azureus.core.networkmanager.VirtualServerChannelSelector)::-1,VirtualServerChannelSelector$1::runSupport()::-1,AEThread::run()::-1,::GC_start_routine::-1,::__clone::-1
java.lang.NullPointerException
   at com.aelitis.azureus.core.networkmanager.VirtualServerChannelSelector.accept_loop() (Unknown Source)
   at com.aelitis.azureus.core.networkmanager.VirtualServerChannelSelector.access$100(com.aelitis.azureus.core.networkmanager.VirtualServerChannelSelector) (Unknown Source)
   at com.aelitis.azureus.core.networkmanager.VirtualServerChannelSelector$1.runSupport() (Unknown Source)
   at org.gudy.azureus2.core3.util.AEThread.run() (Unknown Source)
   at .GC_start_routine (/usr/lib/libgcj.so.6.0.0)
   at .__clone (/lib/tls/i686/cmov/libc-2.3.2.so)




and so on and so on. Any help? I believe I broke it during the first install (of azureus). I think I had was looking at the back of my system and bumped the power cord. Oh well. Whats up with this loop?

---

### Post by ^NoX on 2005-08-03
after a power failure, azureus performs a check on the files you download. if we are talking about 10GB - it can take a lot of time. maybe 5-10 minutes.
during this time, your cpu goes 100% and it looks like an infinity loop.
anyways, my suggestion is to leave it to work and go have some coffee or something  :razz: 

on the other hand, maybe im wrong and it is an inifinty loop - but i don`t think so. look in azureus`s bugzilla for any case.

---

### Post by electrosoccertux on 2005-08-03
[QUOTE=^NoX]after a power failure, azureus performs a check on the files you download. if we are talking about 10GB - it can take a lot of time. maybe 5-10 minutes.
during this time, your cpu goes 100% and it looks like an infinity loop.
anyways, my suggestion is to leave it to work and go have some coffee or something  :razz: 

on the other hand, maybe im wrong and it is an inifinty loop - but i don`t think so. look in azureus`s bugzilla for any case.[/QUOTE]

I haven't downloaded anything from azureus yet...haven't been able to get it to start. I hope its what you say. I'll leave it and go to work.

Doing apt-get remove and then installing it again didn't work last night.

---

