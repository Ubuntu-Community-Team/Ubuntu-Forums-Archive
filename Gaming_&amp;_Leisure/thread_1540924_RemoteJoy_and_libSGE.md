---
title: "RemoteJoy and libSGE"
date: 2010-07-28
forum: Gaming &amp; Leisure
---

### Post by TyrantWave on 2010-07-28
I'm trying to get Remotejoy to run, so I can record my PSP screen on linux.

Following this guide:
[http://lgallardo.com/2010/02/15/remotejoy-para-linux-usando-irshell-5/](http://lgallardo.com/2010/02/15/remotejoy-para-linux-usando-irshell-5/)

I have IRShell on my PSP, I can run usbhostfs18, but when I go to run rj_resize_mod -c -d, I just get this error:

```
./rj_resize_mod: error while loading shared libraries: libSGE.so.0: cannot open shared object file: No such file or directory
```

I have installed libsdl-sge, as recommended, but I still get the error =/.

On Ubuntu 10.04 x86-64.

Any reason the library would be missing?

---

### Post by TyrantWave on 2010-07-29
Bump~

---

### Post by Perfect Storm on 2010-07-29
If the app you want to run is a 32-bit, you need to install the 32-bit version of the lib you're reffering to.
You can check out getlibs for that purpose.

---

