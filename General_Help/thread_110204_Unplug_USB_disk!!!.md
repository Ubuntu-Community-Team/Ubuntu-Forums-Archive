---
title: "Unplug USB disk!!!"
date: 2005-12-30
forum: General Help
---

### Post by kurei on 2005-12-30
i unmounted flash disk but It's light is still
Any idea?

---

### Post by Suger on 2005-12-30
man eject :p

Seriously, eject is your solution. You have three options (given that your flash player is /dev/sda mounted in /media/flash)

```

eject /dev/sda
eject /media/flash
eject flash

```

No need to umount before, ain't life beautiful ?

---

### Post by wanger123 on 2005-12-30
Hey thanks suger, I just put a new 'link to application' in my panel which ejects the dvdrw draw with the click of the mouse ie eject /media/cdrom
wanger

---

### Post by kurei on 2005-12-30
thank very much
last i could unpluged it .
> No need to umount before, ain't life beautiful ?
Yes,with Ubuntu :)

---

### Post by chalkie1975 on 2007-11-05
using: 

eject /dev/sda
eject /media/flash
eject flash

How do i create a link in the app launcher panel which will perform all three commands? what do i write as a command line?
this: 
eject /dev/sda, eject /media/flash,eject flash?

---

