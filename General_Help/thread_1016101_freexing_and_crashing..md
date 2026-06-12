---
title: "freexing and crashing."
date: 2008-12-19
forum: General Help
---

### Post by PsYcHoTiC_MaDmAn on 2008-12-19
started another thread elsewhere but that was to do with ubuntu (which I've un-installed and put xubuntu in its place)

I have an older PC which used to run windows XP, however when I dug it out the other day and tried switching it on it kept rebooting, attempted the recovery disk but got nowhere.

as I couldn't create a boot disk with partition magic I transferred the hard drive to the computer that is working (the one I'm typing on now(also XP))I then formated the hard drive, 

having downloaded v8.10 of ubuntu I burned it to DVD which the computer refused to boot from, so I then downloaded unetbootin and got it to boot from a USB stick instead. the only problem being that the other PC wouldn't boot from USB despite me setting it to do so from bios.

therefore I removed the main hard drive from the working machine, and shoved the other in, and installed via USB stick, no problems, the system ran stable, and worked straight off.

however once I transferred it to the other PC it started randomly freezing, with the odd reboot. freezing both during start up and in the middle of starting/in programs.

as a result I reformatted the hard disk, and installed xubuntu (in the same manner as previously) again works fine on the one machine, but refuses to run on the other. with the same problems reoccurring.

the one thing that leads me to believe that its not anything to do with the CPU or memory is that both suse 9.2 (albeit incredibly slowly) and knopix worked fine when run off the cd. 

first PC (the one that runs properly) AMD Athlon 64 3200+ (1.9GHz)512 MB PC3200 RAM 160GB hard drive.

second PC (the one I'm trying to get to work) AMD Athlon 1200+ 256mb PC2100 RAM 20GB seagate baracuda hard drive.

I've attempted installing some of the updates, however it just wont carry on further than about 5minutes downloading.

think I've covers all the data needed. if this doesn't work I'm going to try digging out a copy of XP home, and see if that will run stable.

---

### Post by spiderbatdad on 2008-12-19
have you tried running with the boot option acpi=off or noapic? This parameter is fairly common, especially in older machines. You can try it once from the grub menu by using the arrow key to select your kernel then press 'e' Use the arrow key again to move to the line that begins with the word kernel, and press 'e' again. Now move to the end of that line and delete quiet splash --. Type in noapic and hit enter, then press 'b'

To make this entry permanent for grub, edit the file /boot/grub/menu.lst ```
sudo nano /boot/grub/menu.lst
```scroll to the section that looks like this: ```
## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-9-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=XXXXX ro **lapic hpet=force pci=routeirq** 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

```where I have highlighted above, you'll be entering "noapic"

---

### Post by PsYcHoTiC_MaDmAn on 2008-12-19
I've attempted the permanent suggestion of yours, however 2 things, one the kernel is 2.6.27.7 and is different after that

and the other thing is when I try and save (having deleted "quiet splash") it says cant open file to write. 

it did seem a little more stable once I'd attempted that, managed to get through the big linux update(29mb or thereabouts) without crashing

however its still hanging, and requiring regular restarts

---

### Post by PsYcHoTiC_MaDmAn on 2008-12-19
I've put the hard disk into the other computer and it is running perfectly. 

shoved the hard disk from the computer that was running previously into the other machine and XP started up 

so somehow xubuntu has a problem with the other machine

any thoughts

---

### Post by PsYcHoTiC_MaDmAn on 2008-12-31
An update on where things are. (hence the repeat on all 3 other threads I started otherwise)

tried installing XP pro afterwards, and had a page file error, so no luck then. 

however I recieved the RAM I'd ordered for the other pc (the one I'm typing on) so transferred the 512mb stick from the 1 machine to the other. 

attempted to boot off the CD, but had no luck again, no idea what the problem was (got through the choose language etc, and when I tried install it just froze up). so transferred the hard disk to the other machine (this 1 again) reformatted it, (Ext3) and installed it via USB stick (incidently, made a mistake with unetbootin, setting it to xubuntu, when i didnt realise it was the ubuntu I had selected) and installed all the updates. 

having done that I then transferred the hard disk back to the other machines, (with a degree of worry that what had previously happened would reoccur) and it booted up fine.

I've had it running for several hours, downloaded and installed flash player, and its running perfectly. 

so works fine with 512mb of RAM, but not so with only 256 (that goes for both ubuntu and xubuntu)

---

