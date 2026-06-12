---
title: "No sound again on Inspiron 1525n and latest 8.04 kernel"
date: 2009-11-20
forum: Dell Ubuntu Support (CLOSED)
---

### Post by bentledr on 2009-11-20
After updating to the latest kernel on my inspiron 1525n the sound has gone again.

It seems that hsfmodem-base doesn't build for kernel 2.6.24-25

I have resorted to the fix originally given by dell support and sound now works again.

I will post it later today when I can retreive the details.

I see from disecting the package that modules are provided for upto kernel 2.6.24-24 only.

Will the hsfmodem packages from the Dell Team PPA be updated at some point giving support for 8.04 kernel 2.6.24-25

The original fix as promised

cd /lib/modules
cd 2.6.24-25-generic/ubuntu/sound/alsa-driver/pci/hda
sudo mv snd-hda-intel.ko.REPLACEDBYhsfmodem snd-hda-intel.ko
cd /lib/modules/2.6.24-25-generic/updates
sudo rm snd-hda-intel.ko
sudo rm snd-hda-codec.ko
sudo depmod -a
sudo update-initramfs -u
sudo reboot

Fot the final solution see post #4 in this thread.

---

### Post by Denny Johnson on 2009-11-20
> **bentledr said:**
> 

I wiil post it later today when I can retreive the details.



Please do.
Thanks

---

### Post by bentledr on 2009-11-23
Original post edited to include the fix.

---

### Post by bentledr on 2009-11-24
Problem of "hsfmodem-base-dkms" not building solved.

I think it was because the package "patch" was not installed.

I installed "patch" as a consequence of installing the "build-essential" package.

"build-essential" pulls other things in also so it could have been one of those but with "build-essential" installed "hsfmodem-base-dkms" now builds and the sound works just as intended.

So the old method described in my original post should no-longer be used or used only as a last resort if the "hsfmodem-base-dkms" fails to build in the future after a kernel upgrade (you would have to substitute the appropriate kernel)

---

