---
title: "Trying to dual boot Recalbox - need help changeing SSD permissions"
date: 2019-06-22
forum: Gaming &amp; Leisure
---

### Post by phillipprado on 2019-06-22
Hey everyone!

I had the idea to "dual boot" Recalbox on my laptop since I had an empty drive bay that wasn't going to use. So, I threw Recalbox on an old SSD I had lying around, and I added it into my laptop. So far, it's actually worked great. Recalbox creates a partition called "SHARE" that houses the roms and other files, and I have set that to automount to my main OS (Ubuntu 19.04), so I can more easily add roms to the lists. 

The only issue is that I have to use the command line to move roms to the Recalbox SSD using the "sudo mv" command since my main OS doesn't have the correct permissions to write to the Recalbox SSD. After some fiddling about, I haven't really been able to change the permissions of the SSD to allow me to just drag and drop to it. 

Does anyone know how I could do that? It would really make this setup near perfect!

Thanks in advance!

---

### Post by CatKiller on 2019-06-22
If you're mounting something with fstab, you set the ownership and permissions of the mounted filesystem there. Obviously all the files that you've already moved with sudo will now be owned by root.

---

