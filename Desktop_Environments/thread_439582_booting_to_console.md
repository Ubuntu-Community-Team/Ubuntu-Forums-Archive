---
title: "booting to console"
date: 2007-05-10
forum: Desktop Environments
---

### Post by hju on 2007-05-10
In Dapper, I used to have a second entry in my grub menu with the additional kernel option to boot to runlevel 3. I'd removed the symbolic link /etc/rc3.d/S13gdm so I could boot to text-only mode and call startx with a different ServerLayout. 

Now I've put Feisty on here, this doesn't seem to work and gdm loads anyway. Is this something to do with upstart and whether it is or not, what should I be doing to allow me to boot straight to the console?

Thanks
hju

---

