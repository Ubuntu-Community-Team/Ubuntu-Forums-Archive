---
title: "Sun VirtualBox Shared folder"
date: 2009-06-24
forum: General Help
---

### Post by th1bill on 2009-06-24
I can find the directions to using the shared foder in a windows host but I am trying to run XP on my Ubuntu host and I need to share a folder.

Any help?

---

### Post by idodos on 2009-06-24
1) Setup a shared folder.
2) In windows, go to run and type "cmd"
3) In the command prompt type: **net use x: \\vboxsvr\sharedfolder**

Of course you can change the drive letter **x** to any other letter and you are to input the shared folder name in the **sharedfolder** field. Simple!

---

### Post by th1bill on 2009-06-24
I'm sorry, I misstated, the Host is Ubuntu and the guest is XP.  I cannot find the folder frm either system.

---

### Post by Legace on 2009-06-24
> **th1bill said:**
> I'm sorry, I misstated, the Host is Ubuntu and the guest is XP.  I cannot find the folder frm either system.

Have you installed guest additions in your Windows host?

If so, read this [http://www.giannistsakiris.com/index.php/2007/09/28/virtualbox-access-shared-folders-from-windows-xp-guest-os/](http://www.giannistsakiris.com/index.php/2007/09/28/virtualbox-access-shared-folders-from-windows-xp-guest-os/)

---

### Post by th1bill on 2009-06-24
> **Legace said:**
> Have you installed guest additions in your Windows host?

If so, read this [http://www.giannistsakiris.com/index.php/2007/09/28/virtualbox-access-shared-folders-from-windows-xp-guest-os/](http://www.giannistsakiris.com/index.php/2007/09/28/virtualbox-access-shared-folders-from-windows-xp-guest-os/)

My host is Ubuntu and the guest is WindowsXP.

---

### Post by Legace on 2009-06-24
> **th1bill said:**
> My host is Ubuntu and the guest is WindowsXP.

I meant Windows guest.

---

### Post by th1bill on 2009-06-24
I followed the directions but I do not find the folder there.  Perhaps I am not correct in the path when I create it?  I used "/share"

---

