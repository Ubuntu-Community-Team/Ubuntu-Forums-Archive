---
title: "TOTALLY remove linux + dual booting.. remove all traces"
date: 2006-02-21
forum: Desktop Environments
---

### Post by lbut on 2006-02-21
Hi,

I'd like to totally remove Linux from this present computer, because I'm going to buy a seperate computer and have linux installed on that. How can I totally delete linux and anything related to it including the dual booting thing, without removing the windows partition and then reconvert that partition to NTFS? 

Thank-you.

---

### Post by Brynster on 2006-02-21
put your original windows CD into the drive and set the bios to boot from CDrom.

Got into recovery console (follow the windows prompts) and type 

fixmbr


This will restore the master boot record. which will allow you to boot into windows directly without GRUB. once your ther you can format the partition/drive that Ubuntu was on using windows. Thsi will completely remove al Ubuntu traces.

---

### Post by az on 2006-02-21
After you remove grub, you can also delete the ubuntu partition, creating free space, and then extend the ntfs partition to its original size, if you shrunk it to install linux.  That would remove all traces of your linux install...

---

