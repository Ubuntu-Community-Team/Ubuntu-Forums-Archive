---
title: "OpenOffice.org crashing"
date: 2005-12-06
forum: Desktop Environments
---

### Post by GrumpyBob on 2005-12-06
I'm using OpenOffice.org 1.9.129 - the version that came with Breezy.  I've been very happy with it, until today.  I'm using it to edit a presentation, and it periodically crashes (sometimes every minute or so).  Writer seems to be OK, these issues seem to afflict Impress.

Would there be any point to uninstalling it and installing the final OOo2 release?  I'm reluctant to because of the hassles I had getting the Bibliography software Bibus to work correctly with it.

Is there a way to find out where the problem lies?  (A log file or similar).

Robert

---

### Post by metoo on 2005-12-06
If you want to try, the final is available under:

deb [http://people.ubuntu.com/~doko/OOo2](http://people.ubuntu.com/~doko/OOo2) ./

or for amd64:
deb [http://people.ubuntu.com/~doko/OOo2-amd64](http://people.ubuntu.com/~doko/OOo2-amd64) ./

Add one of the lines to your /etc/apt/sources.list

---

### Post by trilo on 2005-12-06
Hi GrumpyBob :)

For what it's worth, I have found the current stable version of openoffice 2 much more reliable than 1.9.129. I think it would definitely be worth a try.

You mentioned that you got bibus to work on breezy with openoffice 1.9.129. I have failed to get this working and as you can probably understand, I need a good bibliography/citation manager. Could you please, please, please tell me exactly how you did this? 

Thanks !

---

### Post by jordilin on 2005-12-06
I highly recommend upgrading to 2.0. As metoo points out, put this 
deb [http://people.ubuntu.com/~doko/OOo2](http://people.ubuntu.com/~doko/OOo2) ./ into your sources.list and do apt-get update and then upgrade.

---

