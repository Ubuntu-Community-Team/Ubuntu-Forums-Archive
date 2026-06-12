---
title: "question about modules in e17"
date: 2006-06-19
forum: Desktop Environments
---

### Post by daedalusman on 2006-06-19
Well I just got e17 installed using the easy_e17.sh script and I was playing around with the modules. I was able to enable a couple of them but when I tried to disable them E segfaults. This is based on the configuration dialog which allows you to enable and disable modules with a gui. My question is, can I disable modules in a different way (command line) so that maybe I can workaround the segfaulting? There are really only two modules I tried that caused a segfault, flame and the mount module (can't remember what it's called). The flame module really eats up CPU so for me to want to use e17 I need to disable this module. Besides this though e17 has come a very long way since I last tried it last year sometime under breezy and I can't wait for it to become stable and ready for release. Thanks for any help.

---

### Post by Third Thoughts on 2006-07-15
to disable
```
enlightenment_remote -module-disable modulename
```
to enable
```
enlightenment_remote -module-enable modulename
```

in general you should look into enlightenment_remote. You can do anything from it, though figuring out exactly what options to use can be tough.

~Andrew S.

---

