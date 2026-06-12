---
title: "Message MBR 2FA:"
date: 2008-12-29
forum: Dell Ubuntu Support (CLOSED)
---

### Post by lhrich24 on 2008-12-29
I purchased a Dell Mini laptop for my daughter for Christmas.  When we turn the laptop on we are getting the message MBR 2FA: 
Dell tech support will not help with Ubuntu.

---

### Post by wizard10000 on 2008-12-29
> **lhrich24 said:**
> I purchased a Dell Mini laptop for my daughter for Christmas.  When we turn the laptop on we are getting the message MBR 2FA: 
Dell tech support will not help with Ubuntu.

Press "2" when you see this message.  What's happening is you're being asked where to boot the machine from - second partition on the hard drive (2), floppy (F) or Auto (A).

---

### Post by lhrich24 on 2008-12-29
Finally found phone number to Ubuntu tech support, but wait is long.

---

### Post by lhrich24 on 2008-12-29
> **wizard10000 said:**
> Press "2" when you see this message.  What's happening is you're being asked where to boot the machine from - second partition on the hard drive (2), floppy (F) or Auto (A).

Thanks I tried this and it still did not work.

---

### Post by sirebral on 2008-12-29
> 
If you have an original Dell Mini 9 with Ubuntu pre-installed, you may have a hard time entering the GRUB menu as the default delay is zero. This is particularly problematic if you're trying to reset your password using the passwd command.

You can enter the recovery mode following these steps:

   1. Boot the mini 9 while pressing ESC every second
   2. When you see the "MBR 2FA:" prompt or similar, the boot process is stopped.
   3. Press ENTER and ESC very fast one after the other.
   4. You should then see the GRUB menu. Using the up and down arrows, highlight the second option and press ENTER to boot into recovery mode. 


Taken From: [https://help.ubuntu.com/community/DellMini9](https://help.ubuntu.com/community/DellMini9)

---

### Post by caljohnsmith on 2008-12-29
Do you have a Ubuntu Live CD? If so, how about booting that, open a terminal (Applications > Accessories > Terminal) and do:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what your problem might be.

---

### Post by sirebral on 2008-12-31
BUMP.  I am wondering how if this was fixed.

---

