---
title: "Need A little help"
date: 2006-04-03
forum: Desktop Environments
---

### Post by phelixnyc on 2006-04-03
I'm pretty new to Ubuntu so I'm having a little problem. I tried to download Limewire and got an error message when I wanted to run it. It said "rpm not supported" or something alone that line. How do i open a "rpm" file?

---

### Post by KingBahamut on 2006-04-03
[http://doc.gwos.org/index.php/FrostWire](http://doc.gwos.org/index.php/FrostWire) -- Frostwire is a limewire alternative. 

alternately you can use gtk-gnutella , apt-get install gtk-gnutella or search for it in Synaptic.

---

### Post by drotter on 2006-04-03
you need to convert it to a .deb file by using alien

do "sudo apt-get install alien"
which will install alien
then you can run "sudo alien limewire_file_name.rpm" (I think) which will change it to a .deb file

then you can install the new deb package it with dpkg:
"sudo dpkg -i new_limewire_file.deb"

---

### Post by aysiu on 2006-04-03
[QUOTE=drotter]
then you can run "sudo alien limewire_file_name.rpm" (I think) which will change it to a .deb file

then you can install the new deb package it with dpkg:
"sudo dpkg -i new_limewire_file.deb"[/QUOTE] Is it in some way beneficial to separate out these two steps? I usually just do ```
sudo alien -i limewire_file_name.rpm
``` Why convert it to a .deb first?

---

### Post by drotter on 2006-04-03
probally not....
I just always did it that way, and in my mind, if it aint broke...

You're probally right.  That works just fine.  I just never bothered to look up the alien options.

Looks like I learned something new today...thanks

---

