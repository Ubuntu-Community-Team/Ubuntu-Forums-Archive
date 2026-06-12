---
title: "Setting User permissions"
date: 2005-09-06
forum: Desktop Environments
---

### Post by Hg80 on 2005-09-06
Im guessing i cant paste the files i want into /usr dir as i havent got the right permissions...
Is there a way i can set my user account to have the same prermissions as the root as there is no root account in Ubuntu (am i rigth in thinking that? im sure i heard somewhere ubuntu doesnt use a root account?).
Many Thanks

---

### Post by vruum on 2005-09-06
hi, Ubuntu uses sudo, instead of root, so you just add "sudo" in front of a command, and it gets executed with root permissions, so to copy files from the command line you'd type "sudo cp file destination" or you could run "sudo nautilus", to open nautilus with root permissions. 
all that said. Be careful, it's rather easy to mess stuff up that way

---

