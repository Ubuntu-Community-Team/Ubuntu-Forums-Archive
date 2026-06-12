---
title: "Annoying issue with KMix not starting =/"
date: 2009-06-11
forum: General Help
---

### Post by Martin Wolflux on 2009-06-11
Short version of the problem: I need to configure KMix, but Kubuntu (8.10) refuses to start it. I have the latest installment of KDE.

When I try to force it running, I get this error:
```
Error: "/var/tmp/kdecache-wolflux" is owned by uid 1000 instead of uid 0.
Error: "/tmp/kde-wolflux" is owned by uid 1000 instead of uid 0.
kmix(4554) KToolInvocation::klauncher: klauncher not running... launching kdeinit
Error: "/tmp/kde-wolflux" is owned by uid 1000 instead of uid 0.
Error: "/tmp/ksocket-wolflux" is owned by uid 1000 instead of uid 0.
kdeinit4: Shutting down running client.
kdeinit4: preparing to launch /usr/lib/kde4/libexec/klauncher
Error: "/tmp/ksocket-wolflux" is owned by uid 1000 instead of uid 0.
Error: "/tmp/kde-wolflux" is owned by uid 1000 instead of uid 0.
kdeinit4: preparing to launch /usr/bin/kded4
Error: "/var/tmp/kdecache-wolflux" is owned by uid 1000 instead of uid 0.
Error: "/tmp/kde-wolflux" is owned by uid 1000 instead of uid 0.
kdeinit4: preparing to launch /usr/bin/kbuildsycoca4
kbuildsycoca4 running...
Error: "/var/tmp/kdecache-wolflux" is owned by uid 1000 instead of uid 0.
kdeinit4: preparing to launch /usr/bin/kbuildsycoca4
kbuildsycoca4 running...
Error: "/var/tmp/kdecache-wolflux" is owned by uid 1000 instead of uid 0.
Error: "/var/tmp/kdecache-wolflux" is owned by uid 1000 instead of uid 0.
kdeinit4: preparing to launch /usr/lib/kde4/libexec/kconf_update
kded(4575) KDEDModule::setModuleName: registerObject() successful for  "kdedglobalaccel"
kmix(4554) Mixer::setGlobalMaster: Mixer::setGlobalMaster() card= "ALSA::ATI_IXP:1"  control= "PCM:0"
kmix(4554) Mixer::openIfValid: Mixer::open() detected master:  "PCM:0"
kmix(4554) Mixer::openIfValid: Mixer::open() detected master:  "Mic:0"
```

Don't suppose anyone know any fixes?


The reason I need to fix it is because my microphone records my voice two octaves lower than what I am speaking xD


*edit2* I fixed the issue myself, but I dunno how xD

Sorry for bothering!

---

