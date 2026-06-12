---
title: "loading screen"
date: 2009-02-28
forum: General Help
---

### Post by rhyz on 2009-02-28
hi this is probably a really stupid question

running ubuntu 8.10

i booted win xp and ubuntu but xp broke and as ubuntu was installed as programme it broke aswell. anyways i couldnt find xp install cd so i installed ubuntu on 5gb unallocated space.
Worked perfectly no problems really like it fond xp cd tried fixing it and replaced mbr :o still didnt work using ubuntu live cd replaced grub booted fine then i decided i would use whole disk as ubuntu now it is working fine but on loading screen i get all the processes that are starting and not the usuall loading splash

the machine runs fine i would just rather the loading screen.

sorry for long post spelling mistakes

---

### Post by NoReflex on 2009-02-28
You must probably configure the boot paramaters - to do that just type in sudo nano /boot/grub/menu.lst and edit the line that says something like : kernel		/boot/vmlinuz-2.6.28-8-generic root=UUID=...... ro quiet and add "splash" to the end of that line. 


Best wishes,
NoReflex

---

### Post by rhyz on 2009-03-01
ok thanks for help just little more needed when i add splash to the end of this line how do i save and exit it shows something like '^X exit' not sure also a little more info when i start grub starts ubuntu it then shows the ubuntu screen with box sliding accross load bar but when it comes to the load it shows the processes its loading

---

