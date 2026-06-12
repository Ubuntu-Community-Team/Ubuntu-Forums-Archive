---
title: "Cloning/expanding WinXP drive"
date: 2009-02-01
forum: General Help
---

### Post by Tulya on 2009-02-01
I am trying to clone a 3gig XP Pro drive formatted as fat32 to a 160 gig drive,
I am using a GParted live CD to copy the partition to the new drive and all seems to go well. I have then installed Ubuntu to the large drive in order to install Grub bootloader.
This too goes well and on rebooting the Grub menu appears and Ubuntu will boot normally, but when I try to boot Windows, it reports the error NTLDR missing.
This file does exist on the drive, as does all files from the original drive.
I have tried booting from a floppy disk which contains NTLDR, boot,ini and NTDETECT.COM but Windows will not start.
I cannot install anything on to the original drive because it is completely full!
Any ideas anyone?

---

### Post by caljohnsmith on 2009-02-01
In order to get a clearer picture of your setup, how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---

### Post by Tulya on 2009-02-02
Thank you caljohnsmith for your reply.
I have found the trouble.

The original drive is from a Compaq Pentium II machine and has a custom boot sector and will not boot on any other system.
Also the Compaq will not boot with any other drive.

Looks like he will have to buy a new system.

Sorry for wasting your time.

---

