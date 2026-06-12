---
title: "Missing files in an ISO file mount."
date: 2009-06-16
forum: General Help
---

### Post by dvergur on 2009-06-16
I mounted an ISO file with

$sudo mount -o loop /pathtofile/file.iso /media/iso/

(I tried with -t iso9660 first but that gave me no files at all)
This produces two folders in /media/iso/ totalling 30 odd MBs when the iso file is 5.6GB, I might add that I just noticed that the folder says it contains 5.6GB so this is obviously a matter of hidden files.

I have actually had this problem before but I cannot find the solution I used then, the help I got then involved the specific ISO file I was using which was a computer game I think. That solution involved changing the mount command somehow to... show hidden files or something, I don't remember so well since it was a long time ago.

Problem was just dolphin not showing the files, my bad.

---

### Post by error420 on 2011-01-24
Ha ha! Same problem here. All you have to do is press ctrl + h to show hidden files...Strange.

Edit... If you files names start with a period ".", they will not show.

---

