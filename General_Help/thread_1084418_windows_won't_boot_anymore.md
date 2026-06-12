---
title: "windows won't boot anymore"
date: 2009-03-02
forum: General Help
---

### Post by benner on 2009-03-02
i had ubuntu installed.  all good.  i temporarily unplugged that hard disk when i installed xp on another drive.  then plugged it back in.  made that the first drive in the order and just ran xp for a while (media center edition).  last night i decided to set up grub properly and have my multiboot.  i was once again able to boot into ubuntu with no trouble.  but when booting into the XP that had been working 10 minutes earlier, i got 'starting up...' then nothing.  it just hung there.  so i went into the bios and changed the hard disk order again so the xp disk was first.  i just wanted to make sure that it was ok.  now i get a 'there was an error loading your operating system' message and it hangs indefinitely. 
i put a lot of time into setting that installation up properly but the only way i now to fix it like that is to reinstall.
i don't really know how to use the XP repair console.
can anyone advise me here?
(in the meantime, i am searching through the forums for more answers but my wife is now pissed at me for breaking the computer... i am therefore in a bit of a hurry.)

thanks in advance

---

### Post by Altay_H on 2009-03-02
If you don't mind losing your ability to boot into your linux partition, [SuperGrub]("http://stmaarten.globat.com/~supergrubdisk.org/index.php?pid=5") is a good tool to fix GRUB problems. You should be able to use it to replace GRUB with MBR and thus restore your Windows install.

---

### Post by sahabcse on 2009-03-02
hi

For Fixing the grub follow give url


=========================================
[http://sahabm.blogspot.com/2009/01/grub-fix-windows.html](http://sahabm.blogspot.com/2009/01/grub-fix-windows.html)
[http://sahabm.blogspot.com/2009/01/grub-fix-ubuntu.html](http://sahabm.blogspot.com/2009/01/grub-fix-ubuntu.html)
=========================================

Regards,
Sahab

---

### Post by caljohnsmith on 2009-03-02
In order to get a clearer picture of your setup, how about downloading the **Boot Info Script** to your Ubuntu desktop:

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Then open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your Windows booting problem might be.

---

### Post by benner on 2009-03-07
when i put the disk order back the way it was, i was able to boot into windows again.  to get into ubuntu, i have to hit f11 (or whatever) at boot to temporarily change the boot sequence.  i think i won't bother with it for now.  when jaunty comes out, i will do a fresh install and let grub take over the MBR on the windows partition.  i imagine it will work out then.  i just have to wait a month.

cheers.

---

