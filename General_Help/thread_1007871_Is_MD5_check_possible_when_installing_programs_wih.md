---
title: "Is MD5 check possible when installing programs wih synaptic"
date: 2008-12-10
forum: General Help
---

### Post by ekloc on 2008-12-10
How can I check integrity of downloaded packages when installing with synaptic package manager?  Is there a way to do md5 check if it is available?   Is it done automatically?

Also, is there a way to control where new packages are installed when using synaptic?  I wanted to install few development tools and I would love to keep it all in one location. 

Thank you in advance for your responses.

---

### Post by teddks on 2008-12-10
I believe all downloaded packages are checked against PGP signatures, which will provide much more authority than MD5 hashes. I could be wrong, though.

---

### Post by ekloc on 2008-12-11
Thank you teddks.  

How about the control of the location where new packages are installed.  Can it be changed when using synaptic or any other package manager?

---

### Post by teddks on 2008-12-11
I don't really understand what you mean by "keep them all in one location", or if I do, I don't really see why you would want to do that. I don't know if that's possible with synaptic.

---

### Post by Locke_99GS on 2008-12-11
debs have placement information within the package. 

It'd probably be easier to install from source to any odd location you want.

Though, I don't see any reason for not wanting them in their proper (FHS) locations.

---

### Post by ekloc on 2008-12-13
In Windows I keeps all my development tools and workspaces in c:\dev folder and under that folder I have a structure that I have been using for ages.  I would love to fully switch to Linux and I found it odd that each distribution has different locations for the same applications which although manageable is annoying.  I was hoping that it would be possible to easily control where new packages are installed.  

But it's not a big deal.  Each operating system has it's advantages and disadvantages and Ubuntu is no exception.  But it still rocks - thank you guys for your answers.

---

### Post by snova on 2008-12-13
> **ekloc said:**
> How can I check integrity of downloaded packages when installing with synaptic package manager?  Is there a way to do md5 check if it is available?   Is it done automatically?

A file is included with the metadata as part of each package containing the md5sums of each included file. So yes, it's automatic.

> How about the control of the location where new packages are installed. Can it be changed when using synaptic or any other package manager?

No.

---

