---
title: "Live USB help - Dual booting nubuntu and Hirens Boot CD"
date: 2009-04-23
forum: General Help
---

### Post by garethsimpsonuk on 2009-04-23
Hi all,

Well I'm trying to do something that i think is really cool and that is a multi bootable usb flash disk.

I'd like to install ubuntu (for portable os), Nubuntu (for security / networking etc. ) Hirens Boot CD for hardware diags etc.

So far I have hirens boot disk as per his guide,[http://www.hiren.info/pages/bootcd-on-usb-disk]("http://www.hiren.info/pages/bootcd-on-usb-disk") (and it works). 

I'm now trying to get nubuntu working. So far I've copied the iso contents to the root and edited the menu.lst to point to /isolinux/isolinux.bin. I don't know any grub so I just copied the previous entry and tried that. It didnt work so then I changed ap --mem /isolinux/boot.cat to point to 'boot.cat' also this threw up errors.

does anyone know I can edit the menu.lst to boot the nubuntu kernel in the options menu?

Here is the menu.lst so far ```
timeout 60
default 0

title Boot from Hard Drive
rootnoverify (hd0,0)
chainloader (hd0,0)+1

title --------------------
root

title Start Hiren's BootCD
find --set-root /HBCD/boot.gz
map --mem /HBCD/boot.gz (fd0)
map --hook
chainloader (fd0)+1
rootnoverify (fd0)
map --floppies=1
boot

title Mini Windows Xp
find --set-root /HBCD/XPLOADER.BIN
chainloader /HBCD/XPLOADER.BIN

title Start Nubuntu
find --set-root /isolinux/isolinux.bin
map --mem /isolinux/boot.cat (fd0)
map --hook
chainloader (fd0)+1
rootnoverify (fd0)
map --floppies=1
boot
```

The last entry is mine. Could someone please tell me what i need to point this to.

any help would be appreciated, thanks.

edit: just to let you know the error is invalid / enexecutable format. files that seem important for this are /casper/initrd.gz and isolinux/isolinux.bin. i just don't know how to get these to work. i'm thinking that there are 2 different bootloaders here (isolinux and grub) so im guessing i may have to 'chainload' these? is this correct and can enlighten in how to do it.

thanks

---

### Post by garethsimpsonuk on 2009-04-24
bump

---

### Post by garethsimpsonuk on 2009-04-24
i spoke to my lecturers today and one said use unetbootin, whilst another said to use grub as it will help me learn. 

i prefer the first option! what do you guys think?

update: it turns out unetbootin doesnt seem to be able to dual boot (not without manual editing of the bootloader)

update: any guidance would be appreciated,
thanks

update: i have tried many different options, i managed to get one boot loader to load another kernel but it froze as it was booting.

---

### Post by garethsimpsonuk on 2009-04-25
bump

---

### Post by garethsimpsonuk on 2009-04-27
ok i give up after this one :-)

---

