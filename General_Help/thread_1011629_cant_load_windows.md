---
title: "cant load windows"
date: 2008-12-15
forum: General Help
---

### Post by roxuresox on 2008-12-15
i have my computer set up to dual boot with ubuntu and windows xp, but when i select the xp loader it tells me that "NTLDR is missing" and it restart it, how can i get it back so i can access my windows OS

---

### Post by 2hot6ft2 on 2008-12-15
I'm sure this is NOT the right way to do it but I'll attach mine in a archive so you can extract it and copy it to the root of your windows if all else fails. But I would only try that as a last resort.

---

### Post by Tim Sharitt on 2008-12-15
If you have your windows XP cd, you can boot from it and there should be an option to repair windows, while leaving your files intact. You may have to reinstall grub, but there is a handy guide to it here: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows").

---

### Post by caljohnsmith on 2008-12-15
Most of the time when you get a "NTLDR missing" error when trying to boot Windows after installing Ubuntu, it is simply because Grub is trying to boot the wrong NTFS partition. In order to get a clearer picture of your setup, how about downloading the attached "boot_info7.sh.txt" file to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo sh ~/Desktop/boot_info7.sh.txt
```
That will create a "BootInfo.txt" file on your desktop; please attach that to your next post, or simply copy/paste the contents to your next post. That will help clarify your setup and what your problem might be about booting Windows.

---

### Post by roxuresox on 2008-12-15
tired making the boot info doc but all it says is 
sh: Can't open /home/stoffer/Desktop/boot_info7.sh.txt

---

### Post by meierfra. on 2008-12-15
[QUOTE=roxuresox]sh: Can't open /home/stoffer/Desktop/boot_info7.sh.txt [/QUOTE]

Did you download the file ""boot_info7.sh.txt" (see post 4) and is it on your Desktop?

---

### Post by roxuresox on 2008-12-16
got it, stupid me thought he ment that was an example of the doc. 
the one im trying to get to load is the the windows install on my sda drive which is also the one ubuntu is installed on

---

### Post by caljohnsmith on 2008-12-16
OK, that helps clarify your setup; are you able to boot into Ubuntu? It doesn't look like your Ubuntu entries in your menu.lst are correct, because they are missing either a "uuid" line or a "root" line. How about booting your Live CD and doing:
```

sudo mkdir /mnt/sda1 /mnt/sdc3
sudo mount /dev/sda1 /mnt/sda1
sudo mount /dev/sdc3 /mnt/sdc3
gksudo gedit /mnt/sdc3/boot/grub/menu.lst
```
And then replace your existing Windows entry with:
```
title Windows NT/2000/XP (loader)
rootnoverify     (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1

```
And then add a "uuid" line to all your Ubuntu entries similar to:
```
title Ubuntu 8.10, kernel 2.6.27-9-generic
[COLOR="Blue"]uuid  5894fb6b-ca2e-4f42-baa0-8ac349084ab8[/COLOR]
kernel /boot/vmlinuz-2.6.27-9-generic root=UUID=5894fb6b-ca2e-4f42-baa0-8ac349084ab8 ro quiet splash
initrd /boot/initrd.img-2.6.27-9-generic
```
Next you'll need to modify your Windows boot.ini file, so do:
```
gksudo gedit /mnt/sda1/boot.ini
```
And change it as follows:
```
[boot loader]
timeout=30
default=multi(0)disk(0)[COLOR="Blue"]rdisk(0)[/COLOR]partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)[COLOR="Blue"]rdisk(0)[/COLOR]partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect
multi(0)disk(0)[COLOR="Blue"]rdisk(0)[/COLOR]partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn /usepmtimer
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons
```
Save, reboot, and let me know exactly what happens when you boot Windows from the Grub menu. We can work from there.

---

### Post by roxuresox on 2008-12-16
well ubuntu loads perfectly fine cept after i installed ubuntu, it made it so i couldnt get into xubunt, no big deal i just uninstalled that, and when i tried getting the boot.ini it comes up blank but i have grub editor installed so what im gonna try is setting it to look in (hd0,1) and see what happens, it was originally set to (hd2,0) so if im reading the code you gave me right changing it to 0,1 should correct things, im gonna reboot and let you know what happens

---

### Post by roxuresox on 2008-12-16
ok so i did that change and instead of the ntlrd missing it just stays at 

"Starting up...."

---

### Post by roxuresox on 2008-12-16
thanks, i must have  missed something when when i was putting all that stuff in the console, works now, unfortunatley their happens to be a windows file corrupted so thats my next task but as far as getting to it thats nothing

thanks everyone for the help

---

### Post by roxuresox on 2008-12-16
ok new problem with loading windows, i cant mount the partition in ubuntu that has the windows partition i use,  so ne idea how i can mount the partition?

---

### Post by roxuresox on 2008-12-16
ok, all is good, thanks everyone

---

