---
title: "Installation of matlab r2008b - problem with license manager"
date: 2009-06-03
forum: Education &amp; Science
---

### Post by calbuco on 2009-06-03
Hello!

I am installing the matlab r2008b studenet version, so I have already done the pre-installation and I have activated matlab on the MathWorks - side, downloaded the license document etc. But as soon as I get to the main-installation I get the following problem with the License manager: 

B2. Install the FLEXnet Network License Manager
----------------------------------------------

License manager executables are missing . . .
License manager installation skipped . . .

To install the license manager executables try
reinstalling the License Manager.
If you downloaded the products you may need to 
download the matlab.glnx86 file.

Continue? ([y]/n) 

Does this mean that I have to optain the FLEXnet Network License Manager to complete the installation? And if so, how and where can I get it?

I would be happy to receive any help!

Lisa

The support -team of MathWorks just told me you didn't need the FLEXnet for the Student version.
But why, then, is matlab not working after the installation?

---

### Post by perroazul on 2009-06-03
hi,
what I always do is run the installer (as root) and tell the installer to add links of the executables to the bin folder (the installer gives you this option at some point of the installation).
then, once that the installation has finished, I go to the folder that contains the matlab license. with a command line:
cd /usr/matlab2007a/etc/
(in your case this could be different, but the license is always in the 'etc' folder)
open the file with a text editor
sudo gedit license.dat 
erase all the contents of this file and replace them with the license they gave you. 
It always works for me.
good luck with that

---

### Post by wesolek on 2010-09-23
Hi there!

I have the same problem... and unfortunately, I don't even have the "etc" folder after the installation... :-(
It seems like the License Maganer has not been installed at all... I'm a bit lost, I have to admit.

---

