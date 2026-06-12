---
title: "Newb Question - File Compatablity"
date: 2005-12-24
forum: General Help
---

### Post by Kirt on 2005-12-24
Totally new to Kubuntu and Linex. Loving it so far!

Until I get my wireless sorted and running I have one question:

Can I download a file using XP and and run it on Kubuntu? (Copy to disk, blah, blah blah)

---

### Post by afhp on 2005-12-24
I'm assuming you've got a dual-boot setup. 

If your XP partition is formatted NTFS, you can read from it in Linux but you can't write to it (not a problem with regards to what you asked). If it's FAT32 you can read and write to it. 

Beyond that it depends on *what* you download. XP has no clues about Linux' file permissions so they might have to be adjusted. That said, most of the time you should be downloading archives or .deb files, not executables ; so even that wouldn't be a problem.

---

### Post by Kirt on 2005-12-24
[QUOTE=afhp]I'm assuming you've got a dual-boot setup. 

If your XP partition is formatted NTFS, you can read from it in Linux but you can't write to it (not a problem with regards to what you asked). If it's FAT32 you can read and write to it. 

Beyond that it depends on *what* you download. XP has no clues about Linux' file permissions so they might have to be adjusted. That said, most of the time you should be downloading archives or .deb files, not executables ; so even that wouldn't be a problem.[/QUOTE]

I'm sorry, I was not more specific...

I meant from two seperate computers? Downlaod and burn on CD from one computer (XP) and transfer to other computer (Kubuntu)?

You see, I cannot get online yet with the Kubuntu... and my wife had threatened me with 'life & limb' if I mess with her XP. :shock:

---

### Post by afhp on 2005-12-24
[QUOTE=Kirt]
I meant from two seperate computers? Downlaod and burn on CD from one computer (XP) and transfer to other computer (Kubuntu)?
[/QUOTE]

Since the filesystem on CDs is standardized (ISO9660 regular CD, UDF packet-writing for read/write CDRW) and Linux supports both standards(1) perfectly, there won't be a problem.

(1) As the saying goes, « the nice thing about standards is that there are so many of them to choose from. » :)

> 
You see, I cannot get online yet with the Kubuntu... and my wife had threatened me with 'life & limb' if I mess with her XP. :shock:

I can relate... Must be why I'm still not married :rolleyes:

---

