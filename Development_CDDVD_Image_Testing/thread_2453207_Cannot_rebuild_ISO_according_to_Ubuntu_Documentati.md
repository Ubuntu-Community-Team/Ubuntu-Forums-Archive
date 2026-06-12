---
title: "Cannot rebuild ISO according to Ubuntu Documentation (11/2020)"
date: 2020-11-05
forum: Development CD/DVD Image Testing
---

### Post by arnolp666 on 2020-11-05
Earlier this year (around April) I could:
 
[LIST=1]
[*]Download a Ubuntu iso (in my case Ubuntu 18.04)
[*]Extract its contents to a folder
[*]Make changes (if needed, specifically preseed some basic commands, no deep changes)
[*]Run the mkisofs commands with the required options to create an iso
[*]Run isohybrid on the iso (this was apparently a crucial step)
[*]Make a bootable USB with startup disk creator and the created iso
[/LIST]
 The mkisofs command and options are the same as those found here: [https://help.ubuntu.com/community/InstallCDCustomization](https://help.ubuntu.com/community/InstallCDCustomization)
 Namely: mkisofs -r -V UBUNTU_V -cache-inodes -J -l -b isolinux/isolinux.bin -c  isolinux/boot.cat -no-emul-boot -boot-load-size 4 -boot-info-table -o  myiso.iso UBUNTU_V
 sudo isohybrid myiso.iso
 (I store the files in a folder called UBUNTU_V where V stands for "Vanilla")
 This used to work just fine. Now it does not work anymore, even when  all I am trying to do is rebuild an iso from unmodified files (step 3.  skipped, hence "Vanilla")
 Now the startup disk creator won't acknowledge the existence of my  iso when selecting it in the browser menu, and trying to dd the iso onto  the USB stick (after dd if=/dev/zero to really cleanse it) results in  the USB boot working (Ubuntu logo greeting) but then an ash terminal  saying no live system could be found.
 Did something change since April ? Why isn't it working as it used to ?
 Thank you very much.

---

### Post by arnolp666 on 2020-11-05
The issue was how I extracted the files from the original iso. I used to just open the USB and copy paste with my mouse and keyboard. Or, I would run
 mount -o loop original.iso temporary/ sudo cp -r temporary/* UBUNTU_V/
 But that somehow corrupts things.
 I found: [https://gist.github.com/AkdM/2cd3766236582ed0263920d42c359e0f](https://gist.github.com/AkdM/2cd3766236582ed0263920d42c359e0f)
 And these commands: mount -t iso9660 -o loop ~/original.iso /mnt/ cd /mnt tar cf - . | (cd /tmp/custom_iso; tar xfp -)
 allow to extract the files cleanly and rebuild the iso with the commands from Ubuntu documentation.
 It didn't use to be so complex though.
 Thank you.

---

