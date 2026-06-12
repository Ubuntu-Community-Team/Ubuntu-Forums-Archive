---
title: "psp authority"
date: 2006-01-04
forum: Gaming &amp; Leisure
---

### Post by Akya on 2006-01-04
for some reason when i try to put something on my psp it shows the file on my computer then i disconnect my psp and it the file goes away can any one help me?

---

### Post by Quirky on 2006-01-08
You have to wait for the copy to finish. This is a new "feature" of pmount that changed from hoary to breezy. 

Previously, the "Copying" dialog box with the little bar telling you how much time is left was correct, it showed how much time was really left. Now it just shows some made up time-left figure that is far too quick. The files don't actually finish copying until some unknown point in the future. This is due to the asynchronous nature of the copying.

The best way to make sure you finish copying the files is to type "sync" in a command line and wait until it finishes before unplugging the PSP (or other USB device)

[http://bugzilla.ubuntu.com/show_bug.cgi?id=13169](http://bugzilla.ubuntu.com/show_bug.cgi?id=13169)

---

