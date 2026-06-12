---
title: "[SOLVED] Virtual Box 2.1.0 issue with jaunty"
date: 2008-12-30
forum: Development CD/DVD Image Testing
---

### Post by lprofil on 2008-12-30
Hello,

i have this odd error when i try to install jaunty as a virtual machine in VirtualBox version 2.1.0 under intrepid. 
Some seconds after loading the initrd the screen show up with the message:

"**can't get a pty: No such file or directory**"

and srolls up the screen to return after a second again.

This issue accours with the *alternate* and *desktop *version.


The *server-version* installs but than complains with the message:

"**Unable to boot - please use a kernel appropriate for your CPU.**"

Every hint or help is appreciated. Thank you very much!

/lprofil

---

### Post by cszikszoy on 2008-12-30
[LEFT]It's pretty rare that the early alpha releases actually work inside of a VM.  Best to install on actual hardware to test the alphas.  Either that or wait for alpha 5-6.  Those usually work pretty well as a VM.
[/LEFT]

---

### Post by lprofil on 2008-12-31
Hey cszikszoy,

thanks for your reply.

Today i tried the new daily build where the problem is fixed.
Thanks for the guy who did it!


/lprofil

---

