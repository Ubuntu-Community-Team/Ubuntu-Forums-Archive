---
title: "Hoary+Diablo2+Cedega 4.2.1=Lockups on install.."
date: 2005-02-14
forum: Gaming &amp; Leisure
---

### Post by leech on 2005-02-14
This is just killing me, my brother was talking about playing Diablo 2 again, so I decided what the heck, paid the $15 for Cedega, and tried to install Diablo 2.... well, after trying multiple kernels (from 2.6.8-2.6.10) I think I've finally given up.  It keeps locking up on me.  I finally got the install to run, but then when switching the Cinematics CD back to the Install CD my computer would lock up.  I tried both of my CD-ROM drives and everything.  

Any ideas?

Leech

---

### Post by piedamaro on 2005-02-14
[QUOTE=leech]This is just killing me, my brother was talking about playing Diablo 2 again, so I decided what the heck, paid the $15 for Cedega, and tried to install Diablo 2.... well, after trying multiple kernels (from 2.6.8-2.6.10) I think I've finally given up.  It keeps locking up on me.  I finally got the install to run, but then when switching the Cinematics CD back to the Install CD my computer would lock up.  I tried both of my CD-ROM drives and everything.  

Any ideas?

Leech[/QUOTE]
 No, but I have LOD working perfectly, and I didn't buy cedega :)
Maybe you want to take a look here:[http://www.frankscorner.org/](http://www.frankscorner.org/)

---

### Post by leech on 2005-02-14
Thanks, I'll give that one a try.  I'm tempted to try a few different games to see if I have any luck with Cedega.  It's odd that it always does it on the same CD though....  I wonder if it'd work better if I just made ISOs, mounted them all, then installed...

It locks whether I use the right-click, eject in Nautilus, or if I hit the Eject button on the CD-rom drive itself....

Leech

---

### Post by leech on 2005-02-14
I DID try wine (version 20050211-1 from wine.sourceforge.net) and all it said was "Please insert the Install CD"  Then I'd put retry again and again, finally hit cancel and it said it couldn't find some file.

Leech

---

### Post by piedamaro on 2005-02-14
I've used the  original diablo2 cds + expansions right here on ubuntu, and I've had no issues umounting them.
I remember I had to set a couple of kernel options to make cedega happy, like this:
in /etc/sysctl.conf:
        vm.legacy_va_layout = 1
I've read that on the cedega FAQs, you should find more infos there.

Also to make the audio work if you use software mixing, I had to use winealsa.drv and disable mmap in ~/.transgaming/config

Maybe you could try to copy your diablo directory from windows, then follow the instructions on frankscorner.

---

