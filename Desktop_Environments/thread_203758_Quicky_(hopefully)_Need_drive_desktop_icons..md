---
title: "Quicky (hopefully) Need drive desktop icons."
date: 2006-06-25
forum: Desktop Environments
---

### Post by helix on 2006-06-25
I have my two EXT3 drives mounted up but I can only access the contents through the mount points, there is no icon on my desktop to access the drives. Now when I plug in my external drive it auto mounts and I do get a desktop icon for the drive. How do i get the two icons for those two drives on my desktop? Would make my life a lot easier. I'm using dapper. Thanks! ;)

---

### Post by scxtt on 2006-06-25
where are you mounting them? -- AFAIK, anything that's mounted in /media is shown on the desktop as an icon ...

---

### Post by aysiu on 2006-06-25
Let's say your drive is mounted at /music and you want it on your desktop: ```
ln -s /music ~/Desktop/music
```

---

### Post by helix on 2006-06-25
Thanks so much aysiu. Though, let me ask you. Does it automatically do that at boot for me? or is there no need? Or do I need to redo the command each time I boot?

---

### Post by aysiu on 2006-06-25
The icon on your desktop will always exist and always point to /music until you delete the icon.

---

### Post by scxtt on 2006-06-25
i think it's easier (and a better representation of the desktop icon setup) to use the built-in /media scheme ubuntu uses ... if you've created mount points for your "music" and "movies" folders (for example) and you mount them in /mnt/music & /mnt/movies it'd be easy to edit your /etc/fstab to mount them in /media/music & /media/movies (which will mount them @ boot and give you icons on the desktop) ... IMO, this is much better than a symbolic link on the desktop, but to each his own ...

---

