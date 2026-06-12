---
title: "I can't boot ubuntu!"
date: 2009-02-07
forum: General Help
---

### Post by RandomDudeWithComputer on 2009-02-07
When i try to boot ubuntu, it says "Could not mount the partition /dev/disk/by-uuid/A4EC4C22E000E1C3. You can fix this problem by logging on to windows, and entering 'chkdsk /r'." and when i type "chkdsk /r" into command prompt it says "The type of the file system is NTFS.
Cannot lock current drive.

Chkdsk cannot run because the volume is in use by another
process.  Would you like to schedule this volume to be
checked the next time the system restarts? (Y/N)". I am extremely confused. If anybody can help me, that would be great! Thanks!

---

### Post by caljohnsmith on 2009-02-07
In order to get a clearer picture of your setup, how about booting your Ubuntu Live CD (the Ubuntu install CD), download the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to the Live CD desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---

