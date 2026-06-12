---
title: "how to open a file with vmd 1.8.7 by double click"
date: 2011-02-19
forum: Education &amp; Science
---

### Post by Claus7 on 2011-02-19
Hello,

I installed the vmd 1.8.7 in an ubu 64 machine following the general guide here:
[http://ubuntuforums.org/showthread.php?t=598518](http://ubuntuforums.org/showthread.php?t=598518)
and here:
[http://ubuntuforums.org/showthread.php?t=1098590](http://ubuntuforums.org/showthread.php?t=1098590)

yet I noticed that I could no longer go to a file, double click it, declare that I want it to open with vmd command and as a result my file to be displayed correctly. Instead a pop up with the display of the molecule was appearing and immediately disappearing from sight.

In order to avoid that I had to go to the file in question and do a right click -> Open with -> Other application... 

and in the new window that appeared to select: use a custom command and type inside the box the string:
> xterm -e /usr/local/bin/vmd

and things worked as normal.

Regards!

---

