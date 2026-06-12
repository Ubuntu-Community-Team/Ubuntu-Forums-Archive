---
title: "can I write to my ntfs drive?"
date: 2006-06-22
forum: Desktop Environments
---

### Post by fikri on 2006-06-22
Hi there, I just want to ask to everyone about my NTFS drive again, can I write, change, delete some folders or files on my NTFS drive?, I've tried but it can't, it says that my NTFS drive was read-only. Or can I converted it to linux system files on Ubuntu?. Thanks very much for helping me:-D :-D :-D

---

### Post by will_in_wi on 2006-06-22
The kernel drivers cannot really write to ntfs. The only way I know of is called captive-ntfs. You install it, and run the search utility. It will use the windows drivers to access the ntfs partitions. I have had success with it.

---

### Post by rado_london on 2006-06-22
[QUOTE=fikri]Hi there, I just want to ask to everyone about my NTFS drive again, can I write, change, delete some folders or files on my NTFS drive?, I've tried but it can't, it says that my NTFS drive was read-only. Or can I converted it to linux system files on Ubuntu?. Thanks very much for helping me:-D :-D :-D[/QUOTE]
Apparently you can but the default option in ubuntu is read-only. To get info how to make ntfs not read only go [here]("http://ubuntuforums.org/showthread.php?t=142481&highlight=howto+write+ntfs")

---

### Post by fikri on 2006-06-22
where I can get the captive-ntfs?

---

### Post by will_in_wi on 2006-06-23
[http://www.jankratochvil.net/project/captive/](http://www.jankratochvil.net/project/captive/)

---

### Post by Ramses de Norre on 2006-06-23
There should be a serious warning about this in this thread!! 
All software to write from Linux to ntfs is still very experimental and breakage is almost guaranteed! So don't use this on partitions with important data!!

---

### Post by ayoli on 2006-06-23
[QUOTE=Ramses de Norre]There should be a serious warning about this in this thread!! 
All software to write from Linux to ntfs is still very experimental and breakage is almost guaranteed! So don't use this on partitions with important data!![/QUOTE]
sure i agree with that but i ve never experienced pb with wrinting on my ntfs partitions from linux (with CONFIG_NTFS_RW kernel option).

---

