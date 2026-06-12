---
title: "psp file write / delete problems"
date: 2009-02-17
forum: General Help
---

### Post by sansa dude on 2009-02-17
when i try to add music on my psp and delete some other files ubuntu won't let me saying i can not do this on a read only disk so i went to properties > permissions of my psp and tried to change the settings but i don't think its letting m,e change them or they don't stay after ive closed the window 
any suggestions?

---

### Post by meson2439 on 2009-03-09
I usually do the copy, replace and delete stuff using the terminal. More convenient. For example to transfer a game ISO from my hard disk in /media/sda1 to my psp folder in /media/sdd1/ISO 

```

cd /media/sda1
sudo cp brave.iso /media/sdd1/ISO
```

use mv instead if you want to cut and paste. To delete

```

sudo rm -f /media/sdd1/ISO/brave.iso
```

use wildcards to do multiple repetitive task such as

```

cd /media/sda1/videos
sudo cp *.avi /media/sdd1/Video
```

This is a temporary solution but it should be enough to get things done. Editing your /etc/fstab for the psp mount parameters may yield a better solution. Unfortunately I haven't try it yet.

---

### Post by rbo83 on 2009-04-28
Sansa Dude,

I'm in Barrie south. I am looking for a copy of the Jaunty release iso I could copy to a USB stick or a CD I could use (I have no DVD). My internet is too slow for download

---

### Post by em3rl_v on 2009-06-09
Hey, i took your advice and tried deleting the files via terminal, but it still gave the the read only error...does anyone know a more perminant solution?

---

