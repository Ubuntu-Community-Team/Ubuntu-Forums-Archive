---
title: "Burg not working anymore on 10.04"
date: 2010-07-24
forum: Desktop Environments
---

### Post by maxxam05 on 2010-07-24
I installed Burg and it worked for some time. I installed some apps that I can't remember anymore and closed my comp. I restarted my computer today and Burg does not work anymore, Grub just start like before. I tried to reinstalled Burg and it changed nothing. When I check Burg-emu it shows me the right thing, like if Burg was working. Did it happened to somebody else? Thanks

---

### Post by Halzacar on 2010-07-24
The exact same thing happened to me today, except i have not recently downloaded any programs. All of my symptoms are the same though.

---

### Post by Halzacar on 2010-07-24
Okay. I figured it out. It was because of a recent GRUB update apparently. I just reinstalled burg to my boot drive.  sudo burg-install "(hd0)"  And then I ran the update:  sudo update-burg  This seems to have fixed it for me.

---

### Post by maxxam05 on 2010-07-24
Did it for me too. thanks. seems that I did not reinstalled Burg properly.

---

### Post by Halzacar on 2010-07-25
No Problem.

---

