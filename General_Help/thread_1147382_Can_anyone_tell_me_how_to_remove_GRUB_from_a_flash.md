---
title: "Can anyone tell me how to remove GRUB from a flash drive?"
date: 2009-05-03
forum: General Help
---

### Post by gohanssjn on 2009-05-03
I used a flash drive as a way to run Ubuntu for a few days, but now I want that flash drive back to normal.  I formatted it as FAT32, but GRUB is still there and forced my laptop to try and boot from it when inserted.

I don't want it to have ANY bootable MBR on it (Windows or GRUB), but that's the only kind of help I can find (replacing GRUB with a Windows one).

So, how can I remove it?

---

### Post by wpshooter on 2009-05-03
Try [www.killdisk.com](www.killdisk.com) 

Be careful not to WIPE your hard drive(s).

---

### Post by caljohnsmith on 2009-05-03
> **gohanssjn said:**
> I used a flash drive as a way to run Ubuntu for a few days, but now I want that flash drive back to normal.  I formatted it as FAT32, but GRUB is still there and forced my laptop to try and boot from it when inserted.
Grub does not force your laptop to boot the flash drive, that is determined by your BIOS boot order. I would suggest going into your BIOS change the boot order so the USB flash drive does not boot first on start up. But if you also want to wipe Grub from the MBR (Master Boot Record) of the flash drive, you can do that with:
```
sudo dd if=/dev/zero of=/dev/[COLOR="Red"]sdX[/COLOR] bs=440 count=1
```
And replace "sdX" with your flash drive. Let me know how that goes or if you run into problems.

John

---

### Post by gohanssjn on 2009-05-04
> **caljohnsmith said:**
> Grub does not force your laptop to boot the flash drive, that is determined by your BIOS boot order. I would suggest going into your BIOS change the boot order so the USB flash drive does not boot first on start up. But if you also want to wipe Grub from the MBR (Master Boot Record) of the flash drive, you can do that with:
```
sudo dd if=/dev/zero of=/dev/[COLOR="Red"]sdX[/COLOR] bs=440 count=1
```
And replace "sdX" with your flash drive. Let me know how that goes or if you run into problems.

John

Great, I will try this later.  I need to keep the USB as the first boot device for other reasons, so this will be very helpful.

---

### Post by gohanssjn on 2009-05-09
> **caljohnsmith said:**
> Grub does not force your laptop to boot the flash drive, that is determined by your BIOS boot order. I would suggest going into your BIOS change the boot order so the USB flash drive does not boot first on start up. But if you also want to wipe Grub from the MBR (Master Boot Record) of the flash drive, you can do that with:
```
sudo dd if=/dev/zero of=/dev/[COLOR="Red"]sdX[/COLOR] bs=440 count=1
```
And replace "sdX" with your flash drive. Let me know how that goes or if you run into problems.

John

Now I cannot even format the drive or make a new partition :(

---

### Post by Legace on 2009-05-09
> **gohanssjn said:**
> Now I cannot even format the drive or make a new partition :(

Open Gparted. (use sudo apt-get install gparted if you don't have gparted)
```
sudo gparted
```

Select your device from the list under the Mimimize/Maximize/Close buttons.

Select Device, then Create Partition Table. And then OK.

Now you should be able to create partitions..

---

