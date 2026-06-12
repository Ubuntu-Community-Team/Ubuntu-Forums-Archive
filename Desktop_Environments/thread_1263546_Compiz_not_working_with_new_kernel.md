---
title: "Compiz not working with new kernel"
date: 2009-09-11
forum: Desktop Environments
---

### Post by Mayfairy on 2009-09-11
I just had a strange occurrence. I was installing new updates and noticed there was a new kernel entry in the mix (2.6.28.15) and I booted my machine as instructed. 

After the bootup I noticed I was still running my old 2.6.28.13 kernel. Installed Grub (for some reason it wasn't installed) and did 'update-grub' which brought the new kernels (14 and 15) on my menu.lst. 

Booted again and chose 15, but then I got a graphics error when logging in. Can't find Nvidia and the usual. I could log in with low-graphics mode, meaning no compiz and window borders until I switched to metacity. 

Booted again with kernel 14 and the same thing happened. Yet another bootup with kernel 13 this time and everything worked nicely, just like before. 


This got me to wondering what the heck is going on. As far as I know (which isn't a lot) changing my kernel shouldn't affect my graphics or anything like that, especially since menu.lst was the only file that changed in the process. 

Wonder if there's something iffy with the new kernels and Compiz, cause I can't think of anything else causing it. 

For the time being I will be running my 2.6.28.13 kernel, but it would be nice to know if anyone else has encountered similar issues.

---

### Post by Mayfairy on 2009-09-16
Bump bump. Am I really the only one experiencing this?

---

