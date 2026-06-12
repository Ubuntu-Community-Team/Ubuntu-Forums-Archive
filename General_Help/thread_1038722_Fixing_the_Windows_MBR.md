---
title: "Fixing the Windows MBR"
date: 2009-01-13
forum: General Help
---

### Post by WhiteRose16 on 2009-01-13
I recently installed Ubuntu 8.04 on my Windows XP partition via Wubi. I later removed the files, planning to update to Ubuntu 8.10. However, when trying to boot the computer, I receive the message: GRUB loading stage 1.5.... Error 21.
GRUB, as far as I know, has overwritten the standard XP MBR. As far as I knew, Wubi didn't require messing around with the MBR. Anyway, the obvious solution would be to repair the Windows MBR via the Windows Install Disk by using the Repair tool. However, this is now unable to find my hard drive; it was able to before. I'm certain the hard drive still works, as I am able to boot into Windows XP fine if I have a boot disk in the drive. Obviously, however, it is not practical to put in a boot disk every time I want to use my computer. Help, please!

---

### Post by caljohnsmith on 2009-01-14
Do you have a Live CD you can boot to use for troubleshooting? If so, how about doing that, download the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what your booting problem might be.

---

### Post by azmo35 on 2009-01-14
Hi,if you don't want help of experient useres and you are looking for kwik fix look [here]("http://www.supergrubdisk.org/")

---

