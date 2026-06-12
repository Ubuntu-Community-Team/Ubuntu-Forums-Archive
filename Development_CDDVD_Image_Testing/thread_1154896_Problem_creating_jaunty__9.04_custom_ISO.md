---
title: "Problem creating jaunty / 9.04 custom ISO"
date: 2009-05-10
forum: Development CD/DVD Image Testing
---

### Post by djbloc on 2009-05-10
In my first steps to customise the live CD, I've run the commands below to extract and repack the ISO to check I'm building correctly.

Unfortunately when I test it in Virtualbox OSE (2.04 Intrepid) it only part loads before dropping to busybox. If I use the original live cd it loads correctly in Virtualbox.

```
# http://paste.ubuntu.com/164208/

sudo mkdir -p /mnt/iso
sudo mount ubuntu-9.04-desktop-i386.iso /mnt/iso -o loop,ro
sudo mkdir -p /mnt/jauntyscratch/isocp
sudo cp -a /mnt/iso/* /mnt/jauntyscratch/isocp/
cd /mnt/jauntyscratch/isocp
sudo mkisofs -D -r -V "CustomLiveCD" -cache-inodes -J -l -b isolinux/isolinux.bin -c isolinux/boot.cat -no-emul-boot -boot-load-size 4 -boot-info-table -o ../ubuntu-custom.iso .
```

What am I doing wrong?

---

