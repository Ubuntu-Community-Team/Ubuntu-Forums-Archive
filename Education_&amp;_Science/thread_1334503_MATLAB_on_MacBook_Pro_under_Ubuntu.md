---
title: "MATLAB on MacBook Pro under Ubuntu"
date: 2009-11-22
forum: Education &amp; Science
---

### Post by kmrjohnson on 2009-11-22
I just bought a MacBook Pro running OS X 10.6 and have installed Ubuntu 9.10 under Parallels Desktop 5 in order to run MATLAB 2009b efficiently. MATLAB runs too slowly on the MacBook Pro under OS X 10.6, in fact no faster than on my old PowerBook G4.  I am referring here to the speed of a specific piece of highly iterated numerical computation code from my particular project.

My question is:  I'd like to use the MATLAB parallel computing toolbox and related functionalities to further speed up the computations.  Will I be able to do this using Ubuntu via the Parallels Desktop?  Is the computer going to be able to see the two Mac Minis I plan to connect to the main computer?  Or am I better off booting the Mac up from a Linux disk (if this is possible)?  Or some other approach? 

I'd appreciate hearing from someone who has tried to do something similar.

Thanks.

---

### Post by zgornel on 2009-11-23
As a general rule, you should never run intensive computational software in a virtual machine. If you want to use the linux version of matlab, use a dual-boot configuration, otherwise, use the mac version.

---

### Post by XCan on 2009-11-23
I suspect you're reffering specifically to Matlab's built in "parfor" function in the Parallel computing toolbox? If that's the case, then I can tell you that it works just fine on my Jaunty machines. Although, I find the implementation not too good. They seem to have tried to build in some intelligence into the functions, but I've run into several times where the "intelligence" fails, claiming a loop is not independent when it is, amongst other things. Thus, from time to time, I even use the freely availble "multicore" toolbox on Matlab Exchange.

---

### Post by kmrjohnson on 2009-11-23
Thanks to both of you for replying.

I see that some users have figured out how to boot up an Intel Macintosh in Linux using Bootcamp.

However, I don't have the skill (or nerve) to try a complex hack.  Is there some alternative out there that works?

---

