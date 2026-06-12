---
title: "grub not reinstalling"
date: 2009-02-28
forum: General Help
---

### Post by islan on 2009-02-28
I used the instructions located here:  [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

However, it still just boots into Windows.  Any advice?

---

### Post by RedSingularity on 2009-03-01
Is Ubuntu on the same HDD as Windows?

---

### Post by islan on 2009-03-01
No, they are on separate HDDs.

---

### Post by RedSingularity on 2009-03-01
Did you install grub to the HDD with ubuntu on it?  If so you need to change the HDD boot sequence to boot the drive with ubuntu on it.  Try holding f9 at startup.  That should let you select your HD.  Then if that works change your boot sequence in BIOS.

---

### Post by caljohnsmith on 2009-03-01
If you are still unable to boot Ubuntu, how about downloading the **Boot Info Script** to your Ubuntu Live CD desktop:

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Then open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---

