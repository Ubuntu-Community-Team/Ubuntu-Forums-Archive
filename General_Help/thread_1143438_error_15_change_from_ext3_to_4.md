---
title: "error 15 change from ext3 to 4"
date: 2009-04-29
forum: General Help
---

### Post by texas.chef94 on 2009-04-29
Obviously I made a monumental error in using gparted to change 9.04 ftom 3xt3 to 4.
Received error 15 at reboot. Went back reversed to ext3 in hopes of recovery no soap.
On my wife's PC and that is almost as bad as error 15 on mine
Please advise

Allen

---

### Post by texas.chef94 on 2009-04-29
Was on line did nothing else but insert gparted live CD restart PC change 9.04 from 3 to 4. Rebooted and received error 15. In desperation reversed but I suspected it would not help and it did not.

Please advise
My wife does not LIKE me on her PC

---

### Post by codeseer on 2009-04-29
> **texas.chef94 said:**
> Was on line did nothing else but insert gparted live CD restart PC change 9.04 from 3 to 4. Rebooted and received error 15. In desperation reversed but I suspected it would not help and it did not.

Please advise
My wife does not LIKE me on her PC

I am pretty sure you weren't supposed to be able to do that, because I think it's 'impossible' to convert from ext4 to ext3 without a reformat. When you try to mount it, do you see any data at all on the partition?

Your best course of action would probably be to restore from backups.

---

### Post by fenian on 2009-04-29
How many Hard drives are in your computer.

---

### Post by quimico69 on 2009-04-29
in my experience, error 15 meant the hard disk was shot.  I had to buy a new one.  It can also mean that grub cannot find the linux kernel.  Perhaps someone more knowledgeable can shed some light on this case?

---

### Post by codeseer on 2009-04-29
I responded to his duplicate post here: [http://ubuntuforums.org/showthread.php?p=7180975](http://ubuntuforums.org/showthread.php?p=7180975)

Basically, your not supposed to be able to revert back to ext3 from ext4; that is without reformatting. Most likely all the data is gone and it could have performed a format. His best course of action would be to restore from backups most likely.

---

### Post by texas.chef94 on 2009-04-30
Strangely enough I either had not read or it did not register pertaining to ext4 not being stable yet because I set up my USB 160 GB data drive with ext4 and its worked famously. So reinstall seemed my option, but with greater ease because of the back ups on data drive. Allen

---

### Post by sahabcse on 2009-04-30
Try to Fix the grub, follow below url

[http://sahabm.blogspot.com/2009/01/grub-fix-ubuntu.html](http://sahabm.blogspot.com/2009/01/grub-fix-ubuntu.html)

---

### Post by caljohnsmith on 2009-04-30
Texas.chef94, in consideration of those who try to help you, please observe the forum rules and do not start multiple threads of the same subject/problem. :)

But about your Grub error 15 problem, how downloading the **Boot Info Script** to your Ubuntu desktop (can be the Live CD):

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Then open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

John

---