### Post by mc_scRAT on 2009-05-20
Got same idea - but my multiboot is a little bit different. no matter. i got Jaunty desktop iso unpacked to (usbdrive)/ubuntu-9.04/ folder. i got ntldr bootsector on my usb unstalled. and got grub4dos chainloaded in ntldr. so, i got grub4dos now.
but from here i don't know where to go: i tried to boot isolinux - but it reports incorrect checksum (i'm sure it's correct!!).
i loaded vmlinuz and initrd directly from grub - but all i have reached is busybox (but it's better than nothing of course!). so i' in no-way-out. heelp!!

---

### Post by dude051 on 2009-05-26
Currently the only way I have found to do this with Ubuntu 9.04 is by using syslinux and not grub4dos. I had 8.10 working fine with grub4dos, and it worked great because it can load the ISO's for other things. I have a super rescue CD like you want, with FreeDOS, Ubuntu 8.10 and Backtrack3. The problem lies with some changes they made to 9.04 booting.

So far the only way I can get the liveCD/liveUSB of 9.04 to work is by using syslinux or GRUB. syslinux is more versatile and can boot the other systems... but I will have to modify them further like I did for my PXE network  :(

By the way, the reason I am saying this is because that guide you followed installed GRUB4DOS not GRUB, which like I said, is unable to boot the new Ubuntu from what I have found.

If I get a similar set up working using syslinux, I'll share.

---

### Post by garethsimpsonuk on 2009-06-20
great! thanks for the info.

i gave up in the end as it is far too complicated for me. it's a shame as i bought a 16 gb usb just for this. 

i have hundreds of portable apps for it to and figured this would be an amazing tool.

if you (or anyone) figures this out please give me a shout and I will send you the 100s of tools i have for your help. i have things like portable word, firefox etc. tor browser (proxy), calendars etc. then i have diag stuff like ccleaner, virus tools, undelete progams, hard disk tools etc.

i think this would be a huge asset for any geek!

---

### Post by alan_cb on 2010-09-25
I successfully integrated Ubuntu 10.04.1 to Hiren's BootCD 10.6 Grub Bootloader menu on my USB flash drive!

I could boot Ubuntu 10.04.1 from Hiren's BootCD via USB flash drive.

Eventually, I will post a tutorial of how to integrate Ubuntu to Hiren's BootCD via USB Flash Drive. It took hours of research until I found out that creating a partition on the USB flash drive helped make this happen, thanks to Grub4Dos. :grin:

---

### Post by hakkafusion on 2010-09-29
I used multiboot iso to integrate ubuntu+windows and then manually added hirens to menu.lst

however I am unable to partition the usb with multiboot iso, usb refuses to boot after it is partition. if you have a solution to that it'd be great help =)

---

### Post by prenuntius on 2010-10-30
Managed to combine Ubuntu and Hirens so that you can boot to Hirens and select Ubuntu from the menu.

You will need:
&#8226; 2GB or greater USB Drive
&#8226; Windows
&#8226; Ubuntu
&#8226; Hirens ISO
&#8226; Ubuntu 10.0.4

1. Partition a USB Flash stick to leave 750MB at the end (you can get away with 710) 
*I used Fat32 for both partitions*
2. Make a Ubuntu Boot CD using the second partition (the 750MB one)
3. Boot into Windows and follow the instructions on this page to generate a Hirens USB drive. [http://www.hiren.info/pages/bootcd-on-usb-disk]("http://www.hiren.info/pages/bootcd-on-usb-disk")
4. Open the HBCD folder and add this text to the menu. (I placed it under the Mini Windows XP entry) ```
title Ubuntu\nYay Ubuntu thanks to Prenuntius
find --set-root /syslinux/isolinux.bin
kernel /casper/vmlinuz noprompt cdrom-detect/try-usb=true file=/cdrom/preseed/ubuntu.seed boot=casper 
initrd /casper/initrd.lz
```
5. Reboot to the usb pen and choose Ubuntu from the Hirens menu to check that everything has worked.
6. Post results, tweaks and what-have-you back here so everyone can enjoy your labours.

Hope this works for you guys too. I've been playing with mine today and found it invaluable. The other advantage is that the first partition is visible in Windows so you can use you Hirens tools and anything else you want to drag onto that partition. 

Enjoy

Addendum: If you have a problem loading up the DOS programs menu then try copying the menu.lst from within your HBCD folder to the root of your drive. This fixed a problem I was having on a machine i was fixing.

I've also posted this on my website:
[http://www.fixitrepairs.co.uk/2010/10/31/combining-ubuntu-and-hirens-on-one-usb-drive/](http://www.fixitrepairs.co.uk/2010/10/31/combining-ubuntu-and-hirens-on-one-usb-drive/)

---

### Post by EvilDead on 2010-11-02
> **prenuntius said:**
> Managed to combine Ubuntu and Hirens so that you can boot to Hirens and select Ubuntu from the menu.

You will need:
• 2GB or greater USB Drive
• Windows
• Ubuntu
• Hirens ISO
• Ubuntu 10.0.4

1. Partition a USB Flash stick to leave 750MB at the end (you can get away with 710) 
*I used Fat32 for both partitions*
2. Make a Ubuntu Boot CD using the second partition (the 750MB one)
3. Boot into Windows and follow the instructions on this page to generate a Hirens USB drive. [http://www.hiren.info/pages/bootcd-on-usb-disk]("http://www.hiren.info/pages/bootcd-on-usb-disk")
4. Open the HBCD folder and add this text to the menu. (I placed it under the Mini Windows XP entry) ```
title Ubuntu\nYay Ubuntu thanks to Prenuntius
find --set-root /syslinux/isolinux.bin
kernel /casper/vmlinuz noprompt cdrom-detect/try-usb=true file=/cdrom/preseed/ubuntu.seed boot=casper 
initrd /casper/initrd.lz
```
5. Reboot to the usb pen and choose Ubuntu from the Hirens menu to check that everything has worked.
6. Post results, tweaks and what-have-you back here so everyone can enjoy your labours.

Hope this works for you guys too. I've been playing with mine today and found it invaluable. The other advantage is that the first partition is visible in Windows so you can use you Hirens tools and anything else you want to drag onto that partition. 

Enjoy

Addendum: If you have a problem loading up the DOS programs menu then try copying the menu.lst from within your HBCD folder to the root of your drive. This fixed a problem I was having on a machine i was fixing.

I've also posted this on my website:
[http://www.fixitrepairs.co.uk/2010/10/31/combining-ubuntu-and-hirens-on-one-usb-drive/](http://www.fixitrepairs.co.uk/2010/10/31/combining-ubuntu-and-hirens-on-one-usb-drive/)


Thanks for posting this.  I'm going to give it a try but have a question before I start. 

On step 2 you say  to "Make a Ubuntu Boot CD using the second partition".  Am I supposed to boot into the CD and use the USB boot install option?

Thanks

---

### Post by KhaaL on 2010-11-05
just wanted to share, the guide here ( [http://0-fx.com/index.php?/General/how-to-make-a-bootable-usb-flash-drive-with-ubuntu-and-hirens-bootcd.html](http://0-fx.com/index.php?/General/how-to-make-a-bootable-usb-flash-drive-with-ubuntu-and-hirens-bootcd.html) ) worked well for me and the instructions were easy to follow.

---

