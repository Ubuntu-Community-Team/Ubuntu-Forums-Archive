---
title: "error 15, can't 'find/ubuntu/disks/boot/grub/menu.lst...NEWBIE, Please Help!"
date: 2009-01-26
forum: General Help
---

### Post by mejbr2003 on 2009-01-26
New to ubuntu, every thing had been going fine for the two weeks using this OS. Installed with WUBI thru XP.
on start-up this morning, I got a command-line...
starts off GRUB4DOS....
I tried some things, finally discovered an error 15 message when I selected the missing menu, or whatever it is.
prior to my failed start-up...I installed a printer in XP...
that is the only thing I can think of that I did diffferently 
please help
thanks

---

### Post by caljohnsmith on 2009-01-26
Do you have the Ubuntu Live CD that you boot to use for troubleshooting? If you haven't all ready deleted the Live CD ISO that Wubi downloads when it installs Ubuntu, you might find the ISO in this directory:
```
C:\ubuntu\install\
```
Once you can boot the Live CD, how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu Live CD desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---

### Post by mejbr2003 on 2009-01-26
I don't have a live CD...no dvd drive...that is why I used Wubi
what should I do?

---

### Post by caljohnsmith on 2009-01-26
Do you have a menu.lst at either of these locations:
```
C:\ubuntu\disks\boot\grub\menu.lst
C:\ubuntu\install\boot\grub\menu.lst
```
If so, please post the contents.

---

### Post by mejbr2003 on 2009-01-26
no I can't get to either one

---

### Post by mejbr2003 on 2009-01-26
any other ideas?

---

