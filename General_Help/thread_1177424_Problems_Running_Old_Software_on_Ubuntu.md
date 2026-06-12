---
title: "Problems Running Old Software on Ubuntu"
date: 2009-06-03
forum: General Help
---

### Post by ciclistadan on 2009-06-03
Hello all,

I have been working on this for a while and have decided to seek the help of my ubuntu community.  I am a graduate student trying to update the computers in my lab that are currently used to run microscopy imaging software called 'softworx'.  This software is not open source but is required for reading and processing many of the information that comes from my microscope.  The problem comes in that it was originally packaged as a set of rpm's for RedHat Linux (circa 2001).  It currently works fine on RHEL3 but the slow and outdated computer needs to be replaced and I was hoping to run Ubuntu (I have had other installs of Ubuntu for the last couple years on my other computers and find it very appealing).  I have tried installing these rpm's (after converting to deb's with alien) and the program starts up but has several major problems, most appearing to involve rendering the gui windows.  

when first launching the application I get this error:
```
Symbol `_XmStrings' has different size in shared object, consider
re-linking
Monitor: Symbol `_XmStrings' has different size in shared object,
consider re-linking
```

later when opening the filesystem navigation function:
```
Warning:
    Name: dirname
    Class: XmComboBox
    XmComboBoxSetItem is not yet implemented!
```

and attempting to open another gui window
```
Warning:
    Name: List
    Class: XmList
    Parent refused resize request. Second XtMakeGeometryRequest() failed
```

any help in shedding some light on these errors would be appreciated, thanks.

---

