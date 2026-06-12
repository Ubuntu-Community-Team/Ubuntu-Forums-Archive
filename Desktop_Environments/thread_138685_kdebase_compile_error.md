---
title: "kdebase compile error"
date: 2006-03-02
forum: Desktop Environments
---

### Post by BrianB on 2006-03-02
When I compiling KDE 3.5 (using konstruct) I get the following error :
```
Making all in fonts
make[5]: Entering directory `/home/brian/KDE/konstruct/kde/kdebase/work/kdebase-3.5.0/konsole/fonts'
bdftopcf -o console8x16.pcf ./console8x16.bdf
make[5]: bdftopcf: Command not found
make[5]: *** [console8x16.pcf.gz] Error 127
make[5]: Leaving directory `/home/brian/KDE/konstruct/kde/kdebase/work/kdebase-3.5.0/konsole/fonts'
make[4]: *** [all-recursive] Error 1
make[4]: Leaving directory `/home/brian/KDE/konstruct/kde/kdebase/work/kdebase-3.5.0/konsole'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/brian/KDE/konstruct/kde/kdebase/work/kdebase-3.5.0'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/brian/KDE/konstruct/kde/kdebase/work/kdebase-3.5.0'
make[1]: *** [build-work/kdebase-3.5.0/Makefile] Error 2
make[1]: Leaving directory `/home/brian/KDE/konstruct/kde/kdebase'
make: *** [dep-../../kde/kdebase] Error 2

``` any help? :-k

---

### Post by metwo on 2006-03-02
Do you have bdftopcf installed?

---

### Post by BrianB on 2006-03-02
Thanks, installed bdftopcf and everything seems to be ok.

---

### Post by BrianB on 2006-03-02
I'm now having another problem, my memory usage, swap and RAM goes to near 100% and nothing happens after this : 
```
then mv -f ".deps/libkmailprivate_la.all_cpp.Tpo" ".deps/libkmailprivate_la.all_cpp.Plo"; else rm -f ".deps/libkmailprivate_la.all_cpp.Tpo"; exit 1; fi
configuredialog.cpp: In constructor 'ConfigureDialog::ConfigureDialog(QWidget*, const char*, bool)':
configuredialog.cpp:216: warning: '__base_ctor ' is deprecated (declared at /usr/local/kde3.5/include/kcmultidialog.h:104)
index.cpp: At global scope:
index.cpp:484: warning: unused parameter 'folder'
index.cpp:495: warning: unused parameter 'folder'
kmfoldertree.cpp: In member function 'virtual void KMFolderTree::contentsDropEvent(QDropEvent*)':
kmfoldertree.cpp:1379: warning: 'keyboardModifiers' is deprecated (declared at /usr/local/kde3.5/include/kapplication.h:1069)
``` 
?????

---

### Post by metwo on 2006-03-02
Do you know what's using the cpu/ram? It might just be compiling a really big file

---

### Post by BrianB on 2006-03-02
It does seem to be this that's using all my ram, and I do only have 256 + 300 swap but I always had a decent amount of ram available throughout the rest of the compile.

---

### Post by metwo on 2006-03-02
Maybe its worth making a temporary swapfile for the duration of the compile?

[http://www.netadmintools.com/art1.html]("http://www.netadmintools.com/art1.html")

---

### Post by BrianB on 2006-03-03
left it overnight and it still the same, nothing has happened since. Maybe it's some bad code?

---

