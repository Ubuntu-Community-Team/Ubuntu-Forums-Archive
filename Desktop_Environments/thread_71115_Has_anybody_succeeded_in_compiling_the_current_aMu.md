---
title: "Has anybody succeeded in compiling the current aMule cvs?"
date: 2005-10-02
forum: Desktop Environments
---

### Post by scorpio2002 on 2005-10-02
Hi there! I'm trying to compile the current amule cvs cause I'd like to use kad, but I cant. Has anybody compiled it successfully? does kad work?

---

### Post by cutOff on 2005-10-02
what's the error you've got?

---

### Post by scorpio2002 on 2005-10-02
When I make it, at the end I get this:

```
ow::FindItem(long int, long int)':
extern/listctrl.242.cpp:4487: warning: comparison between signed and unsigned integer expressions
extern/listctrl.242.cpp: In member function `virtual wxListItemAttr* MuleExtern::wxGenericListCtrl::OnGetItemAttr(long int) const':
extern/listctrl.242.cpp:5465: warning: unused parameter `long int item'
make[4]: *** [amule-listctrl.o] Error 1
make[4]: Leaving directory `/home/skorpio/Desktop/amule-cvs/src'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/skorpio/Desktop/amule-cvs/src'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/skorpio/Desktop/amule-cvs/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/skorpio/Desktop/amule-cvs'
make: *** [all] Error 2
```

what is it?

---

### Post by cutOff on 2005-10-02
It seems to be related with wxGtk or wxWidgets. Look at here

[http://forum.amule.org/thread.php?threadid=5139&sid=896b516cc0d2a6cf02ccf0239a2a65ef&hilight=warning+unused+parameter+%60long+int+item](http://forum.amule.org/thread.php?threadid=5139&sid=896b516cc0d2a6cf02ccf0239a2a65ef&hilight=warning+unused+parameter+%60long+int+item)

---

### Post by scorpio2002 on 2005-10-02
Thank you, but unfortunatelly it did't work :|

---

### Post by billdd on 2006-04-06
I haven't been able to and I've spent hours trying.  I installed mine using Automatix.  It didn't work.  So then I came here to the forums and tried a couple of times.  They didn't work either.  The software installed fine but I haven't been able to connect yet.  Always says Kad is firewalled even when I didn't have one.  Tried installing Firestarter and adding rules to enable the ports that one Ubuntu user suggested.  That didn't work either.  I'm using FrostWire now and hate it.  Wish someone would tell me what I'm doing wrong with aMule.:confused:

---

