---
title: "MBR recovery help"
date: 2009-06-21
forum: General Help
---

### Post by amotorkat on 2009-06-21
Long story short, I messed something up pretty bad.

I have a vista box and was setting up ubunto on a usb stick.  GRUB ended up on my c:.  I cant boot into vista any longer.  removed c: from laptop, and now its a usb drive on my other vista laptop.  Windows explorer does not see it, it sees it in disk management though, but has no drive letter but it says its a healty partition.  Vista recovery wont do anything because it cant see that drive.  That partition is not viewable in any linux distro that ive tried either, i tried to view it in slax, fadora and ubuntu.  I dont think ill be able to repair the MBR at this point, but desperatly need o recover the data.  I know, I should have backed it up first, but I didnt :(  Ive tried every utility I can, the best so far was Partition Find and Mount, which found the small 253 MB part. for ubuntu, but cant find and let me mount the one for windows.  Any ideas would be great.

---

### Post by hyperdude111 on 2009-06-21
I made a similar mistake when I first started with linux. 
Try this link.

[http://www.lancelhoff.com/how-to-fix-vista-mbr-repair-broken-vista/](http://www.lancelhoff.com/how-to-fix-vista-mbr-repair-broken-vista/)


If that failed read more info here.
[http://ubuntuforums.org/showthread.php?t=596507](http://ubuntuforums.org/showthread.php?t=596507)
[http://forums.techarena.in/vista-help/691963.htm](http://forums.techarena.in/vista-help/691963.htm)
[http://ubuntuforums.org/showthread.php?t=595467](http://ubuntuforums.org/showthread.php?t=595467)
[http://ubuntuforums.org/showthread.php?t=595015](http://ubuntuforums.org/showthread.php?t=595015)
[http://ubuntuforums.org/showthread.php?t=594223](http://ubuntuforums.org/showthread.php?t=594223)
[http://ubuntuforums.org/showthread.php?t=594164](http://ubuntuforums.org/showthread.php?t=594164)

This is the best link IMO

[http://www.lancelhoff.com/how-to-fix-vista-mbr-repair-broken-vista/](http://www.lancelhoff.com/how-to-fix-vista-mbr-repair-broken-vista/)

---

### Post by amotorkat on 2009-06-21
Thanks, I will take a look at those links tomorrow and see what I can come up with.  I just ran Easeus Data Recovery Demo, and that sees my files so I have a little bit of hope that something will work here.  :)

---

### Post by egalvan on 2009-06-21
From the description of your problem, it seems Vista's MBR got replaced by Ubuntu's MBR.
The rest of your Vista partition(s) should still be in their original state. Ubuntu installations don't touch these.
Unless you chose the "use the whole disk for the Ubuntu install" option.

So, before you try radical surgery,
take a look at these links...

From MS themselves...
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

if you don't have a real Vista Install CD/DVD, try this...
[http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1)

Another view-point...
[http://www.vistaheads.com/forums/microsoft-public-windows-vista-general/26168-fix-mbr-vista.html](http://www.vistaheads.com/forums/microsoft-public-windows-vista-general/26168-fix-mbr-vista.html)

There are lots more out there.

EGalvan

---

