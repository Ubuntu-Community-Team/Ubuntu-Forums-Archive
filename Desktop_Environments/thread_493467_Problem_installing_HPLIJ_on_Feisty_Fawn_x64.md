---
title: "Problem installing HPLIJ on Feisty Fawn x64"
date: 2007-07-05
forum: Desktop Environments
---

### Post by the_nite_owl on 2007-07-05
I am trying to install the hplij drivers for my HP PhotoSmart 3310.
I installed the drivers fine on a laptop with the x86 version but on my x64 server install it just runs forever while trying to install dependencies.
Anyone know if the drivers have a problem with x64?
If I abort the install and try to restart it gives me errors saying apt-get is already running and to shut it down then try again.

Any ideas what the problem or solution might be?

---

### Post by the_nite_owl on 2007-07-06
Well, I managed to fix it myself and figured I would post my results.
The automatic install would bring up a message indicating I should enable some of the software repositories and had a link to go to for instructions on doing it.  Unfortunately the instructions did not seem to be up to date for Ubuntu 7.04 Feisty Fawn and indeed seem not to be entirely applicable.  
So I started the manual installation and while installing dependencies it prompted me to insert the Ubuntu installation CD so I think the problem was that the automatic installation did not recognize the changes in repositories or allow for the prompting for the install CD so that it could continue.

Everything seems to be working fine now that I have completed the manual installation. 
There were errors/warnings related to the scanner but also the instructions on how to enable it.  I have yet to test scanning functions but the software seems to think everything is configured well.

---

