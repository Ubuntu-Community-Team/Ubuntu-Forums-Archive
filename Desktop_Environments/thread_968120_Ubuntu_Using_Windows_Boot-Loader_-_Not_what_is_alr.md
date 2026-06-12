---
title: "Ubuntu Using Windows Boot-Loader - Not what is already suggested?"
date: 2008-11-02
forum: Desktop Environments
---

### Post by fidgaf on 2008-11-02
Several posts suggest /boot/grub/ and even Lilo for booting Ubuntu from the Windows Boot-Loader.

I don't want to do it that way.

I have Ubuntu on a dedicated hard drive (Slave) and Windows XP Pro on a dedicated hard drive (Master).

This is done on an old Dell machine and has the option (F12) to choose which drive to boot from on startup. Either XP or Ubuntu can be easily started just by selecting the drive they are on with their existing vanilla MBR and /boot/grub/. Both boot just fine.

I wondered if I could change the Windows Boot-Loader to give me a menu with Ubuntu (Slave) as an option?

I can find it to edit it but have no clue what I should write - if anything.

Thanks.

---

### Post by caljohnsmith on 2008-11-02
It's definitely possible to add the Grub boot loader to your Windows boot loader. One small disadvantage of this is that to get to Ubuntu, you will have to go through two boot menus; the first menu will be the Windows boot loader screen, and the second will be the Grub menu screen. 

One other option you may want to consider though is Grub4DOS, which you can easily install in Windows, and it is simple to set it up to boot either Windows or Ubuntu. You can even configure it so that you have only one boot menu on start up to boot either Windows or any of your Ubuntu Grub entries. Personally I would recommend Grub4DOS, but it's up to you. 

Whichever you decide, it would help if you could first post: 
```
sudo fdisk -lu
```
And we can work from there if you want.

---

### Post by Zimmer on 2008-11-02
EasyBCD will do that for you. It will provide the Ubuntu option and that points to your other drive and GRUB.

---

### Post by fidgaf on 2008-11-02
> **caljohnsmith said:**
> 

Whichever you decide, it would help if you could first post: 
```
sudo fdisk -lu
```
And we can work from there if you want.

Done:

```
Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb65eb65e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    78140159    39070048+   7  HPFS/NTFS

Disk /dev/sdb: 40.0 GB, 40000000000 bytes
255 heads, 63 sectors/track, 4863 cylinders, total 78125000 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63    76630049    38314993+  83  Linux
/dev/sdb2        76630050    78124094      747022+   5  Extended
/dev/sdb5        76630113    78124094      746991   82  Linux swap / Solaris
```

Grub4dos and EasyBCD are not in my Add/Remove - Will I be Ok just hunting them on Google?

Thanks, BTW. I so love the help that I get on these forums.

Ta!

---

### Post by caljohnsmith on 2008-11-02
EasyBCD is only for Vista, so I don't think that's going to help you. To use Grub4DOS, first you'll need to copy over your menu.lst from Ubuntu into Windows. So go ahead and boot into Ubuntu and do:
```
sudo mount /dev/sda1 /mnt
sudo cp /boot/grub/menu.lst /mnt/.
gksudo gedit /mnt/menu.lst
```
And edit all the Ubuntu lines to use (hd1,0) instead of (hd0,0), similar to:
```
title		Ubuntu 8.04, kernel 2.6.24-19-generic
root		[COLOR="Blue"](hd1,0)[/COLOR]
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=77677cb5-6e56-4936-a373-80c15de06bca ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet
```
Next add an entry for Windows at the end of the menu.lst:
```
title		Windows XP Pro
root (hd0,0)
chainloader /ntldr
```
Next boot into Windows, then download the Grub4DOS package from [here]("http://download.gna.org/grub4dos/grub4dos-0.4.4-2008-07-21.zip"), and also the "grubinst" package from [here]("http://internap.dl.sourceforge.net/sourceforge/grub4dos/grubinst_1.0.1_bin_win.zip"). Unzip those packages, and then put the "grldr" file from the grub4dos-0.4.4 package (not the grubinst package) in the Windows root directory C:\, then run the "grubinst_gui.exe" program to install Grub4DOS to the MBR (Master Boot Record) of your Windows drive. Then reboot, and you should get the Grub4DOS menu on start up. Let me know how it goes or if you run into problems.

---

### Post by connonm on 2008-11-02
I actually think this is what you want:

[http://jaeger.morpheus.net/linux/ntldr.php](http://jaeger.morpheus.net/linux/ntldr.php)

This adds a boot image in the windows partition and means an addition to the boot.ini for windows.

I used to use this method before to stop distressing my girlfriend when I first started dual booting :)

---

