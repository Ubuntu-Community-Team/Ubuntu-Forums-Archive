---
title: "make error"
date: 2005-11-10
forum: Desktop Environments
---

### Post by Basu on 2005-11-10
I get the following the error when I run make on the polymer theme. I get the same one when I'm try to run baghira, except that the file is baghira.cc. Is it a problem with the compiler? or is something missing. I'm running Ubuntu with the default Kubuntu package.
```

In file included from polymer.cc:1412:
polymer.moc:22: error: no class template named `polymerButton' in `polymer'
polymer.moc:23: error: non-member function `const char* className()' cannot
   have `const' method qualifier
polymer.moc: In function `const char* className()':
polymer.moc:27: error: no class template named `polymerButton' in `polymer'
polymer.moc:28: error: no class template named `polymerButton' in `polymer'
polymer.moc:28: error: non-local variable `
   polymerButton::QConnection::~QConnection()::QMetaObjectCleanUp
   polymerButton::cleanUp_polymer__polymerButton' uses local type `
   polymerButton::QConnection::~QConnection()::QMetaObjectCleanUp'
polymer.moc:28: error: `
   polymerButton::QConnection::~QConnection()::QMetaObjectCleanUp
   polymerButton::cleanUp_polymer__polymerButton' is not a static member of `
   class polymerButton'
polymer.moc:31: error: no class template named `polymerButton' in `polymer'
polymer.moc: In function `QString tr(const char*, const char*)':
polymer.moc:39: error: no class template named `polymerButton' in `polymer'
polymer.moc: In function `QString trUtf8(const char*, const char*)':
polymer.moc:50: error: no class template named `polymerButton' in `polymer'
polymer.moc: In function `QMetaObject* staticMetaObject()':
polymer.moc:52: error: `metaObj' undeclared (first use this function)
polymer.moc:55: error: variable `const
   polymerButton::QConnection::~QConnection()::QUMethod slot_0' has initializer
   but incomplete type
polymer.moc:56: error: variable `const
   polymerButton::QConnection::~QConnection()::QUMethod slot_1' has initializer
   but incomplete type
polymer.moc:57: error: variable `const
   polymerButton::QConnection::~QConnection()::QUMethod slot_2' has initializer
   but incomplete type
polymer.moc:59: error: incomplete type `QMetaData' does not have member `
   Protected'
polymer.moc:60: error: incomplete type `QMetaData' does not have member `
   Protected'
polymer.moc:61: error: incomplete type `QMetaData' does not have member `
   Protected'
polymer.moc:62: error: elements of array `const QMetaData slot_tbl[]' have
   incomplete type
polymer.moc:62: error: uninitialized const `slot_tbl'
polymer.moc:62: error: storage size of `slot_tbl' isn't known
polymer.moc:71: error: incomplete type 'QMetaObject' cannot be used to name a
   scope
polymer.moc:72: error: `cleanUp_polymer__polymerButton' undeclared (first use
   this function)
polymer.moc:62: confused by earlier errors, bailing out
make[3]: *** [polymer.lo] Error 1
make[3]: Leaving directory `/home/basu/Desktop/polymer/polymer/client'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/basu/Desktop/polymer/polymer/client'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/basu/Desktop/polymer/polymer'
make: *** [all] Error 2
basu@Linuxsys:~/Desktop/polymer/polymer$
basu@Linuxsys:~/Desktop/polymer/polymer$                          
```

---

### Post by frodon on 2005-11-10
By the way, you can find a .deb of the polymer theme and install it using these command : ```
wget http://fleixius.com/files/downloads/polymer-0.3.2_0.3.2-1_i386.deb
sudo dpkg -i polymer-0.3.2_0.3.2-1_i386.deb
```For compilation you need the buil-essential package : ```
sudo apt-get install build-essential
```

---

### Post by Basu on 2005-11-10
already have build essentials off the CD. I need a permanent solution to this.

---

### Post by frodon on 2005-11-10
Did you give the whole log output in the first post ?
Because at this point, I don't see why you get errors. 
Does the .deb install works ?

---

### Post by Basu on 2005-11-11
I just posted the part in the make process where the errors start to come out from. It's all fine upto this point. Like I said, I get the exact same problems when I compile baghira. Oh well, my friend got a bunch of Breezy discs, so I think that I'll just get 3.4.3 from there. BTW, I want to install KDE in bits and pieces, ie just the essentials and the few programs that I want. Can someone point me to a list?

---

