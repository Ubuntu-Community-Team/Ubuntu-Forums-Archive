---
title: "RealVNC problem"
date: 2006-02-01
forum: Desktop Environments
---

### Post by stardotstar on 2006-02-01
I have been using the VNC client within Terminal Services Client but found it dropped out a lot.  Connecting to an XP box.

I decided to look at the newest 4.1.1 version of RealVNC and downloaded and installed it to /usr/local/bin as suggested.

It did not run because it complained it needed:

```

wparker@geko:/usr/local/bin$ ./vncviewer
./vncviewer: error while loading shared libraries: libstdc++-libc6.2-2.so.3: cannot open shared object file: No such file or directory

``` 
So I looked in the package manager and found a packaged version of 4.0-8 and installed that.  It worked OK for a while but seemed to still quit - so I switched back to Terminal Services Client and got the same error as with 4.1.1...

I assume it is calling the client.

What do I need to do - is it a path thing or a lib that I need that may conflict with my existing C libs???

TIA

Will

---

