---
title: "Cannot see files on my external Hard Drive (not hidden)"
date: 2008-12-09
forum: General Help
---

### Post by gsirit on 2008-12-09
I'm a newbie in ubuntu...

I can't see files on my USB external hard drive (Western Digital), when I enter the disk it says 0 files, but 6.9GB free (out of 320GB). It doesn't show the files even pressing control+h. I try entering "ls" command on the terminal but it shows this error: "ls: reading directory .: Input/output error".

I know the files are still on the disk, because I still can access to my music (thru Rhythmbox music player library) and my pics and videos thru links I put in Nautilus's places before.

I connected the HD to a Windows PC and a Macbook Pro Laptop but with same results.

Please I really appreciate any help! Thank you!
PS: The last thing I did before this happen, was installing MediaTomb.

---

### Post by mikewhatever on 2008-12-09
Post the output of <df -h> while your disk is connected, also post the output of <ls -l /media/disk>

---

### Post by gsirit on 2008-12-09
Phew! nevermind, I ran NTFStools and fix the hard drive...

---

