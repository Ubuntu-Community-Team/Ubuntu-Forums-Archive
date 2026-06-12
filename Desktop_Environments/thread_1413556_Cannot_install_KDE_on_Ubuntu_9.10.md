---
title: "Cannot install KDE on Ubuntu 9.10"
date: 2010-02-22
forum: Desktop Environments
---

### Post by tonsil on 2010-02-22
I thought I'd try KDE on my Ubuntu 9.10 so I followed the instructions on [http://www.psychocats.net/ubuntu/kde](http://www.psychocats.net/ubuntu/kde). I marked kubuntu desktop for installation on synaptic package manager, and when I clicked apply it started to install files, but after installing some 10 files it gave me the following error:

E: Method http has died unexpectedly!
E: Sub-process http received a segmentation fault.

I re-clicked apply and it seemed to continue from where it left off, only to give me this error:

E: Method http has died unexpectedly!
E: Sub-process http received signal 4.

Well, I clicked apply again, it went for another number of files, but sadly gave me the same error.

The installation has not finished yet. But I doubt KDE will work. Is there anything I can do?

Thanks!

---

### Post by koleoptero on 2010-02-22
That looks like a network problem. If your connection does not have any problems you can select a different mirror from the System > Administration > Software Sources tool. Select a mirror from your country there and make sure you use the http protocol.

---

### Post by tonsil on 2010-02-23
I switched to main server, and although it gave me another segmentation error it installed KDE nonetheless, and I'm writing this message from KDE environment :) Thank you very much!

---

