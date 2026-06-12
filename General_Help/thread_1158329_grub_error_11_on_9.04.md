---
title: "grub error 11 on 9.04"
date: 2009-05-13
forum: General Help
---

### Post by AoA Linux on 2009-05-13
I have 9.04, Vista, and OpenSolaris on my computer, and I can boot into them, but can not boot into Ubuntu.  I get the grub error 11.  Unrecognized Device String.  What can I do about this?

Thx

---

### Post by evilbuntu on 2009-05-13
> **AoA Linux said:**
> I have 9.04, Vista, and OpenSolaris on my computer, and I can boot into them, but can not boot into Ubuntu.  I get the grub error 11.  Unrecognized Device String.  What can I do about this?

Thx

did you just upgrade to 9.04 and did this start after the upgrade?

---

### Post by AoA Linux on 2009-05-13
No sir, I updated my grub menu list to include Solaris and now it wont boot into ubuntu.

---

### Post by AoA Linux on 2009-05-14
Bump, I think the problem is that I removed the stuff that goes after Ubuntu 9.04,....... in the grub menu list.  Does anyone have it so I can replace it if that is what caused my error.

---

### Post by Egi_Power on 2009-05-14
Did you edit */boot/grub/menu.lst*?
If yes, how did you do it?
If you used *gedit* for the job, then I think you can still get the original back.
In my experience, when I edit a file in *gedit* and save it, *gedit* automatically creates a backup file of the original in the same folder.
For example I open **myfile** in *gedit*.
I edit it according to my needs.
Save it.
Then gedit creates from **myfile** -> **myfile~**.
If I'm right it's a hidden file.
Have a look.

Egi_Power

---

### Post by AoA Linux on 2009-05-14
I edited it by going to filesystem... boot... grub... menulist.

---

