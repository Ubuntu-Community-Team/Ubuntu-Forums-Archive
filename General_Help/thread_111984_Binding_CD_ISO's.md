---
title: "Binding CD ISO's"
date: 2006-01-03
forum: General Help
---

### Post by ATAQ on 2006-01-03
Hi I would like to bind some of my game CD ISO's into one DVD image, does anybody know how I can do this?

---

### Post by sciurus on 2006-01-04
I think you could 
1) rip all the CD's using the command dd if=/media/cdrom of=*cd_image_name.iso*
2) Create a folder such as ~/dvd with subfolders for each cd image.
3) Mount the cd images to the subfolders,  mount -t iso9660 -o loop *iso_file_location* ~/dvd/*subfolder_name*
4) Make a new iso that includes all the images. mkisofs -o *dvd_image_name*.iso ~/dvd

It maybe be possible to skip steps 2 and 3 and directly merge iso images, I don't know enough to say. I'm not sure if your games will still work from the DVD.

---

