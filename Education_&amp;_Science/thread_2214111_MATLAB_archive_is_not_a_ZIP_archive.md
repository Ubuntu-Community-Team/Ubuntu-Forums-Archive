---
title: "MATLAB: archive is not a ZIP archive"
date: 2014-03-30
forum: Education &amp; Science
---

### Post by ayez20 on 2014-03-30
Hi guys,

I must say first of all that i'm a beginner and I tried widely to find the solution of the issue on the net... no way.

 I just installed GNOME Ubuntu 13.10 64bit and I'm trying to install MATLAB R2013a version, and here the problems start! ](*,)
First, I encountered the error described in this thread ([http://ubuntuforums.org/newthread.php?do=newthread&f=169](http://ubuntuforums.org/newthread.php?do=newthread&f=169)) and, I guess, I solved it by suggesting Toby
 > [COLOR=#000000]When the files are zipped, symbolic links are turned into text files. To solve this issue you have to re-create the link using the following commands:[/COLOR]

[COLOR=#000000]cd bin/glnxa64[/COLOR]
[COLOR=#000000]rm libstdc++.so.6 && ln -s libstdc++.so.6.0.10 libstdc++.so.6[/COLOR]

[COLOR=#000000]After that the installer should work.[/COLOR]

[COLOR=#000000]If you have problems with permissons when accessing the glnxa64 folder (like I had) you have to do a "chmod 755 bin/glnxa64".[/COLOR]

[COLOR=#000000]Regards[/COLOR]
[COLOR=#000000]Tobi[/COLOR]

Than the installation started, but before ending Matlab returned the error that I posted in the attachment.
Obviously when I retry installing sl3d_glnxa64 pressing "Yes", nothing happends...

I hope someone can help me soon, please.
Thanks in advance. :-)

---

