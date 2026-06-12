---
title: "Removing old kernel from HDD+grub help"
date: 2009-01-24
forum: General Help
---

### Post by tunznath on 2009-01-24
After having ubuntu for a while I have a whole list of old kernels, and want to remove them from the HDD and from the grub list - any easy ways? or does anyone have commands for the terminal that will do it?

thanks 
Nath

---

### Post by Yashiro on 2009-01-24
Use Synaptic. Search for linux-image. Be VERY careful of the numbers as you remove them.

Keep your latest and the one previous. Using this method will remove the files from /boot and properly update the grub menu.

---

### Post by fooman on 2009-01-24
ok

---

### Post by Yashiro on 2009-01-24
Using non bundled apps from the universe repository is not necessarily safer. ;)

---

### Post by tunznath on 2009-01-24
Thanks Yashiro - that worked well - 
Nath
Now I just have to figure out how to mark it as solved and thank you

---

