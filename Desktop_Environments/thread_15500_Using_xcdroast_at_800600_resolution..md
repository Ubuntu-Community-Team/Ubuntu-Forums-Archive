---
title: "Using xcdroast at 800*600 resolution."
date: 2005-02-15
forum: Desktop Environments
---

### Post by Lachlan on 2005-02-15
I have just downloaded and installed Xcdroast,but when I try to run it from a root terminal I get this error : You need at least a screen resolution of 1024*768 to run xcdroast. Tried xcdroast --display 800*600 without success.
I have used xcdroast at 800*600 in many other distro's without a problem,why does Ubuntu tell me that I need to run it at the higher resolution and how can I correct it.

Lachlan

---

### Post by evangelion on 2005-02-15
Try starting xcdroast with the -n switch
[quote=man xcdroast]
       -n     Disables the cdrtools version check  and  allows  X-CD-Roast  to
              start  when  even wrong versions of cdrecord, mkisofs, readcd or
              cdda2wav are installed. Use at own risk! [b]This also overrides the
              forced  exit  when you don't meet the 800x600 minimal resolution
              requirement.[/b]
[/quote]

---

### Post by Lachlan on 2005-02-15
Thanks evangelion, that did the trick but xcdroast does not recognise my cd-rom or writer,one step forward,one step back.I will have a look at previous postings to try to sort it out.

Lachlan

---

