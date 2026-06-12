---
title: "Dual boot"
date: 2006-09-18
forum: Desktop Environments
---

### Post by madsurfer on 2006-09-18
Hi 
Have installed Ubuntu but need to go back to my old windowsXP to get a backup of outlook. When I first installed, grub gave me the option to reboot in windows, now this option seems to have gone, when I press esc to get into grub's boot list my old windows has disappeared even though all the files are there. How do I reboot my old windows?
Adrian

---

### Post by Average Joe on 2006-09-18
You could try:

sudo update-grub

That should restore all your grub entries.

Or put back the Windows boot entry yourself in the file /boot/grub/menu.lst (make a backup first!)

title Windows Whatever
root        (hd0,0)
makeactive
chainloader +1

I am not sure about the (hd0,0) though. It is kind of default when you have only one hard disk that previously only contained Windows. But it could differ in your case.

---

### Post by madsurfer on 2006-09-19
Thanks for the info, edited the grub file and installed the windoze boot, seemed to work fine.

---

