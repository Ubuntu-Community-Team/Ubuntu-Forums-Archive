---
title: "Copy and Paste using Terminal"
date: 2008-10-23
forum: Desktop Environments
---

### Post by cvandal on 2008-10-23
Hi All,

I've just installed Xubuntu with VMWare Server 2. I've created a Virtual Machine and the folder the VM is stored in is managed by the root account.

I'd like to copy the folder and paste it elsewhere but when I try it, it tells me I don't have permission to do so.

Can I copy and paste the folder using the Terminal and the sudo command? Or is there another way I can work with this folder and it's files?

Thanks,
Chris.

---

### Post by PocketDog on 2008-10-23
I'm not familiar with VMWare but if you run your file browser by typing ```
sudo thunar
``` in Terminal, it gives you temporary root access to your files with a GUI.

-----

Added 'thunar', I originally typed 'nautilus' for the file browser. I don't use Xubuntu, sorry! Didn't notice.. hope it still helps

---

### Post by kilroy423 on 2008-10-23
sudo cp -r source dest

---

