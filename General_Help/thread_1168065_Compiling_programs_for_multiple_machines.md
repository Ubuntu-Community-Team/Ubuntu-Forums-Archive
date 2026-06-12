---
title: "Compiling programs for multiple machines"
date: 2009-05-23
forum: General Help
---

### Post by speed32219 on 2009-05-23
If I downloaded a source program and compile/run as follows:

./configure
make -j2
sudo make install

Can I copy that directory (FTP) to another machine and what?

1. go into directory and run sudo make install.

Or do I need to run all three commands again?  

This is assuming that all the networked machines have been updates with all the programs and dependencies.  Just looking for an easy way to accomplish this over and over again.

---

### Post by albinootje on 2009-05-23
> **speed32219 said:**
> 
Can I copy that directory (FTP) to another machine and what?

1. go into directory and run sudo make install.

Or do I need to run all three commands again?  

No, iirc that should work with just "sudo make install".

(The configure basically checks for your platform (and 32 or 64 bit), and for needed libraries and header files, and "make" compiles it.)

---

### Post by mcduck on 2009-05-23
First install the "checkinstall"-package. Then, when compiling, replace the "sudo make install" with "sudo checkinstall". Checkinstall will create a .deb package from the compiled program.

Actually this is recommended for any apps you compile, even if you only use them on that computer, as it makes removing self-compiled applications a lot easier.

(just remember that checkinstall won't add information about possible dependencies to packages so .deb packages created with it shouldn't be used for public distribution of programs.)

---

