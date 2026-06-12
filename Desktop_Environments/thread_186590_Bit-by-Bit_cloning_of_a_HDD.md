---
title: "Bit-by-Bit cloning of a HDD"
date: 2006-06-02
forum: Desktop Environments
---

### Post by el3ktro on 2006-06-02
Hello, I need your help guys.

I need a bit-by-bit clone of an existing 80GB HD. I want to copy _EVERYTHING_, and I really mean every single bit to a new, identical harddisk. I've found "g4u" for this, a NetBSD-LiveCD which does a bit-by-bit copy of a harddisk to a FTP server, and then you can boot the other computer with the new HD and fetch this image from FTP again. But it doesn't support direct disk-to-disk copies - which would save some time indeed. So my question: Could'nt I do this with the "dd" command? I could put both HDs into one computer, boot the Ubuntu LiveCD, and dd-copy the harddisk. Would dd really copy every single bit? What about this "blocksize" argument for dd? How could this be done? I'm just unsure if dd is really the right tool and if ys, how to exactly run it. Any help would be appreciated!

Tom

---

### Post by uros678 on 2006-06-02
dd has always worked for me... I don't actualy remember setting the blocksize, just the input and output parameters... 

Best regards,
uros

---

### Post by FuturePast on 2006-06-02
dd is the right tool. (I believe dd=disk duplicate).
If the disks are really identical then the command is simple:
dd if=/dev/hda of=/dev/hdc bs=1024k

where hda is the old disk and hdc is the new one.
The block size is 1Mb here, to speed up the copy.

HTH

---

### Post by GrammatonCleric on 2006-06-12
I know this is sort of off the subject but I just want to say the "g4u"
rocks!  So far everything I've tried it on it has worked wonderful (Dell workstations running XP and linux, Dell Servers running linux or Windows, etc)!  

GC

---

