---
title: "issues with booting off of my portable HD"
date: 2009-02-24
forum: General Help
---

### Post by extravillager on 2009-02-24
hi, 
i have had ubuntu on my desktop computer for a while now, and it has worked wonderfully. i recently decided to dual boot it with vista on my laptop. because my laptop has a hanously small HD i partitioned some space on my 640 GB HD and installed it on there, this HD is normally connected to my computer but due to its large size and battery requirements i dont take it everywhere. i would expect when the HD is not connected to boot directly to vista however my computer attempts to boot directly to Ubuntu through its GRUB file, but it is not present so it simply reads "Error" and will not allow me any further. can i edit my laptop in any way, or copy the grub file to my HD to cause it to automatticly boot into vista when the HD is not attached?
thanks in advance, 
Extra

---

### Post by extravillager on 2009-02-24
--------------------------------------------------------------------------------

hi, 
i have had ubuntu on my desktop computer for a while now, and it has worked wonderfully. i recently decided to dual boot it with vista on my laptop. because my laptop has a hanously small HD i partitioned some space on my 640 GB HD and installed it on there, this HD is normally connected to my computer but due to its large size and battery requirements i dont take it everywhere. i would expect when the HD is not connected to boot directly to vista however my computer attempts to boot directly to Ubuntu through its GRUB file, but it is not present so it simply reads "Error" and will not allow me any further. can i edit my laptop in any way, or copy the grub file to my HD to cause it to automatticly boot into vista when the HD is not attached?
thanks in advance, 
Extra

---

### Post by caljohnsmith on 2009-02-24
In order to get a clearer picture of your setup, how about downloading the **Boot Info Script** to your Ubuntu desktop:

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Then open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---

