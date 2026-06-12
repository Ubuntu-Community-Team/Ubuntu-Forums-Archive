---
title: "Problem erasing DVDRW and burning with k3b"
date: 2006-08-11
forum: Desktop Environments
---

### Post by Saubazi on 2006-08-11
I have a DVD-RW drive and yesterday I tried to erase a DVDRW disk I have written with Nero in Windows in order to rewrite on it. It pretended to do so but the data was still there!?!Burning would not work afterwards.

I have had several thoughts ever since...tried to insert auto,user,rw on /etc/fstab but it did not work.

under /mnt/ I have /mnt/cdrom with all the read and write rights which is a link to /mnt/cdrom0, which does not have those rights?!?! I tried chmoding it but the next time I inserted the dvd it removed all "w"s - I could imagine this being the problem or could it be that while mounting it just simply does not recognise the windows written media as rewritable anymore?

---

### Post by jchau on 2006-08-12
Have you tried Tools->Format DVD+/-RW and then select "Force" and unselect "Quick Format"? 

FYI, I don't have any DVD+/-RWs to try with my computer.

---

### Post by Ocxic on 2006-08-12
some dvd-rw's i think DVD+RW just gets written over, no format required.

---

