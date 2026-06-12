---
title: "How to sudo from a running process"
date: 2007-08-12
forum: Desktop Environments
---

### Post by kentsin on 2007-08-12
For example,

when browsing the folders, we try to do some operation like delete, which may require sudo, how can I do that? 

Even worst, when in the middle of running an application, when sudo is required, can we do sudo without restart the application 

For example, making backup, after running to the end, an unexpected file permission occur, how can I sudo

Do you guys think Ubuntu need a redesign?

---

### Post by aysiu on 2007-08-12
Look into Nautilus scripts.

Or launch the application as *gksudo* or *sudo* if you know you need to make a root change.

---

### Post by kentsin on 2007-08-17
People working with ubuntu is much knowledgeable than people working with OSX.

---

### Post by aysiu on 2007-08-17
> **kentsin said:**
> People working with ubuntu is much knowledgeable than people working with OSX.
I don't see how your extra comment is relevant to your original proposal that Ubuntu needs a redesign. In any case, both Mac OS X and Ubuntu use *sudo*.

---

### Post by fragility14 on 2007-08-17
I havnt found a way to do it besides

sudo konqueror /folder/location

and then doing what you need to do.


edit: I should mention, using Kubuntu it is only konqueror in my instance ;)

---

### Post by aysiu on 2007-08-17
> **fragility14 said:**
> I havnt found a way to do it besides

sudo konqueror /folder/location

and then doing what you need to do.


edit: I should mention, using Kubuntu it is only konqueror in my instance ;)
You mean ```
kdesu konqueror /folder/location
``` ? Then, yes.

But in Kubuntu, there should be a right-click *Edit as Root* option in Konqueror.

---

