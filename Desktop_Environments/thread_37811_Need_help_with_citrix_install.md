---
title: "Need help with citrix install"
date: 2005-05-28
forum: Desktop Environments
---

### Post by shyweij on 2005-05-28
Hello All,

[B]I have successfully resolved the issue by myself installing openmotif which includes the needed libraries.  Hope this helps others in my former situation.

-notsocluess1[/B]

-----------------------------
I finally took the jump and decided to install linux on my old Dell Laptop. Now When I tried to install Citrix 9 ICA client and have errors running the wfcmgr .  I get this error :  

 error while loading shared libraries: libXm.so.3: cannot open shared object file: No such file or directory

I've already installed prior libraries suggested in the forums, ( libxaw6, mozilla ). 
If anyone is wiling to try installing the client and help me out that would be great. 
If not, it would appear to be the end of my Ubuntu adventures. Thanks

-clueless1
running 5.04.

---

### Post by marguz on 2005-06-02
Hello,
I too got this error. I too aplied the fixes I found here (install libxaw6) but that did not work, as I was still getting the error...
" error while loading shared libraries: libXm.so.3: cannot open shared object file: No such file or directory"

Do this "apt-get install libmotif3"

Have FUN!

---

### Post by draxula on 2005-06-04
Hi,

In which repository did you find libmotif3?

Stephan

---

### Post by thepeel on 2005-06-16
install libmotif3 from multiverse

---

