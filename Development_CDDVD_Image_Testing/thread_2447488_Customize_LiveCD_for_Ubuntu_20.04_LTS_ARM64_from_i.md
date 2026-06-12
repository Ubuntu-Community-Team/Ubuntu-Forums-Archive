---
title: "Customize LiveCD for Ubuntu 20.04 LTS ARM64 from installed OS"
date: 2020-07-20
forum: Development CD/DVD Image Testing
---

### Post by haseebzahid on 2020-07-20
I downloaded Ubuntu 20.04 LTS for ARM64 and it worked fine on my ARM64  desktop machine. I want to customize the installed Ubuntu and repack  into LiveCD for ARM64 based desktop system however the steps i found  online are mostly for AMD/Intel but they does not work exactly when i  follow on ARM64 machines. Can i get guideline for ISO creation for  latest Ubuntu20.04. or any direction.

Regards
Haseeb Zahid

---

### Post by haseebzahid on 2020-08-18
update I managed to boot the ISO. the issue was i was had dual boot setup ubunt20.04 and Ubuntu18.04. due to this the initrd I created during chroot doesnot work properly and gives error at boot time about root parameters not set.
Now i can boot to liveCD and start installation but durrig installation i get filesystem.squashfs checksum error + manifest checksum error or both this is total random everytime. I used below steps to create squashfs and checksum. can anyone help me out of this error.

###create squashfilesystem
sudo mksquashfs ${WORK}/rootfs ${CD}/${CAPSER}/filesystem.${FORMAT} -noappend

###Calculate squashfilesystem size
echo -n $(sudo du -s --block-size=1 ${WORK}/rootfs | tail -1 | awk '{print $1}') | sudo tee ${CD}/${CAPSER}/filesystem.size

###Calculate MD5
sudo find ${CD} -type f -print0 |sudo xargs -0 md5sum |sudo sed "s@${CD}@.@" |sudo grep -v md5sum.txt | sudo tee -a ${CD}/md5sum.txt

---

