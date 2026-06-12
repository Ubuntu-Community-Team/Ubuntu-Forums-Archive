---
title: "Nautilus takes 100% of the CPU"
date: 2008-08-19
forum: Desktop Environments
---

### Post by mariourk on 2008-08-19
I'm having a weird problem with Nautilus. When I open an SMB-share with photos, it starts to render thumbnails of the pictures. At a certain point it will stop rendering the thumbnails, while the CPU-load jumps to 100%. This is very annoying.

Are there more people who experience this problem? Does someone know if there is a fix or a workaround?

Thanks! :)

---

### Post by ragtag on 2008-08-27
No you're not alone. :)

I have this same bug with .avi video files, both on a FAT32 drive and an ext3 drive, haven't tested with Samba (smb) share though. Nautilus will work fine with a folder with several hundred .jpg images, but if I open a folder with just 3-4 .avi files, it will begin churning on the drive and eat up CPU. If I don't either go up one folder or kill Nautilus, the computer will eventually become unresponsive.

This began happening recently, though a bit of searching on the web shows people having similar issues a couple of years ago, but I've not seen a clear pattern in when it happens. Some had problem when downloading video files and looking at them in Nautilus, but that's not my case.

Currently I'm trying to figure out how to replace Nautilus with Thunar in Ubuntu (don't really want to go all the way with Xubuntu), as Thunar seems to run without problems for me.

---

### Post by estyles on 2008-08-27
I had a similar, but not exactly the same, problem.  I fixed it by reinstalling fglrx.  If you use an ATI video card, try re-installing the proprietary drivers.

---

### Post by mariourk on 2008-08-28
It turned out that I had this problem with only one directory. As soon as I entered it, the CPU would shoot to 100%, even when it was empty. I solved it by deleting it, creating a new one and copying all the files back to it.

Still a strange problem though.

---

