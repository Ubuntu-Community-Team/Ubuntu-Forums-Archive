---
title: "Automatically Load Specified Partition"
date: 2009-04-20
forum: General Help
---

### Post by Alitis on 2009-04-20
My mother board (cheap piece of junk) is dieing and will detect but not accept input from my keyboard during startup.  Since it pauses to wait for input I can't get my comp to start.  So the trick is to unhook my keyboard until the OS boots, and then the keyboard works fine.  (Its not my keyboard, I have tried others, and PS2 keyboards).

Anyway, since Ubuntu is the default OS selected, its the only one I can boot. I need to get into Vista to run some programs though, is there a way I can select the Vista partition to automatically be loaded when I restart without using the keyboard during startup? And switch it back to Ubuntu afterward?

---

### Post by Alitis on 2009-04-21
wow... I really hate it when I post a question and find the answer 5 min later.  Seeing as I don't see how to delete a thread, I thought I'd offer the answer to all others who look here for the answer.

Go to your program add/remove, and search "Grub"

Download the "Start-up Manager" app

Open "Start-up Manager" from System -> Administration

There will be a spot to select next default starting partition.



Not really sure how to switch it back after.... but Ill figure it out.

---

### Post by codeseer on 2009-04-21
You could have also edited the 'default' setting in the /boot/grub/menu.lst.

---

