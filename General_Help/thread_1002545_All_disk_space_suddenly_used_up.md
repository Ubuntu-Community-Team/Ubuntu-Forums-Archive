---
title: "All disk space suddenly used up"
date: 2008-12-05
forum: General Help
---

### Post by AussieGuy69 on 2008-12-05
All my disk space got used up suddenly - df says

Filesystem            Size Used Avail Use% Mounted on
/dev/sda3              44G   37G  4.5G  90% /

df is saying I have 37G used up. However, Ive done a full "properties" of the / folder in nautilus running as root with sudo, its counted everything totalling 11GB. What could be mysteriously using up the space? something other than a file?

df without -h says /dev/sda3 45718980 36407784 7007076 84% / by the way

What could be causing the inconsistency there? I noticed this problem when gedit would not let me write a text file for "lack of space". I quickly deleted a few big files to free 6gb to maintain system stability but the result is above.

What could be causing this amount of space to be used up and how do I get the space back? If its not used up in files, what could it be?

Ive just rebooted the machine and the space is still mysteriously all used up, as above.

---

### Post by fooman on 2008-12-05
try applications > accessories > disc usage analizer

run a scan with that...should give you a good idea of where the build-up is occurring.

---

### Post by AussieGuy69 on 2008-12-05
it turns out that the disk usage was in the .Virtualbox folder, 25 gigs all up.

Apparently when nautilus was doing its full file count it neglected to look inside hidden folders.

---

