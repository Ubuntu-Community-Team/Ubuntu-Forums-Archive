---
title: "how to get my pictures in my windows partition into ubuntu"
date: 2006-01-12
forum: General Help
---

### Post by angeleyes on 2006-01-12
Hello Its me again ....Ive posted a few times already and first wanted to thank those of you who helped me.
I am a Ubuntu novice ...just having installed it a week ago.
I recently found I have a corrupted or missing boot file in my windows XP so I cant get it started(can anyone help me with fixing that?).I have alot of family pictures in it and wanted to know if there was anyway I could transfer them into my Ubuntu so I can burn them to cd?
I appreciate any help you could give me.
Thanks ahead of time

---

### Post by carlosqueso on 2006-01-12
Can you post your fstab file, just type (in a terminal) ```
sudo gedit /etc/fstab
``` and paste it here.

---

### Post by jasay on 2006-01-12
You should be able to [mount your windows partition]("http://help.ubuntu.com/starterguide/C/ch05.html") and then transfer the files.  With XP you probably have a NTFS filesystem.

---

