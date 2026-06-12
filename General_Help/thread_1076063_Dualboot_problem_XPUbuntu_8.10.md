---
title: "Dualboot problem XP/Ubuntu 8.10"
date: 2009-02-20
forum: General Help
---

### Post by dBreak on 2009-02-20
Hello.

So heres my problem:
I installed Ubuntu on drive /D:/ before that i had Windows XP Pro on /C:/. When the ubuntu say that I needed to restart I clicked on the "Restart Now" Button and took the disk out of the Ubuntu CD drive. Then when I choose the from the boot menu /D:/ drive It says
"Please insert a system disk and Press ENTER". Then I try to boot from /C:/ which XP is installed on I just boot into Windows Xp.

What could be wrong and how can I fix it?
The two drives shows in bios. So it´s not "dead disk".
It would be very nice to fix this :)

---

### Post by zy_guy on 2009-02-20
Linux doesn't use "D:". Google is your best friend. For me, the install method was pretty black and white. Did you select your second drive and choose the option to use the whole drive in the installation menus?

---

### Post by mtopro on 2009-02-20
The grub loader is probably on your D: drive or /dev/sdb1 most likely.

You may have chosen to place it there during your install.

Can you boot to the second hard drive?  Try F12 as bios is booting.  If F12 doesn't work, look for a message from your bios telling you how to bring up the boot menu.  The boot menu should show both hard drives and one of them should boot up into Ubuntu.

If there isn't an option to boot to the 2nd drive, under your bios settings you can choose which hard drive you want to load first.  This is the drive that should boot first.

Not ideal for a dual boot situation but should work.  You may want to consider trying to install Ubuntu again and not change the default advanced setting for where the grub host is located.

---

### Post by caljohnsmith on 2009-02-21
In order to get a clearer picture of your setup, how about booting your Ubuntu Live CD (the Ubuntu install CD), download the **Boot Info Script** to the Live CD desktop:

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Then open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---

### Post by dBreak on 2009-02-21
> **mtopro said:**
> The grub loader is probably on your D: drive or /dev/sdb1 most likely.

You may have chosen to place it there during your install.

Can you boot to the second hard drive?  Try F12 as bios is booting.  If F12 doesn't work, look for a message from your bios telling you how to bring up the boot menu.  The boot menu should show both hard drives and one of them should boot up into Ubuntu.

If there isn't an option to boot to the 2nd drive, under your bios settings you can choose which hard drive you want to load first.  This is the drive that should boot first.

Not ideal for a dual boot situation but should work.  You may want to consider trying to install Ubuntu again and not change the default advanced setting for where the grub host is located.

It doesnt load when i boot from the second disk [ubuntu]
It says "Please insert a system disk and press ENTER". 

To **caljohnsmith** I'll try that. :)

---

