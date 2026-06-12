---
title: "Help Grub Error 25"
date: 2009-02-06
forum: Dell Ubuntu Support (CLOSED)
---

### Post by jashfa93 on 2009-02-06
I installed a new harddrive today. I partitioned it and installed Ubuntu to it and the installation went fine. When I restarted, I got an error that said "Grub Loading Please wait... Error 25" I went back into the live cd and formated that partition and set the BIOS to boot from my original harddrive with Vista installed on it and it still gives me the Grub Error 25. I want to remove grub completely from my harddrive and be able to boot back into windows

---

### Post by 73ckn797 on 2009-02-06
> **jashfa93 said:**
> I installed a new harddrive today. I partitioned it and installed Ubuntu to it and the installation went fine. When I restarted, I got an error that said "Grub Loading Please wait... Error 25" I went back into the live cd and formated that partition and set the BIOS to boot from my original harddrive with Vista installed on it and it still gives me the Grub Error 25. I want to remove grub completely from my harddrive and be able to boot back into windows


Best that I can do for now is refer you to:
[http://www.gnu.org/software/grub/manual/grub.html#Stage1_002e5-errors](http://www.gnu.org/software/grub/manual/grub.html#Stage1_002e5-errors)

---

### Post by natehall on 2009-02-07
With the live cd try sudo fdisk -l and post the results. Grub is friendly to Windows if you can fix it.

---

### Post by curtlee2002 on 2009-02-07
If you use the alternative ubuntu cd it has a utility to reinstall grub.  If you really don't want to use ubuntu you can boot from the windows install cd, go into the recovery console and type "FIXMBR".  It will replace the master boot record with Windows default one.

I would be more then happy to help you fix grub.

---

### Post by jashfa93 on 2009-02-07
Well i put the vista recovery cd in and did the fixmbr  and that allowed me to go into vista fine.  later i tried to put ubuntu back on and it worked fine. Now when i boot it goes to the grub loader and i have the option to go to vista.   Problem solved

---

