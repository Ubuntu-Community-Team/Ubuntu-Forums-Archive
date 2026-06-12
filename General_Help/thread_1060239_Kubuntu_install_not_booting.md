---
title: "Kubuntu install not booting"
date: 2009-02-04
forum: General Help
---

### Post by Sabz on 2009-02-04
hello i recently tried to install Kubuntu on my XP machine here are the specs:

Desktop- Dualboot
Mobo: ASUS p5l2d-vm
CPU: P4 prescott @ 4ghz
RAM: OCZ 2x2 reaper 1066
GFX: ATI powercolor 4870 1gb
HDD's: IDE 160 gb, sATA 320gb and 640 gb
OS's: winXp sp3 & Kubuntu 8.10 -intall using wubi

i'm having difficulties booting into kubuntu because it only boots from windows bootloader and when i select Kubuntu i get the loading page then just a white screen, i hear the welcome tone but the screen remains blank/white till it restarts.

how do i boot into kubuntu safe boot without grub?

tried fixes:
1)boot from ubuntu live CD and re-instal grub===> Error 15 file not found (/boot/grub/stage1)
2)burnt all files from [here]("http://www.supergrubdisk.org/index.php?pid=5")
to a CD and tried booting from it Supergrub found ===> bios msg prompt: please insert a bootable CD or check bood priority..bla..bla

As you can see ive been scratching my head all day trying to get this to run.. 

Calling all Ubuntu drinkers please advise

Thanks
Sabz

---

### Post by Sabz on 2009-02-04
Ok i managed to get to the GRUB menu.. Selected Kubunto (vga problems..etc)
i get an error msg at log-in along the lines of "Disk is not clean, please run chkdisk -r from windowns then reboot will complete"

Back to windows, ran error-checking on wubin instal hdisk

Reboot-->Kubuntu (vga problems)-->same login error

Back to windows run--->cmd prpmt---> chkdisk

i'm about to reboot now. hopefully il finally get to see my first bot into Kubuntu on this machine.... AWWW my head hurts

---

